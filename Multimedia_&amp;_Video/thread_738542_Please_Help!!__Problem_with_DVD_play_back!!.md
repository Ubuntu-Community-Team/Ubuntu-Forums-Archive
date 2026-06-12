---
title: "Please Help!!  Problem with DVD play back!!"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by Gove on 2008-03-28
Hi all,

This is my first post and I am new to the ubuntu world.  I have installed Gutsy on my Lenovo R61 think pad and have tried everything to get encrypted DVDs playing but nothing has helped.  I will outline what I have done and then if people have any suggestions that would be fantastic.

I have installed the following:

- Ubuntu restricted extras
- libdvdccs
- libdvdread3
- totem-xine
- w32codecs

But even though I have done all of this I still get the following message when I try to play a DVD through totem:

An Error has occured

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss? 

I then installed gxine and VLC but still can't play DVD through them.  I am not sure what to do next and getting pretty frustrated.  Can anyone help me out.  I know there are heaps of posts about DVD play back already but none of them seem to answer my question.

If you need more detail let me know.

Cheers.

---

### Post by Bruce M. on 2008-03-28
> **Gove said:**
> Hi all,

This is my first post and I am new to the ubuntu world.  I have installed Gutsy on my Lenovo R61 think pad and have tried everything to get encrypted DVDs playing but nothing has helped.  I will outline what I have done and then if people have any suggestions that would be fantastic.

I have installed the following:

- Ubuntu restricted extras
- libdvdccs
- libdvdread3
- totem-xine
- w32codecs

But even though I have done all of this I still get the following message when I try to play a DVD through totem:

An Error has occured

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss? 

I then installed gxine and VLC but still can't play DVD through them.  I am not sure what to do next and getting pretty frustrated.  Can anyone help me out.  I know there are heaps of posts about DVD play back already but none of them seem to answer my question.

If you need more detail let me know.

Cheers.

Welcome to Ubuntu

Check out QuickStart in my sig, it will load everything you need in one click.

---

### Post by xc3RnbFO8P on 2008-03-28
Try to install again:
> 
wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb
> wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

I Synaptic Package Manager:
dvd95
dvdauthor
liba52
liba52 dev
libdvdnav4
mkisofs

---

### Post by Gove on 2008-03-28
> **Ringi said:**
> Try to install again:




I Synaptic Package Manager:
dvd95
dvdauthor
liba52
liba52 dev
libdvdnav4
mkisofs

Thanks for the rely.  I installed everything that you told me to and reinstalled the packages also.  But it still doesn't work...

I have been looking around and think that I might have to set a region for my dvd player.  This is a brand new machine and I am not sure if a region has been set.  Does any one know anything about this?  If I do this will this mean that I will only be able to watch DVDs from region 4 or is this just something that you have to do and libdvdcss2 will allow you to watch DVDs from any region.

If I should set the region could someone please tell me how to do this?

Also, I am not exactly sure what quick start is?  I am a bit new to this game.  Could someone explain it a bit more before I install it.

Many thanks again.

---

### Post by xc3RnbFO8P on 2008-03-29
Do you got this problem with all Dvd's?
Here is thread about new encryption:
[http://ubuntuforums.org/showthread.php?t=727671&page=2]("http://ubuntuforums.org/showthread.php?t=727671&page=2")
and here is region set: 
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDsRegion]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDsRegion")

---

