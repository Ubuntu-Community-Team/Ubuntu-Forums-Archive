---
title: "Problem with RubyRippper install. Can't find libglade2-ruby 0.14.*, gtk bindings?"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by AaronS2 on 2006-12-30
I'm trying to install RubyRipper on the edgy version of ubunto. I was able to get it to sorta work. However, I ran into a sort of snag. I'm getting the error described in RubyRippers Readme FAQ.

Q : My buttons don't react and give the following error in a terminal:
warning: GRClosure invoking callback: already destroyed Callback error
A : Downgrade the ruby gtk bindings to a 0.14.* version. The bug is known by
the ruby gtk bindings team and will be fixed in the >0.15.0 versions of the
bindings.

Despite these errors on some unworking button pushes I was able to get it to rip music. However, it hiccups a lot, and sometimes somethings don't work.
 
I'm currently working on trying to document the RubbyRipper install process on Ubuntu's wiki which can be found here: [CDRipping -- RubyRipper Section ]("https://help.ubuntu.com/community/CDRipping#head-82c29ac724da877efef66ffcbfa07192ef12dbc4")

Incase it gets edited the steps I took were (sorry about the mess but it's a rough copy):
To install:
    *     First follow the steps for RestrictedFormats. Not much point in ripping mp3s if your installation can't even play them.
    *      Install dependant packages.
          o   "cd-discid"
          o "cdparanoia"
          o  "libglade2-ruby"? and all it's dependancies. [WWW] RubyRipper's instructions ask for "ruby-libglade2" same thing?
          o "ruby1.8-dev" package (or whatever version of ruby you are using)? May not be necessary but it may have worked better when I tried it? Needs further testing.
          o  "build-essential" package? May not be necessary but it may have worked better when I tried it? Needs further testing.
    * Install optional packages. (Depending on the codec you wish to use.)
    *              Lame
    *      Then download Rubyripper
     *      type: make install

Since I was getting the  ruby gtk bindings version error I tried searching for them but couldn't find them. I'm guessing they are in the "libglade2-ruby" package mostly by the description and the 0.15.* version number on them.  However, I couldn't find any 0.14.* version anywhere. I even searched all of Debians packages but it skips from 0.12 to 0.15.

After that I saw on a forum post that ubunto's ruby version is tweeked and can cause problems. so I tried uninstalling all of ubunto's ruby packages and downloaded ruby to install it by hand. Searches on the ruby site still couldn't locate the  ruby gtk bindings and now making rubyripper errors wanting the ruby-libglade2 package. Of course I could back peddle all that but that still doesn't get me the correct 0.14 version.

Any ideas?

---

### Post by budgie9 on 2006-12-30
Seems the file you require was in Dapper. It is listed here. It should work for you.
[http://packages.ubuntulinux.org/dapper/interpreters/](http://packages.ubuntulinux.org/dapper/interpreters/)

---

