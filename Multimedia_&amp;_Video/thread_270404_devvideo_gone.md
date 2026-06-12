---
title: "/dev/video gone"
date: 2006-10-03
forum: Multimedia &amp; Video
---

### Post by MikeBenza on 2006-10-03
I have camstream installed, and it used to work.  There was a /dev/video for my Logitech Quickcam Messenger webcam.  Now, for some reason, there is no /dev/video, and I can't use camstream.

Here's lsusb:
```

Bus 001 Device 007: ID 046d:08f6 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 054c:0069 Sony Corp. Memorystick MSC-U03 Reader
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```Where do I begin to be able to use my webcam again?

---

### Post by n_hendrick on 2006-10-03
You can either make the video link manually as root with mknod or you could try to reinstall your devices with the MAKEDEV command as root in the dev directory, if niether of those techniques work, I'm not sure how to go about restoring your video device. I had this problem serveral times with missing devices just arbitrarily disappearing, sometimes I had to do a whole reinstall to restore the device properly.

---

