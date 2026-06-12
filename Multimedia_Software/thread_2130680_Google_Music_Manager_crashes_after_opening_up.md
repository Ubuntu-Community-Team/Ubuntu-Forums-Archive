---
title: "Google Music Manager crashes after opening up"
date: 2013-03-30
forum: Multimedia Software
---

### Post by enroxorz on 2013-03-30
The oddest thing is happening with my Google Music Manager. After the latest update from Google, the application opens up of a second, and even if I quickly get to the options the Google Music Manager app closes. No crash reports. No nothing. Just closes. I re-installed 12.10 to see if that was the issue and sadly it didn't help. What should I do? Is there an app log that might help me with this?

---

### Post by Gamer_Z. on 2013-04-03
I do not have a solution (though I can confirm that problem has existed for me since 11.04 and Google's updates have not fixed it).  I did notice Music Manager sometimes crashes if I try to upload a lot of music at once, but if I add a folder to upload and move the files into that folder one at a time, Music Manager does not crash.

For logs, try looking in ~/.config/google-musicmanager.

---

### Post by savi3000 on 2013-04-06
Having the same issue. Anyone know a fix?

---

### Post by georanger on 2013-04-06
I worked around this crash by removing the latest version, which left all my music data intact and then installing version 1.0.55.7425 which is working fine.

---

### Post by enroxorz on 2013-04-08
This worked like a charm.

Just in case anyone needs the file without googling for it:

[http://ubuntuone.com/63gYDtAAJow4nWizbZqM6U](http://ubuntuone.com/63gYDtAAJow4nWizbZqM6U)

---

### Post by Excalibre on 2013-04-11
Oh, awesome! Thank you for that link, enroxorz, I've been going nuts trying to get my music uploaded and it's finally working right. It seems the current release if you download it from Google is just complete crap.

---

### Post by PantherFarber on 2013-04-15
> **enroxorz said:**
> This worked like a charm.

Just in case anyone needs the file without googling for it:

[http://ubuntuone.com/63gYDtAAJow4nWizbZqM6U](http://ubuntuone.com/63gYDtAAJow4nWizbZqM6U)


i would like to try this but i cant find the 32 bit version and this is the 64. have been searching for over an hour for the 32 bit version.

---

### Post by georanger on 2013-04-15
You can get it from [http://dl.google.com/linux/musicmanager/deb/pool/main/g/google-musicmanager-beta/google-musicmanager-beta_1.0.55.7425-r0_i386.deb](http://dl.google.com/linux/musicmanager/deb/pool/main/g/google-musicmanager-beta/google-musicmanager-beta_1.0.55.7425-r0_i386.deb)

---

### Post by DeLiK on 2013-04-16
Thanks! Problem solved for now.. :)

---

### Post by fragargon on 2013-04-19
> **enroxorz said:**
> This worked like a charm.

Just in case anyone needs the file without googling for it:

[http://ubuntuone.com/63gYDtAAJow4nWizbZqM6U](http://ubuntuone.com/63gYDtAAJow4nWizbZqM6U)

thanks mate,

this solved my problem... i had got the current deb amd64 and same issue as described.
the file provided by the link solved the issue, uploading ATM

:D

---

### Post by danevans10 on 2013-04-23
awesome, cheers

---

### Post by mrjm on 2013-04-28
how i solved this problem:

1. removing installed (latest) version of google-musicmanager 
```
sudo apt-get remove google-musicmanager
```

2. deleting directory ~/.config/google-musicmanager
```
sudo rm -R ~/.config/google-musicmanager
```

3. download .deb file from google

4. install the .deb

```
sudo dpkg -i google-musicmanager-beta_current_amd64.deb
```

worked perfect.

---

### Post by alex-s77 on 2013-05-11
Hm,
no luck for me…

When I first installed the current version or also 1.0.55.7425-r0 from a comment in this post, I got the dialog window of the application to show up. I entered username, password and said that I wanted to DOWNLOAD my PURCHASED stuff. It did so.

But now I'd like to upload music. How? When I click on the icon in the notification area (or what's it called…?), I get a context menu. But I cannot get the app to show up, and thus I cannot select what I want to do.

Oh, yeah, at first I also got this "error":

```
a@ask-home:~$ google-musicmanager 
log4cxx: No appender could be found for logger (root).
log4cxx: Please initialize the log4cxx system properly.
```

To overcome this "error", I created a [FONT=courier new]log4cxx.xml[/FONT] file in my [FONT=courier new]$HOME[/FONT] directory; see [ATTACH]242480[/ATTACH] or [http://pastebin.com/Ja7h9iJv](http://pastebin.com/Ja7h9iJv). Now, when I start [FONT=courier new]google-musicmanager[/FONT], this error is no longer shown.

Well?

I'm on Ubuntu 13.04 with Unity.

---

