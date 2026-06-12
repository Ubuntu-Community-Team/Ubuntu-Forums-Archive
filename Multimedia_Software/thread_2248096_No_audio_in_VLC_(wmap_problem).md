---
title: "No audio in VLC (wmap problem)"
date: 2014-10-12
forum: Multimedia Software
---

### Post by A Traveller on 2014-10-12
Hi all.

I have tried searching for a solution to this problem, but all the results on the web are old and I couldn't find any up to date info on whether this problem can be fixed.

For some .wmv files, the video plays fine in VLC but there is no audio. I get the message "VLC does not support the audio or video format wmap". I have tried playing it in MPlayer, Firefox and just installed SMPlayer as well but with the same result (video but no audio).

Ubuntu 10.04 LTS
AMD 64bit
VLC 1.0.6 Goldeneye
MPlayer Totem Movie Player 2.30.2, Movie Player using GStreamer 0.10.28
SMPlayer Version: 0.6.8 (SVN r3213), Using Qt 4.6.2 (compiled with Qt 4.6.0), Using MPlayer SVN r1

Has anyone got any up to date relevant info that could help please?

Thanks.

---

### Post by mc4man on 2014-10-12
That versions of players & ffmpeg in *10.04 *don't support wmap (and a lot more
So some updated info would be to get more recent, 12.04 at a min.

---

### Post by A Traveller on 2014-10-16
Thanks for the advice mc4man.

So I take it there is no way to get wmap to work fully in 10.04 then? I'd be willing to carry out any installations, etc.

---

### Post by mc4man on 2014-10-16
Well actually looking back there was some indication it could work back then. 
[http://ubuntuforums.org/showthread.php?t=1273474](http://ubuntuforums.org/showthread.php?t=1273474)
Have a read thru & let me know what the deal was...

---

### Post by A Traveller on 2014-10-17
Thanks for the reply and link.

Unfortunately, I don't have the TINIEST idea what they are talking about in that thread! Haha.

Thanks.

---

### Post by Vladlenin5000 on 2014-10-18
Any reason why you aren't running a current Ubuntu release? 10.04 is out of support since a long time ago...

---

### Post by A Traveller on 2015-03-29
Sorry I never replied to your question,  Vladlenin5000. I never saw your post. I just wish to use 10.04 at the moment.

Anyway, here I am again and the problem was never fixed but I am trying to have another attempt.

I have tried following the instructions at the link below but I have learnt that Medibuntu no longer exists

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html)

so I tried the following in a sudo terminal

[http://download.videolan.org/pub/libdvdcss/1.3.99/libdvdcss-1.3.99.tar.bz2](http://download.videolan.org/pub/libdvdcss/1.3.99/libdvdcss-1.3.99.tar.bz2)

but got an error saying : No such file or directory

How can this be when I am able to download the file from that link perfectly fine? Is this what I need anyway?

Thanks.

---

### Post by Rob Sayer on 2015-03-29
That download gets you the libdvdcss library.  It's for playing DVDs and has nothing to do with .wmv files.

As mentioned, just install a supported version of ubuntu or whatever.  10.04 is unsupported.  Unsupported = no support here or anywhere else.

---

### Post by mc4man on 2015-03-29
I seemed to have been thinking you were using hardy, not lucid. If desired try this ppa, it's possible that the vlc there can handle wmap
(- you'd need to also install any ffmpeg upgrades from that ppa, ect. A sudo apt-get dist-upgrade may be needed..

If deciding to try that ppa I'd first install ppa-purge so reverting if needed or wanted  could be much easier, especially if using dist-upgrade
[https://launchpad.net/~lucid-bleed/+archive/ubuntu/ppa](https://launchpad.net/~lucid-bleed/+archive/ubuntu/ppa)

Overall I'd consider this a bit risky as 10.04 shortly will be completely EOL & you may have issues reverting the ppa packages, ect., & I can in no way vouch for that ppa

---

### Post by A Traveller on 2015-04-04
Thanks Rob Sayer. I also have 12.04 installed but I wanted to get this to work in 10.04.

Thanks for the info mc4man. It's been appreciated.

---

### Post by Siddhartha_Kashyap on 2015-04-04
Have you installed restricted extra?? Open terminal and type : 
sudo apt-get install
ubuntu-restricted-extras

---

