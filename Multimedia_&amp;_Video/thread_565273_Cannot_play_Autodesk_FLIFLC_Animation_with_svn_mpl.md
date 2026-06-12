---
title: "Cannot play Autodesk FLI/FLC Animation with svn mplayer"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by andrew.46 on 2007-10-02
Hi,

 I have put a huge effort into compiling the svn mplayer with the 'all' codecs pack but I have failed miserably to get mplayer to play fli / flc animations.

 Some examples of these animations can be seen at:

[http://woodshole.er.usgs.gov/operations/modeling/circulation.html](http://woodshole.er.usgs.gov/operations/modeling/circulation.html)

 I have compiled mplayer as per:

[http://ubuntuforums.org/showthread.php?t=558538&highlight=howto+svn+mplayer](http://ubuntuforums.org/showthread.php?t=558538&highlight=howto+svn+mplayer)

 with the addition of the following 3 files:

```
lib3ds-1.2 lib3ds-bin lib3ds-dev 
```

 It is a small issue but I am keen to solve it. The mplayer users list drew a blank, as in nobody answered my query so I am hoping for more luck here :-)

                      Andrew

---

### Post by andrew.46 on 2007-10-02
Hi,

 Although this may have been solved in the very latest svn the syntax to play the fli files works as:

```
$ mplayer -demuxer lavf filename.flc
```


Although I note that as of MPlayer dev-SVN-r24688-4.1.3 this appears to have been fixed and now plays without this syntax.


           Andrew

---

