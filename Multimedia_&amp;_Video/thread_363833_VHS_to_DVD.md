---
title: "VHS to DVD"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by Jeff59 on 2007-02-17
Hello I'm new to video editing and would appreciate some advice. I'm trying to convert some old VHS legally purchased movies to DVD. So far I've ripped one to raw video using Kino and converted it to mpeg2. I then used DVD Styler to convert it to an ISO. This is were my problem is. The resulting file is to large to fit on a standard DVD. I tried to use K9copy to shrink it but it just stalls. The same with DVD shrink. Has anyone had any luck converting VHS full length commercial movies?

---

### Post by david_2001 on 2007-02-17
When converting from the raw recording to mpeg2, you'll need to encode at video and audio bitrates that will give the desired final file size.  Here are two on-line calculators that I've used from time to time and which may help:
[http://dvd-hq.info/Calculator.html](http://dvd-hq.info/Calculator.html)
[http://www.videohelp.com/calc.htm](http://www.videohelp.com/calc.htm) (requires Java)

---

### Post by Jeff59 on 2007-02-18
David 2001,  Thanks for the information.  Since I'm a newbie to this is there a GUI for encoding Mpeg2 or a site that would explain the command line options and set up?

---

### Post by david_2001 on 2007-02-18
You could try starting with avidemux (it's in the Ubuntu repositories) to do the encoding.  It can work out the encoding parameters necessary to fit a video file to a DVD automatically but be aware that it's not the greatest mpeg2 editor - transitions are not handled particularly well and the result is blocky artifacts immediately after the cut-point when played back.

None of the software that I use for mpeg2 encoding/DVD creation is in the repositories: [COLOR="SandyBrown"][Tovid]("http://tovid.wikia.com/wiki/Main_Page")[/COLOR] is easy to set-up - the wiki has Ubuntu-specific instructions - and gives good results.  [COLOR="SandyBrown"][KmPg2]("http://kmpg2.sourceforge.net/view.php/page/Voorpagina")[/COLOR] is a useful encoder and I normally use it in combination with [COLOR="SandyBrown"][KDE DVD Authoring Wizard](http://dvdauthorwizard.sourceforge.net/view.php/page/Voorpagina)[/COLOR] from the same author.  Neither are quite as easy to set-up as tovid, however.  For simple editing of mpeg2 files, e.g. removing adverts from TV recordings, I use [COLOR="SandyBrown"][DVBCUT]("http://dvbcut.sourceforge.net/index.html")[/COLOR], which has to be compiled from source.

---

