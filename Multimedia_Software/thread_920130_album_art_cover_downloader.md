---
title: "album art cover downloader"
date: 2008-09-14
forum: Multimedia Software
---

### Post by demonskier on 2008-09-14
I'm trying to use album art cover downloader but it keeps giving me an error... this is the traceback can anybody help me please

Traceback (most recent call last):

  File "/usr/lib/albumart/process.py", line 130, in run
    for cover in albumart.getAvailableCovers(artist, album, requireExactMatch = self.requireExactMatch):

  File "/usr/lib/albumart/albumart.py", line 115, in getAvailableCovers
    results += s.findAlbum("%s %s" % (artist, album))

  File "/usr/lib/albumart/albumart_source_amazon.py", line 48, in findAlbum
    return amazon.searchByKeyword(name,type="lite",product_line="music")

  File "/usr/lib/albumart/amazon.py", line 315, in searchByKeyword
    return search("KeywordSearch", keyword, product_line, type, page, license_key, http_proxy, locale, associate)

  File "/usr/lib/albumart/amazon.py", line 293, in search
    xmldoc = minidom.parse(usock)

  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)

  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 928, in parse
    result = builder.parseFile(file)

  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 207, in parseFile
    parser.Parse(buffer, 0)

ExpatError: junk after document element: line 1, column 26

---

### Post by demonskier on 2008-09-15
Bump

---

### Post by Duranxl on 2008-10-13
I have the same problem

---

### Post by DJ_Peng on 2009-07-23
I found a solution for this problem, as well as a place to get the program. To get info on the ACAD you can visit [this page on the Internet Archive's Wayback Machine]("http://web.archive.org/web/20070324042046/http://kempele.fi/%7Eskyostil/projects/albumart/"), and you can download the latest version Debian installer ([albumart_1.6.0-1_all.deb]("http://web.archive.org/web/20070323002339/http://kempele.fi/%7Eskyostil/projects/albumart/dist/albumart_1.6.0-1_all.deb")) as well as other versions, including source code, on [this page]("http://web.archive.org/web/20070323002339/kempele.fi/%7Eskyostil/projects/albumart/albumart-1_6_0.blog/"). Once you get it installed you can launch albumart-qt, but you may get errors like the ones I got.
> $ albumart-qt
Traceback (most recent call last):
  File "/usr/bin/albumart-qt", line 145, in <module>
    sys.exit(runGui())
  File "/usr/bin/albumart-qt", line 77, in runGui
    import albumart_dialog
  File "/usr/lib/albumart/albumart_dialog.py", line 32, in <module>
    from pixmap import getPixmapForPath
  File "/usr/lib/albumart/pixmap.py", line 4, in <module>
    import albumart_images
  File "/usr/lib/albumart/albumart_images.py", line 6
SyntaxError: Non-ASCII character '\xa0' in file /usr/lib/albumart/albumart_images.py on line 6, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details
Thanks to a [post by mglukhovsky on another thread]("http://ubuntuforums.org/showpost.php?p=2809331&postcount=15") I'm able to get it working. I'll go ahead an summarize the steps I followed to get things working.

Open a terminal, and open the offending file in gedit as root:
     Code:
     sudo gedit /usr/lib/albumart/albumart_images.py 
2) Insert the following as the first line of the file:
     Code:
     #coding:utf-8 
3) Save the file, then exit gedit. Then simply launch ACAD again by running albumart-qt either in a terminal or from Alt-F2.

***THIS JUST IN:*** It turns out Sami Kyöstilä has moved his site to a [new URI]("http://www.unrealvoodoo.org/hiteck/"), and there's an [update to ACAD]("http://www.unrealvoodoo.org/hiteck/projects/albumart/")! I purged my old install and installed the new version (1.6.6) and it launched with absolutely no issues whatsoever.

Now if you'll excuse me, I need to mount my E100 media player and see how succcessful it is on my end. :guitar:

---

