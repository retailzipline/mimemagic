This is a GPL-2.0 version of mimemagic pinned to 0.3.6.

0.3.6 was yanked to switch back to MIT license and now requires installing the mime database
provided by freedesktop.org separately (see: https://github.com/mimemagicrb/mimemagic#dependencies).

See: https://github.com/mimemagicrb/mimemagic/issues/98 and https://github.com/rails/rails/issues/41750 for background.

---

MimeMagic is a library to detect the mime type of a file by extension or by content. It uses the mime database
provided by freedesktop.org (see http://freedesktop.org/wiki/Software/shared-mime-info/).

[![Gem Version](https://img.shields.io/gem/v/mimemagic.svg)](http://rubygems.org/gems/mimemagic)

Usage
=====

```ruby
require 'mimemagic'
MimeMagic.by_extension('html').text?
MimeMagic.by_extension('.html').child_of? 'text/plain'
MimeMagic.by_path('filename.txt')
MimeMagic.by_magic(File.open('test.html'))
# etc...
```

Extra magic overlay
=====

Microsoft Office 2007+ formats (xlsx, docx, and pptx) are not supported by the mime database at freedesktop.org. These files are all zipped collections of xml files and will be detected as "application/zip". Mimemagic comes with extra magic you can overlay on top of the defaults to correctly detect these file types. Enable it like this:

```ruby
require 'mimemagic'
require 'mimemagic/overlay'
MimeMagic.by_magic(File.open('test.xlsx'))
```

You can add your own magic with `MimeMagic.add`. See `lib/mimemagic/overlay.rb`.

API
===

http://www.rubydoc.info/github/minad/mimemagic

Tests
=====

```
bundle install

rake test
```

Authors
=======

Daniel Mendler

LICENSE
=======

GPL-2.0
