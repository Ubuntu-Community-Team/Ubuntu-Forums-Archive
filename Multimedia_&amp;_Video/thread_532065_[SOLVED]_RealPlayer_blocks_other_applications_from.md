---
title: "[SOLVED] RealPlayer blocks other applications from the sound system"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by eurgain on 2007-08-22
Hi,

I use RealPlayer on Feisty (KDE) to listen to the BBC content.  While RealPlayer is running, no other application can access the sound card.  If a KDE app tries to make sound (e.g. KMail's mail received sound) the system "saves them up" until RealPlayer exits, when all of the KDE sounds are played at once.  Most unpleasant!

This does not happen on my OpenSuse 10.2 box.  Other applications can access the sound card normally while RealPlayer is active.

Both machines use Intel 82801 sound hardware, with the Ubuntu box being the newer of the two.

Any ideas?

Regards
A

---

### Post by linuxwizard on 2007-08-22
Look down page almost to bottom for: Getting more than one application to use the soundcard at the same time.

[https://help.ubuntu.com/community/SoundTroubleshooting#head-882ddc981673f44656e4f791858e9a586a007705](https://help.ubuntu.com/community/SoundTroubleshooting#head-882ddc981673f44656e4f791858e9a586a007705)

---

### Post by eurgain on 2007-08-23
Thanks linuxwizard - you got me going down the right path!

First, I edited /usr/bin/realplay to look like that on the SUSE box by changing line 70 to
```
/usr/bin/aoss $REALPLAYBIN "$@"
```

That simple change should do the trick on a 32-bit install.

However, that is not enough for an AMD-64 install because feisty does not install the 32-bit aoss libraries in AMD-64 systems.  Therefore, I went to a 32-bit feisty, and copied its files /usr/lib/libaoss.so.0.0.0 and /usr/lib/libalsatoss.so.0.0.0 to /usr/lib32 on the AMD-64 machine, and did

```
sudo ldconfig
```

Done!

A

---

### Post by Lexyboy on 2007-08-23
Sorry if this is an obvious question, but how can I get hold of a 32-bit libaoss.so.0.0.0 without a 32bit feisty install?  Is there some apt-get command which can install a particular architecture?

I have a similar problem (Realplayer & flash play through the wrong soundcard) which I reckon is due to the same issues.

---

### Post by eurgain on 2007-08-23
Hello, Lexyboy

No, it is not an obvious question, and I have to admit that I did feel that I was copping out by not saying anything about this when I posted my reply (I hoped no-one would notice).

Here is a suggestion:  

Direct your web browser to the repo that has the .deb, and download it -- do NOT try to install it!  From here in the UK, the URL to the repo is (you can click on it below)

[http://gb.archive.ubuntu.com/ubuntu/pool/universe/a/alsa-oss](http://gb.archive.ubuntu.com/ubuntu/pool/universe/a/alsa-oss)

and the file you need is alsa-oss_1.0.14-1_i386.deb .  Right-click/Save-Link-As.  You may wish to change the server if you are not in the UK, but there is probably no need.

Store the file somewhere convenient (like your home directory ~).  Then do:

```
~:$ dpkg -x alsa-oss_1.0.14-1_i386.deb foo
```

This extracts all of the files in the .deb to ~/foo .  You can then look in ~/foo/usr/lib, *et voila*, you should find all the files you need.

I suggest just copying the files libalsatoss.so.0.0.0 and libaoss.so.0.0.0 to /usr/lib32 and then doing ldconfig.

Note: this is not exactly how I did it, but it should work fine.  ***Run *dpkg* as an ordinary user --not root-- to avoid any chance of it breaking important things***, and use sudo/su *only* to copy the library files to /usr/lib32 and to run ldconfig and there is little chance that you will break your computer.  Make sure that you do not copy anything to /usr/lib (as would happen if you installed the .deb) or you will overwrite the 64-bit libraries (although it is, to my mind, questionable that these are really of any use, since I expect that there are few 64-bit programs that do not use alsa by default).

HTH
A

---

### Post by Lexyboy on 2007-08-24
Thanks Eurgain! :KS  Worked a treat, just took a restart of alsa.  I did try googling for the names of the libraries to see if I could find a deb - closest I got was a fedora rpm...  Very useful to know all the individual debs of official ubuntu packages are on the ubuntu website.

Cheers!

Alex

---

### Post by eurgain on 2007-08-24
Alex

I am very pleased you have got this sorted.  It is rather silly that Ubuntu is not set up like this by default, when it works automatically in SUSE.  Maybe it is a desire in Ubuntu to deal with really ancient sound hardware that is supported only under OSS.  I really don't know.

In GNU/Linux systems, the answer is often available for the curious, and there is very little that the system cann do automatically that a user cannot do manually.  That is one reason why it is so good; it keeps few secrets!  Have a look at the file

    /etc/apt/sources.list

This is the file that tells the update system where to get its software from.  If you look at this file, you will see lots of things that look like Internet URLs, beginning with http:// . That they look like URLs is not a surprise, because that is just what they are.  These URLs can be useful to you as they are to the system.

All the best
A

---

### Post by satya_461 on 2007-12-07
Reducing the volume in realplayer changes the volume in other players. Is there anyway to decouple this functionality..?:confused:

or is it a bug in realplayer ? :(

---

