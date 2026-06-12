---
title: "Revo 3600 as front and back end?"
date: 2009-12-30
forum: Mythbuntu
---

### Post by Amit.Deshpande on 2009-12-30
Hi, I am considering to setup MythTV. I was hoping to get some hints from people who have already done. I am considering using Acer Revo both as my frontend and backend. I am planning to use it with HDPVR. So, in theory, I am thinking to having my HD receiver connect to HDPVR, which in turn will be connected to Revo via USB. For frontend, I was hoping to utilize ION's capabilities. I was wondering if anyone had any word of caution or is it a total no-no?
I plan to use the Revo 3610 which comes with a dual core Atom processor. 
Other configuration I am thinking is using 2 Revo 1600s. One for backend one for frontend. Thanks.

Regards,

Amit

---

### Post by Amit.Deshpande on 2009-12-31
bump

---

### Post by oliver.greg@gmail.com on 2009-12-31
I just got myth installed on mine and setup the hdpvr.  After updates install, I'll let you know.  :)

---

### Post by oliver.greg@gmail.com on 2010-01-01
Well, I am "almost" finished..  Has to wait until today to get more RAM so I could bump my ion up to 512 and get vdpau going.

BTW:  I have a 1600, so a slower machine.

Everything is running great with stock mythbuntu packages (except lirc).  I am just going to drop $20 and get a receiver/blaster and not try to use the HD-PVRs because my time is worth more than it takes to get it going and maintain.  

This little $160 Acer is by far the best mythtv investment I have ever made.  It plays videos better than my $2400 laptop with quad core and ATI video card :)  Of course it is a bit slower though.

All in all, it plays HD streams very well though.  With myth .22, you need 512 on the video card to get vdpau though.

-Greg

---

### Post by oliver.greg@gmail.com on 2010-01-01
Oh - and BTW - It servers up to itself as a frontend and another frontend in the house just fine..

---

### Post by Amit.Deshpande on 2010-01-01
Thanks Greg. I am encouraged by your response. I think I will also get Revo 1600. One thing I am planning to do is get a firewire port to communicate with the digital cable box, instead of IR remote. 
But, yes.. I think I will start with 1600 and see if I need to upgrade to 3610 later.

---

### Post by oliver.greg@gmail.com on 2010-01-02
BTW:  - I spent half of a day trying to use other repos for vdpau, but was fooled by my HDPVR.  The official mythbuntu repos have everything needed for studder/tear free hd video on these ION GPUs.  the mplayer in the repos is vdpau enabled as well.

The 2 well liked non-ubuntu repos for nvidia driver and vdpau enabled myth are not needed.  

I bought a 2GB stick of ram for $32 and popped it in there and bumped system to 2.5gb and video to 512mb.  It has ran without a hitch with my hdpvr since.

-Greg

---

