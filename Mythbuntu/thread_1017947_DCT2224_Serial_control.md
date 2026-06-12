---
title: "DCT2224 Serial control"
date: 2008-12-21
forum: Mythbuntu
---

### Post by quaa on 2008-12-21
Hello I was wondering if anyone could please point me in the right direction in getting my motorola DCT2224 Cable Box working with mythbuntu.  I previously had it connected with a MCEUSB2 irblaster but i would like to connect it with a serial rs232 cable.
I have tried searching but could not find anything.  All i could find is homemade serial irblasters.  anyways if anyone could please point me in the right direction that would be very appreciative!

thank you!
quaa

---

### Post by quaa on 2008-12-21
ok well i have gotten past where i was.  I found the dct-channel in the contrib folder but every time i try to run it i get 
root@myth:/home/mythuser/dct-channel# ./channel -v -d /dev/ttyS0 -c 100
channel: /dev/ttyS0: Input/output error


or even trying /dev/ttyS1
root@myth:/home/mythuser/dct-channel# ./channel -v -d /dev/ttyS1 -c 100
channel: /dev/ttyS1: Input/output error



any ideas?

---

