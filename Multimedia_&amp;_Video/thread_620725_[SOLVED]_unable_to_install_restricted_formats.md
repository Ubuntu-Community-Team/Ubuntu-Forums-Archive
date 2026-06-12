---
title: "[SOLVED] unable to install restricted formats"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by samuel.rajesh on 2007-11-22
Hi ,

I jus made the move to ubuntu 7.10 today and im tearing my hair out .i got it installed and running and connected to the internet and am trying to play divx and mp3 files ,so i tried to install the ubuntu-restricted-extras through **application --> add remove --->** and then searching for the package and then clicking 

what happens is 
1)when its selected a window pops up "list of applications not available "
2) then i click refresh as indicated where it dowloads something 
3) tada nothing happens the apply changes button is not activated 

I tried installing other software as well nothing happens 
tried the terminal and here is what i got 

[B]sam@sam-laptop:~$ sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer0.10-pitfdll
sam@sam-laptop:~$ [/B]

Now what could be the problem ,internet is working jus fine ,please help .


thanks 
Sam

---

### Post by deruberhanyok on 2007-11-23
The command you're using is for an old version of Ubuntu. Some of those packages may not exist for 7.10. In fact it's much easier to get it working in 7.10 now, but you have to make sure you've enabled all of the repositories. Go to system/admin/software sources and make sure you have the 'restricted' and 'multiverse' ones enabled, let it rebuild the package list, and try installing the restricted-extras again.

In fact, once those are enabled, you shouldn't even have to do that. Just try to play, for example, an MP3 file. Double-click on it and it will open up the totem player. You'll get a pop-up saying "you need to download some codecs" and it will show you which ones are available.

---

