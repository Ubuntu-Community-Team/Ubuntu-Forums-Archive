---
title: "Create channels.conf for Xine with PCHDTV HD-5500 card"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by theshibboleth on 2007-03-18
I'm trying to create a channels.conf to use with my PCHDTV HD-5500 card. I'm pretty sure the card works as I've been able to view some video in MythTV and the dtvsignal tool from PCHDTV works. However, dtvscan doesn't create a working channels.conf file for me. What do I need to do to do this?

---

### Post by computx on 2007-03-24
I too am having problems. My channels.conf file is empty after running dtvscan.conf >channels.conf.

Any ideas appreciated.

---

### Post by computx on 2007-03-24
I finally got dtvscan to generate the channels.conf. The mojo for me was in this line.
 dtvscan -dvb 0 -fx -o channels.conf
I also used -c 33:40 to tell it to only scan between channel range of 33 to 40 since all my channels are in that range and it made scanning much quicker.
.

---

