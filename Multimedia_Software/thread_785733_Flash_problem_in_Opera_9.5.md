---
title: "Flash problem in Opera 9.5"
date: 2008-05-07
forum: Multimedia Software
---

### Post by magnus0 on 2008-05-07
Flash doesn't work on some sites, it shows the flash content for a second and then the screen goes white there. Youtube works perfectly. It seems to be only on some sites. Myspace doesn't work either. The same page works on Firefox and in other browsers, but not in Opera. How can I fix this?

---

### Post by magnus0 on 2008-05-08
Here's a screenshot from myspace. The player appears for 2 seconds and then the area goes white.

---

### Post by gandaran on 2008-05-08
which flash did you install, gnash, swfdec or adobe (flashplugin-nonfree)?
check that you only have one installed, the flashplugin-nonfree,could be conflicting if you have two of them installed.

---

### Post by magnus0 on 2008-05-09
I only have flashplugin-nonfree installed. But come it works on most of the sites but not on some sites?

---

### Post by Nameless_one on 2008-05-09
I am guessing you use version 9.27, the one downloadable from the site. That version is a bit old (although stable). 

Great progress has been made on Flash, in Opera's development builds. You can download the latest build from here:

[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

I used to have the same problems as you, but the problem's been solved in the development builds a long time ago. Try it.

---

### Post by Colonel Kilkenny on 2008-05-09
Myspace flash is not working with Opera 9.5, don't know the reason. Probably because the flashplugin still sucks quite a lot. Or maybe it has something to do with Myspace sucking quite a lot.

Atm the situation is pretty much no-can-do.

---

### Post by Nameless_one on 2008-05-09
Myspace works fine on my Opera 9.50, though.

---

### Post by Colonel Kilkenny on 2008-05-09
> **Nameless_one said:**
> Myspace works fine on my Opera 9.50, though.

Myspace flashplayer working? Actually with the snapshot released today it seems to be a little bit better but it's still crashing a lot.
Try to listen one song from here [http://www.myspace.com/massiveattack](http://www.myspace.com/massiveattack) (change volume and song) and see if it crashes.
It is crashing constantly for me.

---

### Post by gandaran on 2008-05-09
> **Colonel Kilkenny said:**
> Myspace flashplayer working? Actually with the snapshot released today it seems to be a little bit better but it's still crashing a lot.
Try to listen one song from here [http://www.myspace.com/massiveattack](http://www.myspace.com/massiveattack) (change volume and song) and see if it crashes.
It is crashing constantly for me.

works fine for me, playing the song and a flash video there at the same time, only crashed when I clicked to play the second video at the same time!

---

### Post by Solrac924 on 2008-05-11
in synaptic, do you have the libflash-SWFplayer installed?

---

### Post by magnus0 on 2008-05-11
> **Solrac924 said:**
> in synaptic, do you have the libflash-SWFplayer installed?

Yes I have, but that doesn't solve anything. Flash still appers for a second and then the area goes white.

---

### Post by Solrac924 on 2008-05-14
i've read that 9.50b2 solves this prob, but not for the x86_64 version of Opera. supposedly Adobe doesn't support 64bit users for now.
i figure, i just need something that works, so i try installing the i386 version. no. there's an error saying it's the wrong architecture. AARRRGGGHHHHH!!!!  ](*,)

---

### Post by Jozza The Wick on 2008-05-14
> **Colonel Kilkenny said:**
> Myspace flashplayer working? Actually with the snapshot released today it seems to be a little bit better but it's still crashing a lot.
Try to listen one song from here [http://www.myspace.com/massiveattack](http://www.myspace.com/massiveattack) (change volume and song) and see if it crashes.
It is crashing constantly for me.


Yeah, that works for me in Opera 9.5b2, 7.10, as well. Listening to it while I type this response. Good taste, by the way!

Sorry I'm not more help, though... I love Opera so I feel your pain.

For what it's worth, after struggling with Flash in Opera, (I'd got it working in Firefox no problem), I uninstalled 9.23, deleted the /usr/lib/opera directory where the plugins were (dunno if the uninstall was supposed to do that), then installed 9.50b2. Was suprised to see that the Opera home page had a flash video on it, which worked immediately - didn't even have to configure or anything!

Good luck!

---

### Post by doorknob60 on 2008-05-14
> **Solrac924 said:**
> i've read that 9.50b2 solves this prob, but not for the x86_64 version of Opera. supposedly Adobe doesn't support 64bit users for now.
i figure, i just need something that works, so i try installing the i386 version. no. there's an error saying it's the wrong architecture. AARRRGGGHHHHH!!!!  ](*,)

[http://blog.isnotworking.com/2007/11/opera-9-on-ubuntu-with-amd64.html](http://blog.isnotworking.com/2007/11/opera-9-on-ubuntu-with-amd64.html) :) That guide isn't for 9.5 but it should work just the same.

---

### Post by magnus0 on 2008-05-15
But I have a 32 bit processor.

---

### Post by gandaran on 2008-05-15
> **magnus0 said:**
> Yes I have, but that doesn't solve anything. Flash still appers for a second and then the area goes white.

may I ask you, why did you install libflash-SWFplayer?
opera 9.50b2 works fine just with the adobe flash (flashplugin-nonfree)
any other flash package installed Will only complicate thinks!

---

### Post by miceagol on 2008-06-01
Somebody have a solution for flash in 64 bit Opera?

---

### Post by gaffurabi on 2008-06-12
**[on 64bit AMD]**
9.50 stable release is out but opera still insists on not running flash :(

i have non-free plug-in installed from apt and firefox runs just fine with it, but strangely opera doesn't 

any solution folks?

(also java doesn't run)

---

### Post by yyka on 2008-06-12
hey, magnuso,I use opera 9.5 too I have had the same problem like you, I have intalled flash player 10 beta, it's works better !! test it and tell me :D

[http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/]("http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/")

yyka the french :lolflag:

---

### Post by gaffurabi on 2008-06-13
so to get it working i should remove all flash plugins and install non-free v10 beta and it's gonna work? :s

---

### Post by eival on 2008-06-13
> **yyka said:**
> hey, magnuso,I use opera 9.5 too I have had the same problem like you, I have intalled flash player 10 beta, it's works better !! test it and tell me :D

[http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/]("http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/")

yyka the french :lolflag:

im going to try this out when i get home, cause ive got the same issue, although im using the 64bit version cause i have 64bit Hardy, is this issue happending in the 32bit aswell?

---

### Post by eival on 2008-06-13
hold up, Adobe are making a flash plugin for linux OS'?

its about damn time, now for Photoshop...

---

### Post by magnus0 on 2008-06-13
> **yyka said:**
> hey, magnuso,I use opera 9.5 too I have had the same problem like you, I have intalled flash player 10 beta, it's works better !! test it and tell me :D

[http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/]("http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/")

yyka the french :lolflag:

I installed it. It's faster that flash 9, but It crashed like in the first 20 seconds. Tried it again and it crashed again in about 20 seconds. The whole browser just locks up and I had to kill it.

---

### Post by eival on 2008-06-13
figures its not availible in 64bit

---

### Post by nanog on 2008-06-15
[SIZE="6"]**Install flash in 64 bit ubuntu**[/SIZE]

(A tutorial by Romeo Adrian Cioaba originally at this dead link: [http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html))

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
```

1.1 To be sure we don't have any other old flash libs let's cleanup the folders where it usually resides:
```
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```


2. Install ia32-libs and latest nspluginwrapper
```
sudo apt-get install ia32-libs nspluginwrapper
```


3. Download the latest flash player from Adobe Labs and extract it:
cd ~
```
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz
tar zxvf flashplayer10_install_linux_051508.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/
```

4. Use nspluginwrapper to install the plugin and link it to firefox
```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
```


5. make sure opera plugins points to:

/usr/lib/mozilla/plugins/

---

### Post by Splinterhood on 2008-06-16
I installed Opera 9.5 and Flash this morning. Both from their own websites, and "uninstalled" flash-nonfree with synaptic (it wouldn't install because the md5 checksum didn't match so I really didn't uninstall anything) so they are both current as of today and I have the path specified in opera to where the plugin is installed, and it mostly works.
  I can watch youtube stuff, but sometimes the video does some major frame and audio skipping, then it settles down and works. In google maps it will sometimes place me in crazy places, and have the zoom out layers mixed with the zoom in layers, but this too settls down after a minute or so. I tried the myspace thing too, and the songs stop playing each time I scroll in the page. The pandora widget will sometimes load or be a blank white rectangle.
  Through all of these things my CPU usage was at 50% or more, with the operapluginwrap being the top user, memory is ok though. I also noted that my Cpu Freq was at 1Ghz and rarely went to 2.2 (it made it to 99% and 2.2GHz in the myspace scrolling).
  I was wondering if this this was because of the way the kernel/Cpu queing was working. I think that the stock ubuntu kernel uses Completely Fair Queing, I am probably wrong. I was wondering if anyone has tried changing this to OnDemand or something. I will try it if no one has tried this yet.[-o<
As a side note, I have had some trouble loading pages, I have to reload the page several times to get it to show, anyone else seen this?

---

### Post by gandaran on 2008-06-16
here's another way to make 32-bit flash work in 64-bit opera.
[http://my.opera.com/csant/blog/index.dml/tag/linux](http://my.opera.com/csant/blog/index.dml/tag/linux)

---

### Post by gaffurabi on 2008-06-16
> **nanog said:**
> [SIZE="6"]**Install flash in 64 bit ubuntu**[/SIZE]

(A tutorial by Romeo Adrian Cioaba originally at this dead link: [http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html))

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
```

1.1 To be sure we don't have any other old flash libs let's cleanup the folders where it usually resides:
```
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```


2. Install ia32-libs and latest nspluginwrapper
```
sudo apt-get install ia32-libs nspluginwrapper
```


3. Download the latest flash player from Adobe Labs and extract it:
cd ~
```
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz
tar zxvf flashplayer10_install_linux_051508.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/
```

4. Use nspluginwrapper to install the plugin and link it to firefox
```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
```


5. make sure opera plugins points to:

/usr/lib/mozilla/plugins/

thanks a lot mate that did the trick :guitar:

---

### Post by mrgnash on 2008-07-15
That did the trick for me too :D Many thanks!

---

### Post by freonchill on 2008-07-24
*** i take no responsibility if you lose/delete anything, please read the entire post before doing anything *** 


i had a problem where i would go to pages (like youtube) and the flash would show up as garbled txt (like if you open a binary file in a txt editor)

i kept changing versions of opera (8.27, 8.29, 9.51, 9.52) and it never fixes the problem. i also tried disabling each and every one of the plugins for flash video, that didnt work either.

then i got sick of the problems and just deleted all the contents of the opera directory

*** WARNING - SAVE YOUR BOOKMARKS FILE FIRST - opera6.adr - WARNING ***
*** WARNING - SAVE YOUR BOOKMARKS FILE FIRST - opera6.adr - WARNING ***
*** WARNING - SAVE YOUR BOOKMARKS FILE FIRST - opera6.adr - WARNING ***

install 9.51 or 9.52 beta (find the beta on the opera daily snapshot page) 
```
/home/$user/.opera/
sudo rm *.*
```this deletes all the settings for opera

run opera again, and all of the settings are reset and flash should work again. something from the older opera settings 9.2x or < 9.51 does not get over-written when you upgrade to 9.51 or newer

---

### Post by trailofdead on 2008-07-25
I have a similar problem as the OP.  I'm using the latest flash 10 beta from adobe right now.  Same as before.  It will play flash videos, sometimes it hangs for a while, about 15 seconds or so, then it'll start playing again.  This usually happens if I exit from full screen youtube videos.  Other times where the flash video was will just turn white and I have to reload the page.  flashplugin-nonfree 10.0.1.218 and opera 9.51.

---

### Post by variaatio on 2008-09-05
> **freonchill said:**
> *** i take no responsibility if you lose/delete anything, please read the entire post before doing anything *** 


i had a problem where i would go to pages (like youtube) and the flash would show up as garbled txt (like if you open a binary file in a txt editor)

i kept changing versions of opera (8.27, 8.29, 9.51, 9.52) and it never fixes the problem. i also tried disabling each and every one of the plugins for flash video, that didnt work either.

then i got sick of the problems and just deleted all the contents of the opera directory

*** WARNING - SAVE YOUR BOOKMARKS FILE FIRST - opera6.adr - WARNING ***
*** WARNING - SAVE YOUR BOOKMARKS FILE FIRST - opera6.adr - WARNING ***
*** WARNING - SAVE YOUR BOOKMARKS FILE FIRST - opera6.adr - WARNING ***

install 9.51 or 9.52 beta (find the beta on the opera daily snapshot page) 
```
/home/$user/.opera/
sudo rm *.*
```this deletes all the settings for opera

run opera again, and all of the settings are reset and flash should work again. something from the older opera settings 9.2x or < 9.51 does not get over-written when you upgrade to 9.51 or newer

Thanks that helped. allso SAVE ALL .adr files, those contain your contact infos, widget lists, notes etc.

---

### Post by Zelandeth on 2008-09-08
Cheers for that!  Clearing the .opera directory seems to be key - no matter what else you've done, something in there seems to be breaking the flash player.

Now happy as I don't need to revert to Firefox for any flash-intensive site!  This seems to have sorted the issue with Opera pulling stupid amounts of CPU resources on such pages as well - figured the two were related.

---

