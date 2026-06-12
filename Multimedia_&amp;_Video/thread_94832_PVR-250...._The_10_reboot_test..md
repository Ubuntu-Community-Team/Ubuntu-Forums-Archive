---
title: "PVR-250.... The 10 reboot test."
date: 2005-11-25
forum: Multimedia &amp; Video
---

### Post by RazorJack on 2005-11-25
Sometimes my Hauppauge PVR-250 card works... and using a mplayer /dev/video0 shows video.  However, sometimes the machine will reboot, dmesg shows the card as a PVR-150, and displays the following error:

Things I have tried:
- Different kernels (Using 2.6.12-10-686)
- Different IVTV versions (0.2.0 to 0.5.0) running 0.4.0 stable now.

This is an intermittent issue and changing nothing but rebooting can make it go working <-> not working.  It almost seems like a hardware issue or conflict.

Hardware is:
2x PVR-250 Hauppauge Tuner 50
Dell Dimension 8100
Latest Bios
Turtle Beach Santa Cruz
NVIDIA Geforce 4 Ti 4600
512MB RDRAM
Digium Wildcard X101P


WORKING DMESG:
[http://pastebin.ca/31113](http://pastebin.ca/31113)

reboot 5 minutes later....

NOT WORKING DMESG:
[http://pastebin.ca/31114](http://pastebin.ca/31114)

Interrupts
[http://pastebin.ca/31115](http://pastebin.ca/31115)

---

