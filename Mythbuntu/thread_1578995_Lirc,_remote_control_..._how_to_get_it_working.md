---
title: "Lirc, remote control ... how to get it working?"
date: 2010-09-21
forum: Mythbuntu
---

### Post by barbex on 2010-09-21
Hi folks!

I have a Hauppauge PVR-350 and have been using the remote control that came with it under old mythtv 0.21. Now I set up a new system with Mythbuntu 10.04 and I can't get the remote to work.

Looking at the howtow in the Mythtv Wiki and in this forum I seem to already fail at the very beginning. Following another howto I tried to do 
ls -lah /dev/input/by-path/
and on the output I only have events from my mouse and the keyboard. So it seems that the IR receiver doesn't even show up.
Now, the module is loaded (lsmod shows lirc_i2c and lirc_dev) and all the lirc.conf and harware.conf are in place but that doesn't do anything.

How can I kickstart this thing to create the necessary device ?

---

### Post by daone on 2010-09-23
I'm trying to get a PVR-250 Remote to work myself. I've been searching the forums and so far I've found it apparently is a bug in lirc that has not been fixed yet in 10.04 Lucid. Would appreciate a reply myself if anyone has info on what they did to get Lirc to work correctly with old PVR tuner remotes.

---

### Post by barbex on 2010-09-26
With the help from the mythtv mailinglist I found the source of my problem:

hardware loaded at boot:
dmesg | grep lirc
[   18.923335] lirc_dev: IR Remote Control driver registered, major 61
[   19.449060] lirc_i2c: chip 0x0 found @ 0x18 (Leadtek IR)
[   19.449063] lirc_dev: lirc_register_driver: sample_rate: 10


It says Leadtek where it should say Hauppauge. 

According to Jarod Wilson (of Fedora Myth(TV)ology fame): "This is an issue with an old version of lirc_i2c mated with a sufficient recent kernel. This was fixed in lirc cvs quite a while back, so all you need is a newer lirc_i2c (like, for xample, the one in the lirc 0.8.7 release), and it should then work just fine."

I haven't tried that yet (I'm afraid of compiling...) but it is probably the solution.

---

### Post by IceCap on 2010-09-28
I'm in the same boat with my PVR-350.  I recently upgraded to 10.04 and the remote doesn't work.

However, I'm confused, why isn't the 0.8.7 lirc release upgraded in update-manager?  Why is the 10.04 LTS running an old version?  I have the 0.23-fixes autobuilds enabled.

  Who is going to jump first and try to get this solved?

  Thanks

  IC

---

### Post by barbex on 2010-09-28
According to 
[http://packages.ubuntu.com/search?keywords=lirc]("http://packages.ubuntu.com/search?keywords=lirc"):
```
    * lucid (utils): infra-red remote control support
      0.8.6-0ubuntu4: amd64 i386
    * lucid-updates (utils): infra-red remote control support
      0.8.6-0ubuntu4.1: amd64 i386
    * maverick (utils): infra-red remote control support
      0.8.7~pre3-0ubuntu1: amd64 i386


```
it looks like we get 0.8.7 with Maverick (Ubuntu 10.10) in the packages. So we can either wait for 10.10 or compile ourselves.

---

### Post by IceCap on 2010-09-28
But we don't know that it actually will work with Lucid.  Maybe I'll compile it this weekend.

 IC

---

### Post by azam_dream on 2010-09-28
my wifi drops the signals in every 15 seconds but stay connected ion window i dont know what is the problem
kindly guide me to getout this problem!!!!!:confused:

---

### Post by barbex on 2010-10-13
[QUOTE=barbex]it looks like we get 0.8.7 with Maverick (Ubuntu 10.10) in the packages. So we can either wait for 10.10 or compile ourselves.[/QUOTE]

So, I just upgraded my mythbuntu box to ubuntu 10.10 and voila! my remote control now works! 
LIRC seems to be fixed in maverick. Hurray!

---

### Post by cliffordsnow on 2010-10-15
I upgraded to 10.10 mythbuntu but the remote still is not working. This is a new MythTV system, only a week old.  The only major item not working is the remote.  I can get some keys to work, but the others don't seem to produce key codes when pressed.  I'm using Hauppauge HVR-1600 video cards with a logitech harmony remote.  (The hauppauge has the exact same symptoms. )  The system load lirc_i2c, lirc_dev and ir_kbd_i2c.  I also get something called rc_hauppauge_new that wasn't there in 10.04.  At least I don't remember it.

Any suggestions?

---

### Post by barbex on 2010-10-15
> I can get some keys to work, but the others don't seem to produce key codes when pressed.

Have you tested the keys with irw? irw should show you output on each key (you can stop irw with CTRL-c). If irw shows output then all you need is a good configuration file in .lirc in your home directory. I'm pretty sure you'll find a file on the mythtv wiki, your card is not uncommon.

---

### Post by cliffordsnow on 2010-10-15
Yes - I did test using irw. I can see all the numbers, the direction arrows, the ok/select, channel up/down and volume up/down.  Nothing for the rest.  I strongly suspect that the remote is putting out something since I can clone the key on my logitech harmony.

---

### Post by cliffordsnow on 2010-10-15
There is a similar problem in Ubuntu Bug #322483.  HAL needs to iqnore input on IR devices.  A files located in /usr/share/hal/fdi/preprobe/20thirdparty/ causes HAL to ignore ignore the IR device.  Without a rule, HAL thinks the IR device is a keyboard and doesn't allow lirc to see the codes.  That is why keys that map to keyboard keys work.  The others don't.  

However, I added a rule to ignore the Hauppauge device, but nothing changed.

---

### Post by sudanmas on 2010-10-16
> **barbex said:**
> So, I just upgraded my mythbuntu box to ubuntu 10.10 and voila! my remote control now works! 
LIRC seems to be fixed in maverick. Hurray!

Did you do a clean install fo 10.10?  Which tv tuner card are you using?  If you're running a similar setup as mine then I might take the upgrade plunge.

Rob

---

