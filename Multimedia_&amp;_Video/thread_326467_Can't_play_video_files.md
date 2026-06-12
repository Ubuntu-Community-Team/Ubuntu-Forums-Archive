---
title: "Can't play video files"
date: 2006-12-27
forum: Multimedia &amp; Video
---

### Post by jreid08 on 2006-12-27
Hello, I've been looking around this forum for information on how to watch everything from windows media files to avi and mpg files.  I can't seem to find information on how to get these files to work, or I'm not understanding the lingo.

I'm assuming I need to have something installed on my machine and maybe codecs?  Basically I'm looking to install whatever it takes to watch everything I currently watch on my windowz machine.

I'm using 6.06 if it matters.

Thanks for help and direction!
JR

---

### Post by unrepper on 2006-12-27
go here [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

scroll down to documentation

click on ubuntu.help.com 

on the next page select your version in the top right

select the OS desktop guide and click view in HTML

on the next page scroll down until you find music and video or multimedia something like that

then follow the directions

---

### Post by ahaslam on 2006-12-27
There's also the restricted formats page, see my sig ;)

Tony.

---

### Post by davebriggs on 2006-12-28
Hi, have followed the Restricted Formats instructions, Tony, but am getting an error.

I paste the following:

> sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs gxine libxine-main1 libxine-extracodecs ogle ogle-gui

But am getting:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer0.10-plugins-bad-multiverse

And mpegs and things aren't playing. Any help much appreciated.

Dave

---

### Post by Ripfox on 2006-12-28
Do you have all your repositories uncommented? Also, a good way to get your multimedia going is Automatix. Hope this helps!

---

### Post by davebriggs on 2006-12-28
> **ripfox said:**
> Do you have all your repositories uncommented?

This is how mine looks - what might I need to change?

> 
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by ahaslam on 2006-12-28
```
deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

```
See the 'Ubuntu Tutorials' link in my sig for more ;)

Tony.

---

### Post by 3rdalbum on 2006-12-29
Go to "System> Administration> Software Sources" and check all the boxes, so all the repositories are enabled. When you click "OK" it will ask you if you want to reload the package list: Do it.

Then your command will work.

---

### Post by ahaslam on 2006-12-29
That's what few other distro's offer, the choice to get your hands dirty or to click a few buttons ;)

Tony.

---

### Post by Gremlinzzz on 2006-12-29
wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
sudo dpkg -i w32codecs_20061022-0.0_i386.deb    these codecs play everything .

---

### Post by Gremlinzzz on 2006-12-29
when i tried the commands i pasted i got a 401 error but when i did it from site everything worked fine     [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)     heres the site where you get the commands.

---

### Post by Gremlinzzz on 2006-12-29
> **Gremlinzzz said:**
> wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
sudo dpkg -i w32codecs_20061022-0.0_i386.deb    these codecs play everything . ](*,) 
go to page 2

---

