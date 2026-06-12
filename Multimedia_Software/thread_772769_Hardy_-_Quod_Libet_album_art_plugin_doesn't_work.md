---
title: "Hardy - Quod Libet album art plugin doesn't work"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Gerontius on 2008-04-28
I installed Quod Libet from the official repository and the album art plug-in does not work. The versin that was available in Gutsy worked well. Apparently, there seems to be some kind of amazon.py problem (none of the album art plugins from the official quodlibet website work - and they worked before). Since i don't know anything about python programming, i came here for help.

Here's output from terminal. I started quod libet, selected an album and then used "download album art" plugin

> Supported formats: mod, mp3, mp4, mpc, spc, trueaudio, wav, wavpack, wma, xiph
Loaded song library.
Opening audio device.
Exception in thread Thread-2:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 486, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.5/threading.py", line 446, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/share/quodlibet/plugins/songsmenu/albumart.py", line 169, in __search
    self.__search_string(query)
  File "/usr/share/quodlibet/plugins/songsmenu/albumart.py", line 151, in __search_string
    query, type="lite", product_line="music")
  File "/usr/share/quodlibet/plugins/songsmenu/_amazon.py", line 316, in searchByKeyword
    return search("KeywordSearch", keyword, product_line, type, page, license_key, http_proxy, locale, associate)
  File "/usr/share/quodlibet/plugins/songsmenu/_amazon.py", line 294, in search
    xmldoc = minidom.parse(usock)
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 928, in parse
    result = builder.parseFile(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 207, in parseFile
    parser.Parse(buffer, 0)
ExpatError: not well-formed (invalid token): line 4, column 11


Thanks for your help

---

### Post by hugmenot on 2008-04-29
Do you have some file like this?:
[QUOTE who="./plugins/songsmenu/_amazon.py"]```
You need a Amazon-provided license key to use these services.
Follow the link above to get one.  These functions will look in
several places (in this order) for the license key:
- the "license_key" argument of each function
- the module-level LICENSE_KEY variable (call setLicense once to set it)
- an environment variable called AMAZON_LICENSE_KEY
- a file called ".amazonkey" in the current directory
- a file called "amazonkey.txt" in the current directory
- a file called ".amazonkey" in your home directory
- a file called "amazonkey.txt" in your home directory
- a file called ".amazonkey" in the same directory as amazon.py
- a file called "amazonkey.txt" in the same directory as amazon.py
```[/QUOTE]

---

### Post by moopoo on 2008-07-12
Amazon changed the API, so all you have to do is to replace _amazon.py and albumart.py in /usr/share/quodlibet/plugins/songsmenu with the new ones i found at [Nabble]("http://www.nabble.com/Bug-482157%3A-quodlibet-plugins%3A-Download-Album-Art-plugin-fails-due-to-deprecated-Amazon-Web-Services-interface-p17355946.html").

---

### Post by flatko on 2009-09-25
Hi. I obtained a license key from Amazon.
Now it shows alert "Search error  u'ingParameter'" when i start the Cover plugin. Somebody hepl?

---

### Post by tv0571 on 2010-12-07
I'm having similar problems.  I think the files referenced above are for an older version of the plugin - they have no comments, but the version I'm running has comments from May 2008.

Time for an update.  Anyone?

---

### Post by lazka on 2010-12-10
[https://launchpad.net/~lazka/+archive/ppa](https://launchpad.net/~lazka/+archive/ppa)

regarding amazon: the plugin now signs its requests with an external server.. so, no license key needed.

---

