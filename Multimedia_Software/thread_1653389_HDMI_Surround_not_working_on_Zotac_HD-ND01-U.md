---
title: "HDMI Surround not working on Zotac HD-ND01-U"
date: 2010-12-26
forum: Multimedia Software
---

### Post by donsimon on 2010-12-26
[FONT="Times New Roman"](I hope I am posting this in the correct spot)

I have done a bunch of searching but haven't found anything that has worked as of yet so I figured I would post and see.

I just picked up a Zotac MAG HD-ND01-U mini PC and installed Maverick Meerkat 10.10.  I have run all of the updates and installed proprietary drivers.  

Here are some specs: Intel Atom N330, NVIDIA ION, 2 GB DDR2, 160 GB HD, HDMI, 6x USB 2.0, WIFI, Gigabit LAN, 8 channel Audio, VGA, 1x eSATA port, SPDIF optical output.

It is working perfect except for 5.1 surround through either the HDMI or SPDIF.  I have the HDMI going to my Sony 5.1 receiver (STR-KS370) which then goes to my Sony Bravia 46' LCD.   I am running the latest XBMC.  Picture is great, 2 channel sound is no problem for MP3's or copied DVD's with only 2 channel sound (older cartoons).  If I try to play anything with 5.1 I get a "failed to initialize" error and no sound at all.  They are all encoded as AC3 passthrough and I have played some of these on my Blu-Ray (from external HD connected by USB) with no problems and all channels.

I have also tried playing these files through VLC but only the front speakers play.  It is like Ubuntu isn't seeing the back speakers or sending the data appropriately (or I am completely wrong).

Any suggestions?
[/FONT]

---

### Post by donsimon on 2010-12-27
From all of my fiddling, it now isn't seeing the sound card at all so I think I am going to re-install 10.10 from scratch and go from there.

---

### Post by donsimon on 2010-12-27
Working now

This is what I did:

1.  Use synaptics to load &#8220;linux-backports-modules-als-2.6.32-25-generic&#8221;. 
2.  Once installed, reboot
3.  Load &#8220;alsamixer&#8221; in a terminal window, press F6 to change to Nvidia sound, then unmute the channels. It will not display channels unless the backport is loaded.
4.  In the terminal, typed the following: "gksu gedit /etc/pulse/daemon.conf".  This should open up the configuration file in gedit. 
    4a.  Scroll down to find the line ; default-sample-channels = 2. Remove the semicolon at the start of the line and changed the line to "6" (5+1)
    4b. Below it, you should see default-channel-map.  Remove the semicolon and the start of the line and change the line to: "default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe"
5.  In terminal: gksudo gedit /etc/modprobe.d/alsa-base.conf
6.  At the bottom of the file, I added: options snd-hda-intel model=3stack-dig
7.  Saved and closed the file, restarted.
8.  At that point, I was able to get VLC and other stuff to do 5.1.

I had to continue searching because XBMC is my main reason for this box.  XBMC kept giving me "cannot initialize" error.  I found that if I changed the Ubuntu sound preference to use analog (any type) then XBMC worked perfect.

---

### Post by donsimon on 2011-04-29
FYI

I just did a 10.10 to 11.04 Natty upgrade and this was the only thing I had to do:

3. Load “alsamixer” in a terminal window and un-mute the channels

Also, I know that XBMC is not installing on Natty yet due to a 404 error but if you go into the software sources and change the 2 xbmc sources to "maverick" instead of "natty" it will install fine.

---

