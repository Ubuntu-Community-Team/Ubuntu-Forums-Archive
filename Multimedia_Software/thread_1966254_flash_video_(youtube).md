---
title: "flash video (youtube)"
date: 2012-04-26
forum: Multimedia Software
---

### Post by acefromspace on 2012-04-26
I did fresh install of Ubuntu 10.04 lucid lynx, did the recommended post install of multimedia and everything worked great (previously using Ubuntu 9.04 with recommended post install of multimedia and loved it... thanks for the great tips!) I go to youtube and the video plays... until I see the notice telling me I need to install "bla bla bla" and of course I click on this. Now I can't play flash, so I go thru the usual search of these forums, try several different solutions and nothing works. I may just do another fresh install, post install routine and start over. I have tried so many things I don't want to sort this all out, but I would like to know what caused this and how to avoid this happening again.

---

### Post by techsupport on 2012-04-26
> **acefromspace said:**
> I did fresh install of Ubuntu 10.04 lucid lynx, did the recommended post install of multimedia and everything worked great (previously using Ubuntu 9.04 with recommended post install of multimedia and loved it... thanks for the great tips!) I go to youtube and the video plays... until I see the notice telling me I need to install "bla bla bla" and of course I click on this. Now I can't play flash, so I go thru the usual search of these forums, try several different solutions and nothing works. I may just do another fresh install, post install routine and start over. I have tried so many things I don't want to sort this all out, but I would like to know what caused this and how to avoid this happening again.

Try using this post install list as well, and see if you still have this issue:

[http://debianhelp.wordpress.com/2011/12/31/to-do-list-after-installing-ubuntu-10-04-3-lucid-lts/](http://debianhelp.wordpress.com/2011/12/31/to-do-list-after-installing-ubuntu-10-04-3-lucid-lts/)

:guitar:

---

### Post by acefromspace on 2012-04-28
Here are the files I found in usr/lib/mozilla/plugins
flashplugin-alternative.so (link)
libjavaplugin.so (link)
librhythmbox-itms-detection-plugin.so
nppdf.so
I downloaded and extracted flash 11.1.102.63 
copied libflashplayer.so to /.mozilla/plugins (had to create plugins folder)
still doesn't work. I've also tried flash-aid but no help. basically, I go to youtube and video is blank screen (but I can download the video) BTW, I also tried minitube but no luck. does any of this depend on which version of firefox is used? I have version 12, but I think Ubuntu 10.4 might have had 11 originally.

I forgot to mention my computer is old... AMD proccessor (running at 1800 MHz), 512 RAM, and an older SOYO board with slow bus speed. Also using nVidia graphics card (gforce2) I had this all working with Ubuntu 9.04 until I recently when I did fresh install Ubuntu 10.4, so doubt it's the computer, but posted this just in case.

temporary solution... flashvideoreplacer works great (opens movie player)
At this point (after hours and hours reading posts) I am going to do a fresh install and start over. After the install, I will run the recommended multimedia routine and then back up filesystem at that point. BTW, I looked at my old Ubuntu 9.04 (it's on another hard drive that is currently in an external USB unclosure) and things looked very different! I must have really screwed up my recent Ubuntu 10.4 (concerning firefox) This time I will be careful and make notes of everything I do.

Started over... fresh install of Ubuntu 10.4, recommended multimedia post-install.
 Now, before I screw things up again, what is the best way to add flash to firefox? 
I tried sudo apt-get install flashplayer-installer
Got this (screenshot)

---

### Post by josephmills on 2012-04-30
install medibuntu 
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu

```
and 
Ubuntu-restricted-extras

```
sudo apt-get install ubuntu-restricted-extras

```

---

### Post by jmore9 on 2012-04-30
I still use an 1.8 gig cpu sempron and it is fast enough for everything i do.  Watching and downloading youtube or other site's videos at the same time.  My major issue with flash was bad/buggy wideo drivers on my machine.  Once that got sorted out everything works great.

---

### Post by josephmills on 2012-04-30
flash debuger 
program I wrote 

[http://ubuntuforums.org/showthread.php?t=1958405](http://ubuntuforums.org/showthread.php?t=1958405)

you might like

---

### Post by acefromspace on 2012-05-03
josephmills, I did that already (repositories)
Actually, I am quite happy with FlashVideoReplacer (for now) and VideoDownloadHelper

---

### Post by acefromspace on 2012-05-26
I recently tried google chrome and flash works. Also, trying chromium and seamonkey.

---

