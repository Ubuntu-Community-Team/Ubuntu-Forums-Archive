---
title: "dvd codecs"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by gimpguy2000 on 2007-08-31
I used to play dvds now I get **no plugin found **for any media type of player. What happened? I have no idea.  Any specific plugins? It won't say, just an error as stated.  

TX

---

### Post by ThrobbingBrain66 on 2007-08-31
You need libdvdread3 and libdvdcss2.  The first is in either universe or multiverse and the second you'll have to get through a 3rd party repo like Seveas repo.

---

### Post by gimpguy2000 on 2007-08-31
Hi and thanks. Well, it seems they are\still installed. I did reinstall, still nothing. It's as if it's all blocked or simply can't find the plugins. 

TX

---

### Post by gimpguy2000 on 2007-09-01
Hmmm... it seems Ubuntu has decided not to allow them at all then. No longer are they anywhere to be found, even apt-get won't get it now. This explains why then, it seems Ubuntu has blocked the use of this. Well, whatever. If this is the case, forget it. I am getting well fed up with not being able to use open source for what I need, I have used it for months now and it's only getting more frustrating. 

You can't use DVD stuff, you can't play half the games as they don't work,  I have had to re-install YET again thinking it was something wrong with my system, yah, thanks Ubuntu.... 
So far Ubuntu has been more of a pain than Windows, fix Java, fix DVD stuff, fix printer problems, fix camera issues, fix ipod issues, crap, and this is just to get the stuff working for Pete's sake. :(

So I have found this to be limited to say the least and I think no longer will I be using it. What good does it really do if you can't do anything besides use it to browse? It may be free, may be safe, but i'll take my Windows safety issues over this crap any day and I hate Windows. 

After almost 4 months, forget it. 


X

---

### Post by mrjcdf on 2007-10-15
I completely agree and I am a bit pissed off about it. I thought this distro was about freedom but it seems its shackled.
I cant play a ******* DVD?!!!!!!!!! complete madness.
Time to find a new distro!!!!

---

### Post by rsambuca on 2007-10-15
DVD's will perfectly fine in Ubuntu.  Please calm down a bit.  [Instructions are right here.]("https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd")

---

### Post by stanz on 2007-12-22
Hi All,
Fresh Gusty install ~
odd, those [instructions ]("https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd")did not work--at all. As For the Seveas repo - not available for Gutsy, at least as far as the 
Ubuntu sources.list generator is concerned.
That page was written for 7.04, but for 7.10 'libdvdplay0' isn't in the repo's
either.
[ This page]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") offered some advice, but it just got my player to flash quickly and exit.
Enough for this day, will check back and update.

---

### Post by osx on 2007-12-23
> **rsambuca said:**
> DVD's will perfectly fine in Ubuntu.  Please calm down a bit.  [Instructions are right here.]("https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd")

Thanks. These instructions worked for me without even using the steps to make gxine the player (I was previously using Totem to watch Ice Age); however, I recommend people click on the help icon in Ubuntu to get the correct instructions for the Ubuntu version they are running. In the standard Gnome installation of Ubuntu (i.e., not Kubuntu or the other versions), help is the question mark icon in the Gnome panel. You can also get to it by clicking on the System menu and selecting "Help and Support" from the list of options. You'll find the instructions in the section called "Music, Videos and Photos". Then select the "Movies, DVDs and videos" link and, finally, click the "Playing DVDs" link.

I tried playback of Ice Age using Totem (default selection), gxine (per the Ubuntu help instructions) and VLC using "vlc dvd://" (without the quotation marks) in the Multimedia command options per the help documentation for VLC command options listed on the VLC website at [http://www.videolan.org/doc/play-howto/en/ch04.html](http://www.videolan.org/doc/play-howto/en/ch04.html). Also, for gxine and VLC, I used the Ubuntu Synaptic Package Manager to install them plus all the listed plugins.

Quality of the playback for each of these applications was roughly the same although gxine seemed slightly better. Also, only gxine produced playback that matched my Toshiba DVD player in that all the menu items (such as icons) were visible. The other two applications did not show everything (such as the acorn icon next to the "PLAY" option) and even skipped some menu features.

Other than that it seems to be a matter of one's personal preference as to which application they use for DVD playback.

On a different, but slightly related note, anyone interested in helping to improve the use of Ubuntu should install the Ubuntu Device Database tool and use it to send "...device, config, logs and QA data for the Ubuntu Hardware Database." To install it, click on the Applications menu, then Add/Remove, select the System Tools category, and scroll down to "Ubuntu Device Database".

---

### Post by osx on 2007-12-23
> **mrjcdf said:**
> I completely agree and I am a bit pissed off about it. I thought this distro was about freedom but it seems its shackled.
I cant play a ******* DVD?!!!!!!!!! complete madness.
Time to find a new distro!!!!

I understand your frustration and that of gimpguy2000 in his above complaints, but understand that the shackling you refer to comes from companies producing proprietary software that is locked down by their choosing, not Ubuntu's or any other version of Linux.

Also, realize this, if you do find another free distro of Linux that already has the proprietary software installed for you, it could very well be that the distro is in violation of some sort of copyright. This means that while another distro may work for you today, the next version may have that feature broke in order to be in compliance with the maker's copyright. My point being that this is not a problem with Ubuntu or any other Linux distro. Nor is Windows exempt from this problem, hence the need for programs like Divx and VLC for Windows.

Actually, I find that Ubuntu handles most other forms of propriety codec installation much better than Windows does because Windows makes me go out and find the codec myself without assitance and has no built-in feature (such as Ubuntu's Update Manager) to make sure that other vendors' software is kept up-to-date. Windows passes that task onto the user or the software maker by requiring them to include some sort of software updater in their applications.

Besides, having to learn how to do something on a computer is something you will always have to go through no matter which operating system you use. Trust me, as someone who has only been a serious Linux user for a little over a year now, the frustration level drops greatly as you learn more and more. For me, the frustration level of learning Linux was no higher than it was when I first learned to use Windows. And now, I find my frustration level is even lower since there is so much less maintenance with Ubuntu than I had with Windows (e.g., no running disk defragmenter, manual file system checks, disk cleanup, constant anti-virus and spyware scans).

---

### Post by kjb34 on 2007-12-23
> **osx said:**
> Thanks. These instructions worked for me without even using the steps to make gxine the player (I was previously using Totem to watch Ice Age); however, I recommend people click on the help icon in Ubuntu to get the correct instructions for the Ubuntu version they are running. In the standard Gnome installation of Ubuntu (i.e., not Kubuntu or the other versions), help is the question mark icon in the Gnome panel. You can also get to it by clicking on the System menu and selecting "Help and Support" from the list of options. You'll find the instructions in the section called "Music, Videos and Photos". Then select the "Movies, DVDs and videos" link and, finally, click the "Playing DVDs" link.

I tried playback of Ice Age using Totem (default selection), gxine (per the Ubuntu help instructions) and VLC using "vlc dvd://" (without the quotation marks) in the Multimedia command options per the help documentation for VLC command options listed on the VLC website at [http://www.videolan.org/doc/play-howto/en/ch04.html](http://www.videolan.org/doc/play-howto/en/ch04.html). Also, for gxine and VLC, I used the Ubuntu Synaptic Package Manager to install them plus all the listed plugins.

Quality of the playback for each of these applications was roughly the same although gxine seemed slightly better. Also, only gxine produced playback that matched my Toshiba DVD player in that all the menu items (such as icons) were visible. The other two applications did not show everything (such as the acorn icon next to the "PLAY" option) and even skipped some menu features.

Other than that it seems to be a matter of one's personal preference as to which application they use for DVD playback.

On a different, but slightly related note, anyone interested in helping to improve the use of Ubuntu should install the Ubuntu Device Database tool and use it to send "...device, config, logs and QA data for the Ubuntu Hardware Database." To install it, click on the Applications menu, then Add/Remove, select the System Tools category, and scroll down to "Ubuntu Device Database".

Thanks for that. I used the help thingie to get DVD playings. At first tried Gxine but that did not work even after getting the necessary plugins so i download VLC and it worked perfectly. :)

---

### Post by fredjara on 2007-12-25
I've been having trouble running DVD's.  I'm brand new to UBUNTU (2 days).  I've read about all the dvd codex's.  Where can I download them?  I need gxine, all the libdvd codexes, etc.  Is there a place I can download them.  Also, is there a Glossary of terms available.  I have no idea what some of the terms are.  Thanks for any and all help!
Fred

---

### Post by cor2y on 2007-12-25
Look here for getting dvd playback in ubuntu and all the other restricted media formats.
[http://medibuntu.org/](http://medibuntu.org/)
Its also on the wiki if you know where to look

---

### Post by osx on 2007-12-26
> **fredjara said:**
> I've been having trouble running DVD's.  I'm brand new to UBUNTU (2 days).  I've read about all the dvd codex's.  Where can I download them?  I need gxine, all the libdvd codexes, etc.  Is there a place I can download them.  Also, is there a Glossary of terms available.  I have no idea what some of the terms are.  Thanks for any and all help!
Fred

Whenever you need to install software in Ubuntu, I recommend you run Synaptic Package Manager and use the search/find feature to see if the desired software is listed. If it is, and the box next to it is not green, then it means the software is not yet installed. To install the software, just put a checkmark next to the box and click the Apply button. If Ubuntu needs to install additional software that the program you want depends on, it will list the other required software and you will have the option of installing that software at the same time.

In standard Ubuntu (i.e., not Kubuntu or the other versions), Synaptic Package Manager can be found by clicking on the System menu, then select Administration, and you will find it listed. An added benefit of installing through Synaptic Package Manager is that Ubuntu will then check and maintain updates for you.

---

