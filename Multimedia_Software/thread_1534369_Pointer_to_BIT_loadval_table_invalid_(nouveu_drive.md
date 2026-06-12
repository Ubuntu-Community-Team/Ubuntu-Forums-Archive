---
title: "Pointer to BIT loadval table invalid (nouveu drivers)"
date: 2010-07-19
forum: Multimedia Software
---

### Post by ssottile70 on 2010-07-19
Hello,

I get this odd behavior when I boot by 10.04 Kubuntu version on a EliteBook 8540w laptop. I get the error
......
 [FONT="Courier New"][drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid[/FONT]

and the boot stops!!!

The odd thing is that I do not get this error all the times I turn on my laptop but it is a random behavior. When I do not get it and log in to my system, this is what I found in the syslog and kernel log.

============
[FONT="Courier New"]Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514234] [drm] nouveau 0000:01:00.0: ... appears to be valid
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514238] [drm] nouveau 0000:01:00.0: BIT BIOS found
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514241] [drm] nouveau 0000:01:00.0: Bios version 70.16.61.00
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514243] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514314] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514316] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514320] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514323] [drm] nouveau 0000:01:00.0: 0: 0x00000040: type 0x40 idx 0 tag 0xff
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514326] [drm] nouveau 0000:01:00.0: 1: 0x00001161: type 0x61 idx 1 tag 0x07
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514347] [drm] nouveau 0000:01:00.0: 2: 0x00001231: type 0x31 idx 2 tag 0x07
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514350] [drm] nouveau 0000:01:00.0: 3: 0x01000331: type 0x31 idx 3 tag 0xff
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514352] [drm] nouveau 0000:01:00.0: 4: 0x01000446: type 0x46 idx 4 tag 0xff
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514355] [drm] nouveau 0000:01:00.0: 5: 0x02000546: type 0x46 idx 5 tag 0xff
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514357] [drm] nouveau 0000:01:00.0: 6: 0x00010631: type 0x31 idx 6 tag 0x51
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514360] [drm] nouveau 0000:01:00.0: 7: 0x00010746: type 0x46 idx 7 tag 0x51
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514363] [drm] nouveau 0000:01:00.0: 8: 0x00020847: type 0x47 idx 8 tag 0x52
Jul 6 09:07:52 ssottile-laptop kernel: [ 16.514365] [drm] nouveau 0000:01:00.0: 9: 0x00000900: type 0x00 idx 9 tag 0xff[/FONT]
===============

Kernel used is 2.6.32-23-generic #37-Ubuntu SMP.

Thanks
/ss

---

### Post by donTommazo on 2010-11-01
I can confirm that I have the same behavior with my HP Elitebook 8540w (Intel Core i7 Q720) and a fresh install of Ubuntu 10.10. 

Anyone that have an idea of what this is all about?

/ Tomas

EDIT: I searched the bugzillas for this, and found a bug report for Fedora system on the same Elitebook model. Unfortunately they haven't yet figured out how to solve it. Do you think we should submit an error report for the Ubuntu bugzilla as well?

[https://bugzilla.redhat.com/show_bug.cgi?id=630765](https://bugzilla.redhat.com/show_bug.cgi?id=630765)

---

### Post by RedBluespot on 2010-11-16
I got the same errormessage[I]:

[/I][I][   14.510607] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   14.792778] nouveau 0000:01:00.0: Invalid ROM contents
**[   14.859203] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid**
[   14.884188] [drm] nouveau 0000:01:00.0: 0xDD22: Failed parsing init table opcode: INIT_ZM_I2C_BYTE -6
[/I]
I think it's related to the Intel-i Processors.
Don't know how to fix it yet. I've been asking around.

---

### Post by schwefeltyrann on 2011-04-16
The same problem with my HP 8540w. Pointer to BIT loadvol table invalid.

What to do now?

---

### Post by skin27 on 2011-05-07
I have the same problem when installing Ubuntu with Wubi:

[https://bugs.launchpad.net/wubi/+bug/775552](https://bugs.launchpad.net/wubi/+bug/775552)

---

### Post by russell.reynolds on 2011-09-09
I had this problem on my Elitebook 8540w. Probable bug in noveau video driver. I edited the boot.cfg and added vga=771 to the boot parameters. ...then installed the nvidia drivers and removed the vga=771 from the boot.cfg. Worked for me.

---

