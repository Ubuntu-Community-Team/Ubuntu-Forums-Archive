---
title: "iMon LCD problems"
date: 2007-12-22
forum: Mythbuntu
---

### Post by wombo on 2007-12-22
I am after any help that is available!

I have tried following these instructions but I have failed to get anything to come up on the screen
[http://mythtv.org/wiki/index.php/LCDproc](http://mythtv.org/wiki/index.php/LCDproc)

lcd0 does appear in my dev folder.

When I run dmesg
> [   26.090322] lirc_dev: IR Remote Control driver registered, at major 61 
[   26.338023] bttv: driver version 0.9.17 loaded
[   26.338029] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   26.349770] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Driver for Soundgraph iMON MultiMedian IR/VFD, v0.3
[   26.349775] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Venky Raju <dev@venky.ws>
[   26.349809] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: found IMON device
[   26.349816] lirc_dev: lirc_register_plugin: sample_rate: 0
[   26.349841] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: Registered iMON plugin (minor:0)
[   26.349880] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: iMON device on usb<4:2> initialized
[   26.349890] usbcore: registered new interface driver lirc_imon


Whe I try 'sudo echo "Hello" > /dev/lcd0' it replies Device or resource busy.

I cant work out what ive done wrong. What should I be checking for?

Thanks

---

### Post by JeepFreak on 2007-12-24
Does this sound like it could be your problem?
[http://venky.ws/forums/viewtopic.php?t=299](http://venky.ws/forums/viewtopic.php?t=299)
[http://venky.ws/forums/viewtopic.php?t=306](http://venky.ws/forums/viewtopic.php?t=306)

Which LCD/Display do you have?

Billy

---

### Post by wombo on 2007-12-24
Yes exactly the same as the second one. And by exactly I mean exactly right down to the output files anything that was LCD related ([http://venky.ws/forums/viewtopic.php?t=306](http://venky.ws/forums/viewtopic.php?t=306))

I am running Mythbuntu 7.10, on the Antec Fusion r2 (LCD)

I decided to reinstall as it wasa fresh build anyway.
So right now I have a fresh machine just built, it then asked if it could update all the packages which I said yes.

I did alot of browsing the net and testing things out hence why I decided to go back to a fresh system again.


Do you know which set of instructions are correct for the new LCD?

---

### Post by JeepFreak on 2007-12-24
> **wombo said:**
> Yes exactly the same as the second one. And by exactly I mean exactly right down to the output files anything that was LCD related ([http://venky.ws/forums/viewtopic.php?t=306](http://venky.ws/forums/viewtopic.php?t=306))

I am running Mythbuntu 7.10, on the Antec Fusion r2 (LCD)

I decided to reinstall as it wasa fresh build anyway.
So right now I have a fresh machine just built, it then asked if it could update all the packages which I said yes.

I did alot of browsing the net and testing things out hence why I decided to go back to a fresh system again.


Do you know which set of instructions are correct for the new LCD?

Well, since Soundgraph will not release the info that is needed, it's been a slow process. 
 
[THIS]("http://codeka.com/blogs/index.php?cat=30") seems to be the best solution so far, but I haven't tried it.

[HERE]("http://www.soundgraph.com/Eng_/Forum/ForumDetail.aspx?topMenu=4&subMenu=4&writingId=725&TB=T&CurrentPage=1&fcStateId=1") is the thread to beg Soundgraph for help.

Be sure to post up if you get it working... I'll do the same.

Good luck,
Billy

---

