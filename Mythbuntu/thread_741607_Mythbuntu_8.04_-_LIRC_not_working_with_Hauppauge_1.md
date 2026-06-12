---
title: "Mythbuntu 8.04 - LIRC not working with Hauppauge 150"
date: 2008-03-31
forum: Mythbuntu
---

### Post by tshannon on 2008-03-31
LIRC doesn't seem to be working correctly for Mythbuntu 8.04.
When I try to run irw, it kills the the lirc session, and I have to restart.

Here's my dmesg | grep -i lirc

[ 3079.087065] lirc_dev: IR Remote Control driver registered, at major 61 
[ 3079.157680] lirc_pvr150: chip found with RX and TX
[ 3079.158631] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 3079.162178] lirc_pvr150: firmware haup-ir-blaster.bin not available (-2)


I want to use the blaster as well as the remote on my 150.  I'm downloading Mythbuntu 7.10 right now, and I'm going to see if that'll work.  Anyone else getting this issue?

---

### Post by foxbuntu on 2008-04-01
there is another detailed post I made  about this issue, please try and post your results there:

[http://ubuntuforums.org/showthread.php?t=742129]("http://ubuntuforums.org/showthread.php?t=742129")

---

### Post by kefkathemad on 2008-05-01
What did you do to get it to work in Hardy? I'm been having the same problem. IR blaster will not work even though I followed the 8.04 instructions.

---

### Post by tshannon on 2008-05-23
If you follow the steps here, it should get you up and running in Hardy Heron with the remote and the blaster.  The repository versions apparently don't work at all for hardy.

[http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)

---

### Post by DirtDart on 2009-06-11
Quick fix for anyone who stumbles across this post (like I did), and don't feel like reading the other posts:

$ cd /lib/firwmware
$ sudo wget [http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin](http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin)
$ sudo reboot


The firmware will be found on the next reboot, and /dev/lirc0 will be created.

---

