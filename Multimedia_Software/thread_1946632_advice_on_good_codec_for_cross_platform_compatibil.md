---
title: "advice on good codec for cross platform compatibility"
date: 2012-03-25
forum: Multimedia Software
---

### Post by chickenPie4breakfast on 2012-03-25
I used to use windows and after editing in Sony Vegas I found I got the best quality but small file size saving in .wmv format unfortunately although I can play them back in linux I cant edit them in some apps although Openshot works with wmv. So for the future I would like to know what format to save a file in - just in case I might need to re-edit later - just a  simple edit like cutting more out.
.mov ?  .avi but with which codec? h264? .dv?

---

### Post by SeijiSensei on 2012-03-25
The most widely supported open codec is XviD which is typically stored in an AVI container.  It has a bit less video quality than H.264, but it can be played on a very wide range of hardware and software.  The standard companion audio codec is MP3.  For a quick overview of using mencoder to create such files, see this [howto]("http://en.gentoo-wiki.com/wiki/Mencoder#XviD").  Two-pass encoding provides the best quality, but try a one-pass encode first and see if it meets your standards.

---

### Post by cotcot on 2012-03-25
There are many possibilities. Turn your question around : which codecs are to be avoided ? Avoid .wmv and any other proprietary codecs. [[COLOR="Blue"]Here[/COLOR]]("http://en.wikipedia.org/wiki/List_of_open_source_codecs") is some info over open source codecs. 
I can join the previous poster with his suggestion for Xvid. I used h264 but changed about a year ago to xvid. I have no problems with it.

---

### Post by chickenPie4breakfast on 2012-03-25
Thanks for the reply it will be xvid for now then. It is a bit of a gamble tying to guess what codecs editing and playing apps will support say 5 years from  now. I really need two good guesses. One for higher quality/higher file size to save master copies of important vids and another for vids that have been edited and are not so important - I will try using xvid for those and maybe .DV for the master copies?

---

