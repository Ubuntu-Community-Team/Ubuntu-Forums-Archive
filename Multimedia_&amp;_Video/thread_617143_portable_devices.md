---
title: "portable devices?"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by bladednuisance on 2007-11-19
I have Gutsy and am unable to connect to my mp3 player (the new creative zen). Where can I download the proper drivers or enable accessabilitie?

---

### Post by linuxwizard on 2007-11-19
[http://gnomad2.sourceforge.net/](http://gnomad2.sourceforge.net/)

---

### Post by bladednuisance on 2007-11-19
Ive looked into Gnomad2 the compatability list says it should work, but I keep getting this error "No jukebox found on usb bus". I cant find anywhere to change the settings, can somebody help with the set up of gnomad2?

---

### Post by aspiteri on 2007-11-19
I'm in the same boat with a Zen I'm setting up as a present.

I posted this yesterday:
[http://ubuntuforums.org/showthread.php?t=616952&highlight=creative+zen](http://ubuntuforums.org/showthread.php?t=616952&highlight=creative+zen) 

I'd recommend a read of this thread for a helpful background story.
[http://ubuntuforums.org/showthread.php?t=199250&highlight=zen+dapper](http://ubuntuforums.org/showthread.php?t=199250&highlight=zen+dapper)

I'm speculating a problem with new Zens and libmtp.:(

---

### Post by aspiteri on 2007-11-19
My progress might help you, is you Vendor ID in the output of mtp-detect 4158?

Have mailed the libmtp mail list with the following progress and the mtp-detect output.  It looks like my Zen has a new VID ( 4158 ), not listed in the libmtp.rules file.

[I]Hi,

I have just bought a new Creative Zen V to work with Ubuntu 7.10 (Gutsy Gibbon).  Having followed many a thread on how to get Gnomad2, Amarok and Rhythmbox working with libmtp and this new Zen, now strongly suspect libmtp is not happy with this Zen, as the mtp-detect (before and after)shows below.

After doing the following I can now dock the Zen, but gnomad2 does no more than display the device's information and add empty playlists.
To:
/etc/udev/rules.d/libmtp.rules
Added:
# Creative Zen V (Video)
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4158", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
Then:
sudo /etc/init.d/udev restart

Do you have any advice for me?

Regards
Alan[/I]

---

### Post by bladednuisance on 2007-11-22
so I got the cvs version of libmtp (which is supposed to work), but you have to compile from source, but I cant get it to work. I followed some instructions from another site, but I dont think they knew what they were talking about, as I tried their method at least 25 times (paying very close attention to every single bit of info), and was never successful, please, I know somebody has got this to work.

---

