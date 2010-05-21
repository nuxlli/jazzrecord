##Hiya! (Intro)

JazzRecord is a simplified ActiveRecord clone for providing a JavaScript ORM layer. It currently supports [Gears](http://gears.google.com), [Adobe AIR](http://www.adobe.com/products/air/), and [Titanium PR1](http://titaniumapp.com/). Like ActiveRecord, Jazz is free and open-source software, licensed under [MIT License](http://www.opensource.org/licenses/mit-license.php). And in being inspired by ActiveRecord, Jazz seeks to minimize its learning curve by mimicking ActiveRecord style and conventions.

JazzRecord is almost feature-complete, and most of it has been tested thoroughly across all major browsers using a test suite called [JSSpec](http://jania.pe.kr/aw/moin.cgi/JSSpec). AIR-side testing will be implemented shortly.

##Whats is new in this fork?

Record now have newModel and createModel methods to hasOne and hasMany associations.

    var Author = new JazzRecord.Model({
      table: "authors",
      hasMany : { books : 'books' },
      foreignKey: "author_id",
      columns: {
        id   : 'int',
        name : 'text'
      }
    });
    var Book = new JazzRecord.Model({
      table: "books",
      foreignKey: "book_id",
      columns: {
        id        : 'int',
        author_id : 'int',
        name      : 'text'
      }
    });
    author = Author.create({ name : 'Renan' });
    author.createBook({ name : 'Hello world!' }); //this is the same of Book.create({ name: 'Hello world!', :author_id : 1 });
    Book.first().name; //'Hello world!'
    author.newBook({ name : 'Not saved yet' });
    Book.count(); //1

##Current Development

Currently underway is work to complete the feature set of JazzRecord, which consists of... asynchronous support (primarily for HTML5) rich dirty records support, implementing a few add'l finder options, and adding support for encrypted local databases for AIR 1.5+. Palm Pre and Titanium PR2 are two new target platforms we aim to support in the near future.

JazzRecord is now MooTools free, and works with any other JavaScript library. We're _very_ excited about the possibilities this might open up.

##More Info

For more information, a demo and the most recent documentation, visit [JazzRecord.org](http://www.jazzrecord.org)

For regular updates on JazzRecord development, follow us on Twitter: [@jazzrecord](http://www.twitter.com/jazzrecord)

To contact Nick Carter regarding bugs or for questions, email me at <thynctank@thynctank.com>
