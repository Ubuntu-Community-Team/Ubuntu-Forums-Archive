---
title: "Flashplugin 10 break youtube playing?"
date: 2009-01-01
forum: Multimedia Software
---

### Post by amos.shapira on 2009-01-01
Hello,

My environment: ubuntu 8.04 LTS, i386 running on Intel Core 2 Duo.

I have flashplugin-nonfree 9.0.152.0ubuntu1~hardy1 and adobe-flashplugin 10.0.15.3-hardy2 installed on my system.

Ever since I installed the new flash 10 from Adobe a few weeks ago I have troubles playing most youtube movies - they seem to download alright (according to the download progress bar) but pause for a few seconds every few seconds.

How can I either:
1. Fix flash 10 to work right.

or

2. Downgrade to flash 8 (I think that's the version I had before 10).

I'm not interested in the latest whiz-bang - just a working system. I think I tried to upgrade to 10 after some web site said that this is required but if it breaks youtube for me then it's not worth it.

Thanks.

---

### Post by gandaran on 2009-01-01
if you have both flash 9 and flash 10 installed, then firefox is probably using flash 9, you can't have two flash packages installed (including any other type of flash like gnash or swfdec), firefox can only use one, so you either remove the flashplugin-nonfree (9) or adobe-flashplugin  (10) to find out which one works better.

---

### Post by amos.shapira on 2009-01-01
> **gandaran said:**
> if you have both flash 9 and flash 10 installed, then firefox is probably using flash 9, you can't have two flash packages installed (including any other type of flash like gnash or swfdec), firefox can only use one, so you either remove the flashplugin-nonfree (9) or adobe-flashplugin  (10) to find out which one works better.
Thanks for your reply.

While I was picking up the exact versions for my question I noticed dependency on libflashsupport which wasn't installed. Since then I installed the library and restarted firefox and so far youtube plays OK.

Adobe's web site ([http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)) says that I'm using version 10 ("You have version 10,0,15,3 installed") but I'll try not to touch things unless it breaks again.

Cheers.

---

### Post by steveneddy on 2009-01-01
Multiple version of Flash will make Firefox go nuts sometimes.

I would suggest using Flash10 from the Adobe website or from the repos.

I use Flash 10 64 bit and it runs flawlessly.

---

### Post by amos.shapira on 2009-01-01
> **steveneddy said:**
> Multiple version of Flash will make Firefox go nuts sometimes.

I would suggest using Flash10 from the Adobe website or from the repos.

I use Flash 10 64 bit and it runs flawlessly.
Thanks for the warning - wouldn't Firefox just stick to whatever it's using now?

I'm just worried that touching any of the packages in this area might break things which seem to be working right now.

---

### Post by ajgreeny on 2009-01-01
Libflashsupport is only needed for flash 9 as far as I can see, so I suspect you are actually using flash 9, not flash 10. To be certain which is being used go to the addressbar in firefox and type *about:plugins.  *This will tell you exactly which plugins are installed, their versions and also the locations of all the plugin files, eg
```
File name:  /usr/lib/adobe-flashplugin/libflashplayer.so
Shockwave Flash 10.0 r15
```
If you can manage to do a bit of trial and error, I would suggest you get rid of* flashplugin-nonfree*, and reinstall *adobe-flashplugin*.  Certainly I have found flash 10 to be much better than flash 9, and it does not need the libflashsupport.

---

### Post by amos.shapira on 2009-01-01
> **ajgreeny said:**
> Libflashsupport is only needed for flash 9 as far as I can see, so I suspect you are actually using flash 9, not flash 10. To be certain which is being used go to the addressbar in firefox and type *about:plugins.  *This will tell you exactly which plugins are installed, their versions and also the locations of all the plugin files, eg
```
File name:  /usr/lib/adobe-flashplugin/libflashplayer.so
Shockwave Flash 10.0 r15
```If you can manage to do a bit of trial and error, I would suggest you get rid of* flashplugin-nonfree*, and reinstall *adobe-flashplugin*.  Certainly I have found flash 10 to be much better than flash 9, and it does not need the libflashsupport.
I get the same version as you show in your reply ("10.0 r15") but without the full path name.

So far - it LOOKS like the installation of libflashsupport solved the problems (movies which I think got stuck before now play 100%) but since they were intermittent before I can't be sure that it solved it.

I'll try to leave it as it is until next time things stop working, then I'll try to remember to follow your advise.

Cheers.

---

### Post by steveneddy on 2009-01-01
If it ain't broke, don't fix it.

---

### Post by celem on 2009-01-01
Hmmm? I am on Ubuntu 8.10 and experience the same, poor performance with YouTube, namely periodic pauses even though the video is full loaded or the loading is well ahead of the playing. I removed the non-free version and loaded the official repository version and there was no improvement.

about:plugins currently shows:
File name: /usr/lib/adobe-flashplugin/libflashplayer.so
Shockwave Flash 10.0 r15

libflashsupport is not available on Intrepid/8.10

---

### Post by Vryko Lakas on 2009-01-01
[QUOTE=ajgreeny]If you can manage to do a bit of trial and error, I would suggest you get rid of* flashplugin-nonfree*, and reinstall *adobe-flashplugin*.  Certainly I have found flash 10 to be much better than flash 9, and it does not need the libflashsupport.[/QUOTE]
You know, I'm using 8.4.1 LTS, and have been sticking with the non-free plugin from the repos. But I notice that Flash (be it Youtube or some game) tends to take my CPU usage, chew it up, spit it out, and go back for more. It's not exactly a weak processor (Intel E4500), and my RAM usage doesn't seem to suffer much. Does the new FLash 10 plugin from Adobe tend to be less beastly in use?

---

