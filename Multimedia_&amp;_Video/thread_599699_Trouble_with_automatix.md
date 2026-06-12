---
title: "Trouble with automatix"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by geovino on 2007-11-01
Just did a clean install of gutsy. Looking for a simple thread to install the dvd and other codecs for sound and video. Tried to us automatix but it won't work. 

Please show me where to install the multimedia files? Thank you.

---

### Post by scrooge_74 on 2007-11-01
Automatix is not backed by Ubuntu so if something breaks, you get to keep all the pieces.

For configuring your multimedia check this [link]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by markharding557 on 2007-11-01
did you use the new gutsy version of automatix

---

### Post by VCSkier on 2007-11-01
yup yup.  scrooge_74 is right.  IMHO, at this point, Automatix is just source of breakage for most people.  there are now officially supported methods for doing most everything it does, plus they're easily and much, much cleaner than Automatix.  If you want flash and all the codecs and everything in one go, slap a "sudo aptitude install ubuntu-restricted-extras" in your terminal, and enjoy the ear to ear joy that follows.  :)

---

### Post by geovino on 2007-11-02
Thanks for the info.  I uninstalled Automatix and also remmed out its entry in the sources.list

I was able to find this page: 
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

I was able to install the codecs needed. Music and Video play now except for Amarok. I still get this message:

Error Loading Media
There is no available decoder.
[http://scfire-chi-aa03.stream.aol.com:80/stream/1018](http://scfire-chi-aa03.stream.aol.com:80/stream/1018)

How would I get it to play?

---

### Post by scrooge_74 on 2007-11-02
What format are you trying to play which gives the error?

---

### Post by geovino on 2007-11-02
I was trying to play Groove Salad and other radio streaming stations.

---

### Post by orange2k on 2007-11-02
Amarok in Gutsy asked me if I wanted to install required codecs automatically...

---

### Post by VCSkier on 2007-11-02
maybe sudo aptitide install kubuntu-restricted-extras?

---

### Post by geovino on 2007-11-02
> **orange2k said:**
> Amarok in Gutsy asked me if I wanted to install required codecs automatically...

Maybe I should uninstall and reinstall Amarok. I'm using Exaile now and it plays streaming radio just fine. Why would Amarok need some other file?

---

### Post by bodhi.zazen on 2007-12-19
Automatix is a third party project and, at this time, is not supported on the ubuntu forums. For additional information see the following links :

	[Technical review of Ax](http://mjg59.livejournal.com/77440.html)

	To my knowledge the maintainers of Ax are working to address these issues, but they remain unresolved at this time. You might check the Ax forums for an update. When and if this occurs the situation will be re-evaluated and subject to change.

	[Official Forums Policy](http://ubuntuforums.org/announcement.php?f=13/)

	[Supported Installation Alternatives to Automatix](http://ubuntuforums.org/showthread.php?t=519872)

	[Automatix forums](http://www.getautomatix.com/forum/index.php?act=idx)

	If you want to discuss Ax, feel free to post here : 

	[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

