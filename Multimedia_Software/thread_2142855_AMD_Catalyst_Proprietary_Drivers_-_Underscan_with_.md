---
title: "AMD Catalyst Proprietary Drivers - Underscan with HDTV"
date: 2013-05-06
forum: Multimedia Software
---

### Post by Kissell on 2013-05-06
I have Ubuntu 12.04.02 LTS Desktop with an AMD Radeon card.  

I installed the AMD Catalyst Proprietary Drivers from the manufacturer website.

I use a 47" HDTV at 1920x1080 resolution as my monitor, and everything is great, except when I reboot.  

When the Unity interface starts up I get a lot of underscan, the screen image doesn't reach the edges of the TV.

To fix it I have to open the AMD Catalyst Control Center and move the overscan/underscan bar (it's already in the correct position, but moving the slider and putting it back to where it was makes the screen fit perfect).  

Unfortunately that setting isn't saved, next time I reboot the same thing happens.

It's been going on for many months now, and I haven't found a solution, finally got annoyed with it enough to see if anyone else knew what I could do to fix it?

---

### Post by Kissell on 2013-05-06
BTW: I found lots of posts about running this command, but it doesn't work for me:  "sudo amdconfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0"

I have found a more indepth post that has more commands at: [http://nixnote.blogspot.com/2012/06/amd-catalyst-fixing-underscan.html](http://nixnote.blogspot.com/2012/06/amd-catalyst-fixing-underscan.html)

I'll give that a try tomorrow and report back.

---

### Post by Kissell on 2013-05-07
None of that worked for me...  but it did clue me into this file: /etc/ati/amdpcsdb

I replaced all 38 instances of "DalForceUnderscanAdjustment=V1" with "DalForceUnderscanAdjustment=V0" and next time I rebooted the underscan was okay.

Unfortunately the file changed everything back to "V1" and I haven't rebooted again yet, but if it does underscan again I'll just write a startup script to edit that file before X-windows starts up.

So FINALLY, my long battle with Underscan appears to be over!!!

---

