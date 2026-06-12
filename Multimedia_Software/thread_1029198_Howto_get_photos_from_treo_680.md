---
title: "Howto: get photos from treo 680"
date: 2009-01-03
forum: Multimedia Software
---

### Post by mwgrient on 2009-01-03
All,
This is how I get my photos from my treo 680 with pilot-link. It took me some time to figure it out, so I thought I will post this here.

To dir the standard photo directory (not an album):

pilot-xfer -p usb: -D /DCIM/Palm/ -l 
[Note. Afther this command you have to push the sync button on your treo]

To get an photo from your treo 680:

pilot-xfer -p usb: -D /DCIM/Palm/ -f Photo_example_010309_001.jpg

Cheers all,
Marco

---

### Post by caughran on 2009-06-10
Thanks!

---

