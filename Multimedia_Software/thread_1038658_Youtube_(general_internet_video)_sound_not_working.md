---
title: "Youtube (general internet video) sound not working!"
date: 2009-01-13
forum: Multimedia Software
---

### Post by Dark Samurai on 2009-01-13
I can see the video on youtube and other videos online (flash animations, too), but I can not hear any sound!  So I have been searching for a solution to this issue, and I have tried many different things:
1.  Installing alsa-oss and changing the line in firefoxrc to aoss
2.  Adding the command for the start up...

And they have not worked... 
Please help!

---

### Post by 2hot6ft2 on 2009-01-13
8.10 uses PulseAudio so you may want to change it to Auto in
System>Preferences>Sound

fixing pulse
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

For codecs and multimedia put this in a terminal and hit Enter
Applications>Accessories>Terminal

```
sudo apt-get install ubuntu-restricted-extras
```

Then your password and Enter (your password will not be displayed)

It will fix that as well as other missing multimedia you haven't found out about yet.

When it gets to the agreement hit Tab then Enter to accept the Java agreement.

---

### Post by Dark Samurai on 2009-01-13
Tried all that, and it still doesn't work.
It said that my ubuntu-restricted-extras were already up to date, so I got no java agreement thing to agree to...
I tried to fix it from the link to the other forum page, but that did not work either ;(
Oh... what should the default mixer tracks device be in system>pref>sound?

---

### Post by Dark Samurai on 2009-01-19
Bump

---

### Post by merkourio on 2009-01-21
I have also the same problem!!!:(
Can you,please, Declare the answer?;)

---

### Post by Hashmere on 2009-01-21
I too am having this problem and tried the advice that is given above. If anyone can help please do.

---

### Post by gandaran on 2009-01-21
what flash are you using? if flash 9 try flash 10 it usually fixes the flash sound issue, if it still doesn't work you have to fix pulseaudio
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Hashmere on 2009-01-21
> **gandaran said:**
> what flash are you using? if flash 9 try flash 10 it usually fixes the flash sound issue, if it still doesn't work you have to fix pulseaudio
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

This worked. Thank you. I first followed the [help thread]("http://ubuntuforums.org/showthread.php?t=789578") exactly, then I went into Synaptics Package Manager, clicked Mark All Upgrades, and upgraded. Strangely this made my flash stop working, so I de-installed flash from SPM and downloaded it from the adobe website. Sound still did not work, so i logged out, logged back in, and now everything is fine.

---

### Post by Dark Samurai on 2009-01-28
Ok so I tried to do the fix with pulseaudio, but that did not work.  I then tried doing what Hashmere tried, and it still did not work... 
Something I have found out: every time I try to play a flash video or a movie of some kind, the sound does not work, but the type of flashplayer that comes up when i right click it is flash player 9.  When I go into synaptic, it says I have version 10 installed...
MEH
Thanks!

---

### Post by merkourio on 2009-01-30
nothing....

---

### Post by Dark Samurai on 2009-02-02
Bump

---

### Post by Dark Samurai on 2009-02-06
Bump

---

### Post by billybag on 2009-02-19
Same problem. It was a result of upgrading the FLASHPLUGIN-INSTALLER. I noticed it was marked for upgrade so i did so... that is when flash sound stopped working. I have tried uninstalling, resintalling, installing other flash files, installing official adobe flash, re following the PULSE AUDIO thread.. nothing works

---

### Post by billybag on 2009-02-19
Fixed it it seems. I had to manually DL the .tar.gz from Adaobe site. [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)   

MAKE SURE IT IS NOT THE DEB. Then i manually dragged and replaced the libflashplayer.so file to /home/YOUR USER NAME/.mozilla/plugins. I DID NOT run the installer. It kept saying i was entering an in valid directory/path. Not sure why it was screwing up, but it was. PLEASE let me know if this worked for you guys too.

restart firefox. this worked.

---

### Post by wotwhowhy on 2009-02-26
Hello Billybag, it has worked for me with ubuntu 8.10, thanks was starting to pull my hair out.

---

### Post by Dark Samurai on 2009-03-29
Update on the issue:
No sound still... Video works and flash works, but there is no sound!
Help please!

---

### Post by Dark Samurai on 2009-03-29
YES!  It now works!  I found a site that helped: [HTML]http://blog.jayway.com/2008/11/10/getting-sound-to-work-on-ubuntu-810ut/[/HTML]
All I had to do was remove pulse audio!

---

