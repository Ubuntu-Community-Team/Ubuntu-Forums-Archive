---
title: "Streaming music to xbox 360 Doesn't work"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by Cyris on 2009-03-22
For some reason no program or guide for streaming to xbox 360 doesn't work. I've tried xbox360mediasharing fuppes and twonky. none of them work. now let me give you some info on my setup.

OS is unbuntu 8.04 hardy heron
Network is like this xbox 360 wired to ubuntu desktop PC, the desktop is connected to my wireless netgear router via a wireless card. the xbox connects perfectly to the internet through my ICS setup.

let me know if you need to see my fuppes.cfg and vfolders.cfg for fuppes. (fuppes is the last one I just tried about 10 minutes ago).

sorry if this is in the wrong forum.

---

### Post by Cyris on 2009-03-22
So no one has been able to get this to work?

---

### Post by dmizer on 2009-03-23
I don't have an X-box, so I don't know but wouldn't something like [gnump3d](http://rss.cnn.com/~r/rss/cnn_topstories/~3/j--1Bf6MKtM/index.html) work?

Here is a howto: [http://ubuntu-tutorials.com/2006/12/28/how-to-setup-gnump3d-for-a-streaming-media-server-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/28/how-to-setup-gnump3d-for-a-streaming-media-server-ubuntu-510-6061-610/)

That howto is old, but it still works.

---

### Post by JNied on 2009-12-30
I also tried Twonky and could not get it to work.  From my XBox 360 (I haven't tried on the original XBox) it shows all of my video files, but every one that I try to play I get an error.  I tried dumping a few of the same files I tried onto a portable drive and connected it to my 360 and they played just fine, so I know the console can play these files.

I apparently don't have the repository to DL gnump3d via aptitude, so I haven't yet tried that method.  However, the XBox 360 uses Microsoft's proprietary media streaming methods, so theoretically you need special software specifically designed to work with it.  Otherwise a normal network file share would work just fine.

If anyone has any suggestions for Twonky or another way to stream from Linux to the 360 I would greatly appreciate your help.

[=== EDIT ===]
In case anyone cares:
[font=courier new]uname -a
Linux Jason-Ubuntu 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux[/font]

---

### Post by dmizer on 2009-12-31
> **JNied said:**
> I apparently don't have the repository to DL gnump3d via aptitude, so I haven't yet tried that method.  However, the XBox 360 uses Microsoft's proprietary media streaming methods, so theoretically you need special software specifically designed to work with it.  Otherwise a normal network file share would work just fine.
So the XBox does not handle m3u streams?

If not, then the only other thing I can suggest is mythtv which I understand does indeed work with the XBox. Failing that, you could set up a samba share.

---

### Post by JNied on 2009-12-31
I already set up a Samba share, which my other Windows computers can access.  But again, the 360 uses proprietary protocols to stream media, by way of Media Player's Media Sharing feature, so a regular network share will not work, you specifically have to set up Media Share or else use software that mimics that.

---

### Post by dmizer on 2009-12-31
> **JNied said:**
> I already set up a Samba share, which my other Windows computers can access.  But again, the 360 uses proprietary protocols to stream media, by way of Media Player's Media Sharing feature, so a regular network share will not work, you specifically have to set up Media Share or else use software that mimics that.

You need an UPnP server, which means you need mythtv. Here's a good howto: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) ... or you can install mythbuntu: [http://www.mythbuntu.org/](http://www.mythbuntu.org/)

Edit:
Here's an alternative that I found while searching for "upnp ubuntu": [http://ushare.geexbox.org/](http://ushare.geexbox.org/) You could run it through a virtual machine like vmware or virtualbox.

Edit2:
And another that looks real promising: [http://www.freesoftwaremagazine.com/columns/upnp_mediatomb_ps3_and_me](http://www.freesoftwaremagazine.com/columns/upnp_mediatomb_ps3_and_me)

---

### Post by Dodsfall on 2010-03-01
I used ushare and it works just fine. There are several hoops to jump through, especially if using VirtualBoxwith a Ubuntu guest, but it's possible.

---

### Post by Zenxlow on 2010-12-29
Yeah >< I am about to give up. Trying to set up my ubuntu 10.04 laptop connected to my wifi router, to stream to my xbox 360 which is also on the same router.. I tried twonky a year or two ago and it worked great, but Im not sure how I got it to work. I tried multiple walkthroughs found here but to no success :/

I wish I could just plug a direct cable from my laptop into the xbox? but Im not sure how to do that either..

---

### Post by PatchesTheCaveman on 2010-12-29
Try using PS3MediaServer.  It's dead simple to set up, and despite its name, works great with the Xbox 360.

[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)

It should work just fine with your setup as originally described.

---

### Post by JNied on 2010-12-29
> **Zenxlow said:**
> I wish I could just plug a direct cable from my laptop into the xbox? but Im not sure how to do that either..Actually, if you want to go that route, you *can* plug your laptop directly to your TV.  I know it's not quite what you were looking for, but it would allow you to watch videos from your computer on your TV.  Unless your TV is from the Ice Age, all you need is a VGA cable, which you can get from any electronics store.  And if you get an AUX calbe, you'll get the audio from your computer on your TV as well.

As far as the streaming, uShare works decently for me, except that my XBox won't play the videos unless I'm connected to XBox Live, and I've had a problem adding share folders.  But other than that, it *will* recognize my computer on the network, and stream my videos.

I haven't tried PS3MediaServer.

---

