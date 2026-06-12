---
title: "IBM X31 - dapper gdm crashes after update/upgrade"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by Vincent_Lin on 2006-11-04
Hi all,

My x31 has been working great with dapper, for many months.  However, last night I ran sudo apt-get update and then sudo apt-get upgrade, and apt-get downloaded some 168 meg of files and updated my system without a problem.

Then the problem starts:  A new kernel was installed 2.6.15-27-686.  Some OOO stuff, and others.  But my problem is that gdm hangs afrer only finished drawing upper half of the screen (no login yet).  Ctrl-Alt-Fn does not work, nothing works, except power switch or 5 sec to shutoff.

The video driver was radeon, with Direct-rendering enabled.  

I eventually booted with Recovery mode in grub menu and changed xorg.conf into using vesa driver and I can ue this computer now.

It seems to me that radeon driver is somehow broken.  

Has anyone encountered the same issue?  Any quick fix to it?

Thanks in advance.


Vincent Lin

---

### Post by Vincent_Lin on 2006-11-06
Nobody responds.  So I did a synaptic xorg driver removal, and re-installed open source ati driver.  Boom!  It works!!

I guess sometimes file do corrupt while doing apt-get upgrade.

Vincent Lin

---

