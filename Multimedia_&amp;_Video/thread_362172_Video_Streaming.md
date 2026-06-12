---
title: "Video Streaming"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by deville75 on 2007-02-15
Hi, I've been trying to get streaming video work for the internet on Ubuntu.  I believe I'm using Breezy Badger.  I have Easy Ubuntu, and I tried installing most of the stuff that comes with it.  THe only problem I seem to be having now is flash websites, and streaming video.  If I get this to work then I can become a complete Ubuntu, no Windows, user.  When I load a video from a website ([www.nba.com](www.nba.com) for example) the video says "Kaffiene Loading" or something like that.  But it never finishes loading.  It just stops.  Also i think I'm having issues with Flash and Java,, I have to look closer into why though, I'm not sure.  Does anyone else use Kaffiene for internet video streaming?  Is there a better program?

---

### Post by deville75 on 2007-02-19
Helloo.. anyone here?

---

### Post by sloggerkhan on 2007-02-19
I have no idea about Breezy Badger issues... Started with Edgy Eft.
However, I think you are missing the correct media player and plugins based off what you are saying.

---

### Post by Bloch on 2007-02-19
99% of people here are using LTS 6.06 Dapper Drake or the most recent release 6.10 Edgy Eft.

Would it be difficult for you to update? I would recommend 6.06 Dapper, as the main advantage for using Edgy Eft is to use the fancy transparancy effects and these are still a bit buggy - perhaps not for a new user who needs to get work done. (but great for trying out and impressing friends . . . )

So there will still be lots of help on these forums for 6.06 Dapper in a years time.

Automatix will install the plugins your browser needs to play streaming audio/video
[http://www.getautomatix.com/](http://www.getautomatix.com/)
but as you will see when you visit this page, they support Dapper and Edgy only.

As a general note streaming video can be problematic due to the wide range of proprietary formats. Don't break your head over them!  Flash videos however seem to work fine for everybody.

---

### Post by r4ik on 2007-02-19
Try Mplayer,

[http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox)

Don't know if it is in easy Ubuntu.

---

### Post by deville75 on 2007-02-20
Hey, I'm not sure if I have Dapper Drake.  How do I update.  I went to update Manager in System > Administrations and ran that program.  It updated, but I don't know if that updates my Ubuntu Version.

---

### Post by r4ik on 2007-02-20
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

    * Replace everything with the following lines 

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
 
## Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

    * Save the edited file 

sudo apt-get update
sudo apt-get dist-upgrade

    * Save and close all opened applications, Reboot computer 

Do not know if this still works it might be better to download.

---

### Post by deville75 on 2007-02-20
So doing this will get me Dapper Drake?  Where can I download? Since you say it would be better to download.

---

### Post by r4ik on 2007-02-20
[http://www.ubuntu.com/products/GetUbuntu/download#lts](http://www.ubuntu.com/products/GetUbuntu/download#lts)

Good luck !

---

### Post by deville75 on 2007-02-20
Hmm, ok well doesn't this mean I have to completely format my Ubuntu?  I thought I could just update my current Ubuntu to Dapper. EDIT: Ok I've found a page on ubuntu.com explaining how to upgrade.  I will do that and i should be good.  Also, back to videos, do any of the above suggested players play .wmv videos? because I have a lot of videos that I used in WinXP that are .wmv.  Is there a player that plays this file type?

---

### Post by r4ik on 2007-02-20
Mplayer is my favorite but others might think different.

Here is a Dapper guide, if you havent found it yet..

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

---

### Post by Bloch on 2007-02-20
The default player Totem (also called simply Movie Player) does not have the codecs built in to play wmv files. You can install the codecs and other proprietary software (like java, flash, realplayer etc) using automatix (mentioned above.)

Some other players like VLC and mplayer come with the proprietary codecs built-in. This software is in a legal grey area, because (depending on the country) they might be subjcet to licences. So it's not that they are "better" than the default, it's just that the ubuntu people   distribute a 100% legit system.

I have always found Totem meets all my needs, although occasionally mplayer has been able to play things where Totem crashed.

---

