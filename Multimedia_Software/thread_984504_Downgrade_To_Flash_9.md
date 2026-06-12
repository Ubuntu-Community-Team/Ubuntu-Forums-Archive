---
title: "Downgrade To Flash 9"
date: 2008-11-16
forum: Multimedia Software
---

### Post by ScrollMaker on 2008-11-16
I recently upgraded to Flash 10 and Kubuntu 8.10, but now a flash game I play no longer works. I believe this is because of Flash 10 and I would like to downgrade back to Flash 9. How would I go about doing this?

---

### Post by binbash on 2008-11-16
[http://www.adobe.com/support/flashplayer/downloads.html#fp9](http://www.adobe.com/support/flashplayer/downloads.html#fp9)

scroll down a little

---

### Post by BeauGeste on 2009-01-17
> **binbash said:**
> [http://www.adobe.com/support/flashplayer/downloads.html#fp9](http://www.adobe.com/support/flashplayer/downloads.html#fp9)

scroll down a little

No use at all now, there are no instruction on how to downgrade at this URL

---

### Post by fmmarzoa on 2010-02-09
Have you solve this?

Last 10.x.x.x version is a CRAP, it crashed firefox, and produces segfaults both in konqueror an chrome for Linux.

I'd like to downgrade to version 9.x to give it a try, as I didn't used to have such problems with older versions.

BTW, I do not found the version -plugin for Firefox+Linux- that I should download at that URL.

---

### Post by rayburn0 on 2010-02-10
[FONT=Verdana]I am having a slightly similar problem. Though I have not lost use of flash in firefox, firefox does get jittery/freezes with high resolution video and advanced games. The same video plays fine outside of 'firefox' using 'vlc'.  

Troubled System:
===========
Kubuntu 9.10
Kernel:=2.6.31-14-generic 
[/FONT]/usr/lib/firefox-3.5.7/firefox[FONT=Verdana]
Adobe Flash Player version 10.0.42.34 - Linux[/FONT]
RAM:= 2 GB
===========
Oh, and the videos play without problem on Kubuntu 8.10 running Firefox-3.0.5 with [FONT=Verdana]Adobe Flash Player version 10.0.42.34 - Linux[/FONT]. Hardware is identical - both are Dell Optiplex GX270.

Any help would be appreciated. Thanks.

---

### Post by Mustache Villain on 2010-02-10
> **rayburn0 said:**
> [FONT=Verdana]I am having a slightly similar problem. Though I have not lost use of flash in firefox, firefox does get jittery/freezes with high resolution video and advanced games. The same video plays fine outside of 'firefox' using 'vlc'.  
[/FONT]...


You can try increase the session interval at which Firefox saves tabs so it'll make videos less jittery: 

```
about:config
```

```
browser.sessionstore.interval
```

Change it to: **30000**

---

### Post by eatingaltoids on 2010-03-17
anyone solved this issue?

because flash 10 is much to buggy for me.

I found a linux install file on the adobe site, which was a .so file (shared libraries)

can't find how to install those (tried [this]("http://blog.andrewbeacock.com/2007/10/how-to-add-shared-libraries-to-linuxs.html") but it didn't work)

---

### Post by Yellow Pasque on 2010-03-18
You would first need to remove all of your existing flashplayer files first. If you've only installed flash using the ubuntu repo (i.e. synaptic apt), then maybe a simple command like this would work:
```
sudo apt-get remove --purge flashplugin-nonfree
```

If you've manually installed or used scripts to install different versions of flashplayer, you would need to search for files named libflashplayer.so and remove them. Here's a good list of commands to make sure all Flash is off your system: [http://ubuntuforums.org/showpost.php?p=8666948&postcount=72](http://ubuntuforums.org/showpost.php?p=8666948&postcount=72) (32-bit users don't need to bother with the npwrapper commands)

Then you would get the version of Flash 9 you wanted. I don't see a link for FP9 on Adobe's site, except for their archive, which is a 253MB file that you probably don't want to download...
Anyway, once you get the .so file unarchived/zipped, you would do this:
```
cd <directory where you have the file>
sudo mv libflashplayer.so /usr/lib/mozilla/plugins
sudo chmod 755 /usr/lib/mozilla/plugins/libflashplayer.so
sudo ldconfig

```
Firefox should list Flashplayer9 in Tools -> Addons the next time it starts.

---

### Post by eatingaltoids on 2010-03-18
I could remove it but the libflashplayer.so is not working (atleast it isn't installed after I run your commands)

but got it pretty stable right now.

---

### Post by Yellow Pasque on 2010-03-18
> **eatingaltoids said:**
> I could remove it but the libflashplayer.so is not working (atleast it isn't installed after I run your commands)

but got it pretty stable right now.
Huh?

---

