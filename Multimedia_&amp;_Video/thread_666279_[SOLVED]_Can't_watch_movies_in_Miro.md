---
title: "[SOLVED] Can't watch movies in Miro"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by jazzgossen on 2008-01-13
I just installed Miro, which looks really neat. I can search and download movies, but not watch them in Miro. I can watch the downloaded files with Totem, though. When I click "play" in Miro, I just briefly get a grey screen, and then I get back to the previous screen. The terminal output is 
```
INFO     got action:playViewNamed?viewName=matchingItems&firstItemId=394
INFO     Playing item with renderer: <frontend_implementation.xinerenderer.Renderer instance at 0x990a58c>
INFO     got file:///tmp/tmpPLjiNa.html
INFO     got file:///tmp/tmpaPefW9.html

```

Any ideas why?

I also get a large number of error messages regarding resizing of the image cache, saying things like:
```
convert: unable to open module file `/usr/lib/ImageMagick-6.2.4/modules-Q16/coders/91384859.la': No such file or directory.
```
but that's a lesser problem.

---

### Post by chewearn on 2008-01-13
Have you installed Miro via the ubuntu repositories?  If yes, there is a newer version at the miro website (with ubuntu *.deb file).

Other than that, I don't have better suggestion.:(

---

### Post by magiver on 2008-01-17
try this [http://ubuntuforums.org/showthread.php?p=4157667]("http://ubuntuforums.org/showthread.php?p=4157667"). it worked for me

---

### Post by jazzgossen on 2008-01-20
> **magiver said:**
> try this [http://ubuntuforums.org/showthread.php?p=4157667]("http://ubuntuforums.org/showthread.php?p=4157667"). it worked for me

Thanks! That solved it.

---

