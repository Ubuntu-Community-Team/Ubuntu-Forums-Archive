---
title: "iPod Shuffle on Ubuntu 9.10"
date: 2010-02-25
forum: Multimedia Software
---

### Post by kasun04 on 2010-02-25
Hi,

Is there a supported player in Ubuntu to manage music in ipod shuffle. I used Songbird plugin but didn't work well with shuffle.

Any other alternatives ?

-Kas

---

### Post by kasun04 on 2010-02-26
Is the plugin comes with Songbird works fine?

---

### Post by JK3mp on 2010-02-26
Songbird is a good player but a bit of a mess at overcomplicating some things. Amarok works fine, but u manage it more like a usb drive than an iPod. All in all it works the same, can add music, listen to music from it etc.

---

### Post by PaulReaver on 2010-02-26
rhythmbox works with ipods

I also use gtkpod.

---

### Post by qyot27 on 2010-02-26
Songbird's iPod extension is broken, has been for all revisions after 1.2 from what I've read.  I've not gotten it to work on either Ubuntu or Windows.  Never recognizes the device even if the system sees it.  I'd love to be able to use Songbird, though, as the interface is nice (and I'm one to eschew library management apps in general - I like my Winamp 2 successors, if not Winamp 2 itself).

I have a 2nd gen Shuffle.  The only solution I've found that works well is gtkpod.  Worked with both MP3 and AAC files (assuming, I guess, that the AAC files have the proper iTunes IDs in the MP4 container headers - I still have yet to test that, though...gotta find a way to remux my non-iTunes-purchased stuff while retaining tags).

---

### Post by kasun04 on 2010-02-26
Thanks dude. GTKPod works.
:)

---

### Post by CompBio on 2010-03-05
> **PaulReaver said:**
> rhythmbox works with ipods

I also use gtkpod.

I haven't managed to get either of those (nor gnupod) to work with my 2GB shuffle.  gtkpod doesn't seem to know about 2GB shuffles.  

gnupod seems to do all the right things and it outputs happy messages, but after I umount the shuffle, unplug it from the USB and try to listen to it, I get the same message: "Please synch your shuffle with iTunes". :mad:

This happens even when I include the Serial # in the mktunes script.

Any suggestions?

---

### Post by qyot27 on 2010-03-05
> **CompBio said:**
> I haven't managed to get either of those (nor gnupod) to work with my 2GB shuffle.  gtkpod doesn't seem to know about 2GB shuffles.  

gnupod seems to do all the right things and it outputs happy messages, but after I umount the shuffle, unplug it from the USB and try to listen to it, I get the same message: "Please synch your shuffle with iTunes". :mad:

This happens even when I include the Serial # in the mktunes script.

Any suggestions?
You could try to run foobar2000 in Wine and make it sync with the iPod (using the right extension).  I've used it to sync before on XP, although I have a 2nd Gen Shuffle 1GB.  [This thread]( http://www.hydrogenaudio.org/forums/index.php?showtopic=54933) details setting it up.  At the bottom there's a blurb about Wine not supporting USB devices, but according to the [Wine Wiki](http://wiki.winehq.org/USB), it supports USB through libusb-1.0 (of note: the hydrogenaudio thread was last edited in March '09, the entry on the Wine Wiki is from July of '09...and I would guess that if you're using the winehq repository, then you'd have USB support - but I can't say, because I've never tried to use a USB device in an app running in Wine; if not, then you'd need to compile Wine with the USB patch).

---

