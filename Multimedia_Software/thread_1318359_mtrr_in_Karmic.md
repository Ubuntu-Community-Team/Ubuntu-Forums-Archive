---
title: "mtrr in Karmic?"
date: 2009-11-07
forum: Multimedia Software
---

### Post by ticket on 2009-11-07
Is it necessary to set up mtrr in Karmic like it was in Jaunty?

I have a nVidia 6200,  and I setup mtrr in Jaunty by putting this line into 
/etc/gdm/PostLogin/Default:

```
echo "base=0xe0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
```
(The actual text to use inside the quotes depends on your particular graphics card).

One can check if the desired result was obtained by typing in a terminal
```
cat /proc/mtrr 
```

However, in Karmic, with my /etc/gdm/PostLogin/Default edited to set up mtrr, it looks like either /etc/gdm/PostLogin/Default is not executed, or the echo line added is ignored, as the mtrr settings do not change.

However if I enter the command directly in the terminal:
```
sudo -s
echo "base=0xe0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
```
then the changes take effect (but they get lost after a reboot, hence the reason for editing  /etc/gdm/PostLogin/Default, but that trick no longer works in Karmic).

Do I need to set mtrr in Karmic?
If so, how?

---

### Post by ticket on 2009-11-07
Maybe I misunderstand - was mtrr just a fix for Intel GPUs?
Even so, why is Karmic ignoring the edit to /etc/gdm/PostLogin/Default, when Jaunty executed it fine?

---

### Post by ticket on 2009-11-08
Sunday bump.

---

### Post by ticket on 2009-11-09
From [http://blog.nachtarbeiter.net/tag/mtrr/](http://blog.nachtarbeiter.net/tag/mtrr/)

> The bug is a miscommunication between X.org and the Kernel, which results in a misconfiguration of the Memory Type Range Registers (MTRR) in the Kernel. The result is poor performance in video playback and everything that involves graphics in general. This bug has been fixed upstream and in Karmic. A fix for Jaunty has been developed, but is yet to be released.

You can test, if you are affected, by running cat /proc/mtrr on the command line. If you can’t see a line, which ends in write-combining you are most certainly affected by this. You can further check with lspci -vv and check the Region 0 memory range of your VGA adaptor. If you cant find that memory range in your mtrr file, you are probably affected.

So is the bug fixed in karmic?

---

### Post by ticket on 2009-11-11
> **ticket said:**
> Maybe I misunderstand - was mtrr just a fix for Intel GPUs?

I think mtrr relates to Intel _C_PUs.

Can anyone offer any more info?

---

### Post by ticket on 2009-11-15
Another xSundayx Tuesday bump.

---

### Post by ticket on 2009-11-22
Sunday bump

---

### Post by ticket on 2009-11-29
Sunday bump for any clues

---

### Post by ticket on 2009-12-04
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446480](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446480) says PAT will be enabled in karmic.

My /boot/config-2.6.31-15-generic contains

```
CONFIG_MTRR=y
CONFIG_MTRR_SANITIZER=y
CONFIG_MTRR_SANITIZER_ENABLE_DEFAULT=0
CONFIG_MTRR_SANITIZER_SPARE_REG_NR_DEFAULT=1
CONFIG_X86_PAT=y
```

So does this mean I don't need to set up mtrr ?

---

### Post by ticket on 2009-12-12
Saturday bump

---

### Post by ticket on 2009-12-24
Well I found that setting the mtrr up inside /etc/rc.local works in Karmic. Putting it in /etc/gdm/PostLogin/Default results in it being ignored.

I got a very slight increase in performance, using the test site
[http://www.craftymind.com/factory/guimark/GUIMark_Flex3.html](http://www.craftymind.com/factory/guimark/GUIMark_Flex3.html)

Nothing to write home about, though : 8.2Hz went to 9Hz.

So mtrr seems to make some difference.  But is it really needed under Karmic?

---

### Post by ticket on 2010-01-03
Anyone?

---

