---
title: "problem when opening mythfrontend"
date: 2008-03-12
forum: Mythbuntu
---

### Post by extasy on 2008-03-12
When I start the computer, I get an error message saying MythPhoto can not mount /dev/sde using the default directory instead. Well I only have 1 disk in the computer and do not have /dev/sde and I never specified this either. In the settings of mythtv I have not found one singel place that referees to /dev/sde, in mythphoto it actually referees to /var/lib/mythtv/pictures where it's supposed to be.

Anyone know where I can find this setting and change it?

---

### Post by uopjohnson on 2008-03-13
I dont' use mythphoto, but is it maybe trying to mount a USB stick automatically or some other external media?

---

### Post by extasy on 2008-03-14
You were right, I have a built in usb 16in1 card reader, I was hoping that when I pushed in a card into the reader the pictures would show in mythtv. But the only way I could to in order to have frontend start correctly was to in settings/settings/General/ page 4 choose ignore devices /dev/sde,/dev/sdd,/dev/sdc,/dev/sdb. This is not ideal and you should be able to have it monitored without getting a nag screen every time you start frontend. A bug or a feature?

---

### Post by uopjohnson on 2008-03-17
Sounds like a bug, but with mythtv not ubuntu.  You may want to visit mythtv.org and look around in the wiki for a solution or else post to the mythtv-users mailing list for any help, or who knows maybe it is fixed in 0.21 and will be taken care of when you upgrade to Mythbuntu 8.04.

---

