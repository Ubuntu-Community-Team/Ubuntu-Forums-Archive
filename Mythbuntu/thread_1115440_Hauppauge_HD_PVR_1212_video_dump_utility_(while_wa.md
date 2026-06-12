---
title: "Hauppauge HD PVR 1212 video dump utility (while waiting for 0.22)"
date: 2009-04-03
forum: Mythbuntu
---

### Post by davidstoll on 2009-04-03
I am using github to edit (and branch as necessary) a utility that some may find useful for getting video out of the HD PVR.  Supposedly, 0.22 will have support for this device...but who knows when 0.22 will be released.  You can try trunk or svn, but that can be a headache.

I did not attach the script to this post because it will be maintained here:

[http://github.com/jettero/videodump-pl/](http://github.com/jettero/videodump-pl/)

If you have suggestions as to how to make this script better, please let me know.

David

---

### Post by davidstoll on 2009-11-15
Even though 0.22 is out the functionality seems to be a little less than ideal.  The main thing with 0.22 is that now the device driver is built in.  So, now you don't have to screw with re-installing the driver every time the kernel gets updated.

Now my script just hums right along.

---

### Post by vronp on 2009-11-24
David,

Just curious, does the 0.22 code release coincide with the 9.10 Mythbuntu release?

thanks,
Dave

---

### Post by davidstoll on 2009-11-24
> **vronp said:**
> David,

Just curious, does the 0.22 code release coincide with the 9.10 Mythbuntu release?

thanks,
Dave

Yes, but I wish I had not upgraded.  9.10 is very flakey.  My script was very reliable.  There is support, but it's just sort of frustrating.  Sometimes it doesn't change channels.  It's also amazing how often the front end "bails" (i.e. crashes) or just freezes up and I have to kill it.

Plus it does not address the fact that the video device can change at each reboot.  i.e. video0 can become video1 and Myth does not seem to be able to keep track of that.

If I had known of all these problems, I would have stuck with 9.04.  By the way, I'm still using my script, it just seems to work more reliably.

---

