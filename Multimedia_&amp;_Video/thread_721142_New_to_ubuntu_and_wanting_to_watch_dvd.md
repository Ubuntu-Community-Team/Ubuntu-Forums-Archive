---
title: "New to ubuntu and wanting to watch dvd"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by colddepression on 2008-03-11
I am new to ubuntu and I want to know how to watch,burn,and copy dvds on it. I mean I put the condemned in and tried towatch it and totem kicked on but nothing. Can anyone help me.

---

### Post by zxscooby on 2008-03-11
try looking here
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29)

---

### Post by colddepression on 2008-03-11
well i looksd ont here but what code do you have to use to get the plugins cause right now it will start up my disc and then stop liek 5 seconds into it and say it dont have the plugin

---

### Post by 6205 on 2008-03-11
copy/paste into terminal >>>

[COLOR="Red"]sudo apt-get install totem-xine libdvdread3 libdvdcss2[/COLOR]

but you must be sure that you have enabled repositories universe, multiverse and medibuntu
[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by colddepression on 2008-03-11
Well I got it working now I just need a dvd copying program cause my girlfriends father is wanting me to copy a dvd of his fathers funreal to send to his son who couldn't make kit.

---

### Post by ubuntu-freak on 2008-03-11
Part 3 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) deals with DVD playback, ripping and burning, Part 1 is worth doing though. Also, you don't need Xine to watch DVDs, you have just changed the backend of Totem from Gstreamer to Xine. VLC is awesome for playing DVDs, great menu support.
 
Nathan

---

### Post by colddepression on 2008-03-12
thanks man I am trying them now on my condemned dvd I am thinking about copying it for my girlfriend.

---

