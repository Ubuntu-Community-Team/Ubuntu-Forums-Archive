---
title: "Can I copy mp3 file onto Android/iPhone via Nautilus?"
date: 2013-06-22
forum: Mobile Technology Discussions (CLOSED)
---

### Post by glln0v on 2013-06-22
I have no experience with smartphones. I was wondering, if I connect an iPhone via USB to Ubuntu will I see iPhone show up in the Nautilus devices sidepane? Can I then simply copy an mp3 file onto the iphone so that I can use that mp3 file as a iPhone ringtone? Can this procedure be done with Android?

---

### Post by 3rdalbum on 2013-06-24
> **glln0v said:**
> I have no experience with smartphones. I was wondering, if I connect an iPhone via USB to Ubuntu will I see iPhone show up in the Nautilus devices sidepane? Can I then simply copy an mp3 file onto the iphone so that I can use that mp3 file as a iPhone ringtone?

No, sorry - iPhones and iPods and iPads can only be loaded with music using Apple's own software.

They are designed to lock you into the Apple software, which sadly only works on Macintosh and Windows.

> Can this procedure be done with Android?

Yes, absolutely. You can load music onto Android phones without needing any special software.

---

### Post by SeijiSensei on 2013-06-24
Let me insert a note of caution about connecting to Android.

The most recent versions of Android on devices like my Samsung Galaxy S3 no longer support the USB mass storage protocol for mounting the phone as a browseable device.  It uses the "Media Transfer Protocol" which was poorly supported in Ubuntu until version 13.04.  Until I upgraded to that version, my Ubuntu machines could not see the filesystem on my phone.

---

### Post by 3rdalbum on 2013-06-25
> **SeijiSensei said:**
> Let me insert a note of caution about connecting to Android.

The most recent versions of Android on devices like my Samsung Galaxy S3 no longer support the USB mass storage protocol for mounting the phone as a browseable device.  It uses the "Media Transfer Protocol" which was poorly supported in Ubuntu until version 13.04.  Until I upgraded to that version, my Ubuntu machines could not see the filesystem on my phone.

True, but there are other ways of getting the music onto the phone if you're using 12.10 or earlier with an Android 4.x device. You can download a free app to make the phone behave like an FTP server that you can access over wifi on your Ubuntu machine, or you can use adb push, or you can Bluetooth files across, or you can put your phone's memory card (if it contains one) into a memory card reader and transfer music across that way. You can do none of those things on an iPhone.

Or upgrade to Ubuntu 13.04 :-)

---

### Post by SeijiSensei on 2013-06-25
Yes, I spent $3 on the WiFi File Transfer Pro app to handle this problem before, but being able to browse the phone as an ordinary device is much more convenient.

---

### Post by glln0v on 2013-06-29
> **SeijiSensei said:**
> Let me insert a note of caution about connecting to Android.

The most recent versions of Android on devices like my Samsung Galaxy S3 no longer support the USB mass storage protocol for mounting the phone as a browseable device.  It uses the "Media Transfer Protocol" which was poorly supported in Ubuntu until version 13.04.  Until I upgraded to that version, my Ubuntu machines could not see the filesystem on my phone.

Thanks Guys. Let me know do I understand correctly: If I buy Nexus 4, I will be able to usb connect the phone to Ubuntu 13.10 and can add .mp3 files onto the phone via Nautilus interface? (Then obviously I can install ubuntu-touch on Nexus 4 later this year and there should be no problem accessing nautilus I assume).

---

### Post by 3rdalbum on 2013-06-30
> **glln0v said:**
> Thanks Guys. Let me know do I understand correctly: If I buy Nexus 4, I will be able to usb connect the phone to Ubuntu 13.10 and can add .mp3 files onto the phone via Nautilus interface? (Then obviously I can install ubuntu-touch on Nexus 4 later this year and there should be no problem accessing nautilus I assume).

Yes, with 13.04 and 13.10 it will work "out-of-the-box".

You can also make it work in a roundabout way in 12.10 and below.

---

### Post by leg on 2013-06-30
> **SeijiSensei said:**
> Let me insert a note of caution about connecting to Android.

The most recent versions of Android on devices like my Samsung Galaxy S3 no longer support the USB mass storage protocol for mounting the phone as a browseable device.  It uses the "Media Transfer Protocol" which was poorly supported in Ubuntu until version 13.04.  Until I upgraded to that version, my Ubuntu machines could not see the filesystem on my phone.And I am having problems transferring files even on 13.04. I can mount and copy files to my computer but I can't write to the phone or view files from it. So still not perfect.

---

