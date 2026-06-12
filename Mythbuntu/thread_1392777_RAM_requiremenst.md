---
title: "RAM requiremenst"
date: 2010-01-28
forum: Mythbuntu
---

### Post by aovermy on 2010-01-28
I have a backend only running mythbuntu 9.10. I currently have 1 G of RAM in it. It works fine. However, I recently showed my partner how to stream using mythweb to his laptop and so the system is now acting as not just a media capture server but also as a file server. I haven't noticed any problems yet, other than that I do see some swapping (about 100M worth) with the free command.

I'm wondering if more RAM will be necessary now that the system is getting more use than it has in the past. It's old hardware (nforce2 pro2 chipset with a AMDXP2400 thoroughbreed)  so at a certain price point it might make more sense to repurpose the hw and buy something newer.

The backend does no video encoding, just captures off MPEG2 (for the OTA HD ones) and MPEG4 (my plextor m401) streams that are presented by the PCI or USB device. Typically CPU usage is quite low.

---

### Post by ian dobson on 2010-01-28
Hi,

1Gb is enough for a simple backend. Linux has a habit of using some swap even if it doesn't need it really. My backend has 8Gb and my apps only use about 600Mb-1Gb ram but linux always used 40-100Mb swap until I disabled swap totally.

Regards
Ian Dobson

---

### Post by aovermy on 2010-02-12
Well, I added in an extra GIG just 'cause I could. I found some decent used memory on ebay that tested well. The big performance improvement I'm seeing is in mythweb. It's much faster to load the recordings and listings panel now. Worth the $20 investment.

---

