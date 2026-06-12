---
title: "Audigy 2 zs and ubuntu 5.10 amd64"
date: 2005-11-11
forum: Multimedia &amp; Video
---

### Post by GangBoy on 2005-11-11
hi. 
I tried to install ubuntu 5.10 amd64 but i got little problem. If i have audigy in pcmcia slot and i am starting ubuntu, it freeze. And also when i start ubuntu without audigy and everything loads, i plug in audigy card and it freeze again :( .
Got anyone any idea please ???

---

### Post by Xcerca on 2005-11-23
i have a similar problem,   mabey we can help each other....

my system boots fine with the card installed, however i cannot get anysound o the speakers,  i have tried a few of the usual techniqes,   checking volume, enabling every volume option,  making sure the right sound card is selected in volume control, sound and mulitmedia selector,  i also did some things with esd and those scripts,  nothing seems to work.

my card works fine in winxp,   but not in ububtu;  so that is my question to you,  does your audigy work in windows?

---

### Post by GangBoy on 2005-11-26
Yes it works in xp 32-bit fine, excelent sound and so. But I want to make it work also with ubuntu. I think it has something to do with irq's because when i have it plugged in when starting ubuntu it freezes and say something with irq 18, which is reserved in my ubuntu by IO-APIC-Level yenta (don't know what it is). But other pcmcia cards like 5-in-1 reader works, doesn't freeze. How can I make audigy to work???

---

### Post by chien on 2005-12-10
I made mine to work by compiling alsa again, but not all the 5 speakers are working, only the front 2.

---

### Post by RadioImp on 2005-12-13
having the same problem as the original poster.

The PCMCIA version of the Audigy 2 ZS locks the system up when it is inserted, or locks the boot process up if it is inserted at boot.

Had a google for it, and can't find any information other than a couple of other people having the same problem.

Anyone got any ideas?

Cheers

---

### Post by GangBoy on 2005-12-14
Can you write your notebook configuration? Maybe we have the same and are the only two who have problems with it. :( :( :( 
I got Acer aspire 1522LMI with texas instrument pcmcia cardbus.

---

### Post by Falados on 2006-01-10
Google has no answers, I've searched endlessly.  

I've booted in recovery mode and it locks the system when I install the card, even before I log on.  I'm not even sure the output is an error anymore, it just 
looks as though it is using IRQ 11 and freezes.  

During normal non-recovery boot, with the card installed, the system seems to lock when "Setting up ALSA card 0" so I am lead to believe it is a problem with ALSA or some function alsa is trying to perform.

I've checked the Interrupts without the card in (because any time the card is inserted, the system locks), and it appears that IRQ 11 is used by all the USB controllers (uhci_hcd) (ehci_hcd), the cardbus controller (yenta), the display device (i915), and ndiswrapper (Wireless)... Wow, thats a lot of sharing, what are they teaching these kids nowadays?!  

I'm running a Dell Inspiron 1150 which has amazingly poor bios options (as do all Dells =\ )

---

### Post by Falados on 2006-01-10
Excuse the double post.

I did a little experiment, I removed all the modules so that only yenta was left.  Still locks when I insert the card.

I suppose that narrows it down to some type of problem with ALSA?

---

### Post by GangBoy on 2006-01-11
I am happy that i am not the only one having this problem. I already tried kubuntu dapper r2 and it didn't freeze. But than i found out that dapper didn't recognize my pcmcia bus controller from texas instruments :(.

---

### Post by Falados on 2006-01-11
The cardbus should be detected andway.  I mean the card bus itself works, so there must be a kernel module that supports the TI Cardbus.

---

### Post by Falados on 2006-01-13
I installed Dapper and lo and behold the card works and is detected. But now I am having this problem:

[http://www.ubuntuforums.org/showthread.php?t=108143](http://www.ubuntuforums.org/showthread.php?t=108143)

I have a TI as well, so it should be loaded.  If you could post what is displayed after you run
```

$ cat /proc/interrupts
$ lsmod

```

then maybe we can go from there?

---

### Post by ev0 on 2006-02-03
FYI I just installed Kubuntu 5.10 on my AMD Athlon64 3000+ box with Audigy 2 ZX and the sound works just fine from the first moment.

---

### Post by Falados on 2006-02-03
[QUOTE=ev0]FYI I just installed Kubuntu 5.10 on my AMD Athlon64 3000+ box with Audigy 2 ZX and the sound works just fine from the first moment.[/QUOTE]
Yeah, but that card is not the problem.  The PCMCIA card hangs the system when inserted on 5.10, and Dapper resolves the hang problem (New kernel modules probably)  But now I'm getting static problems as mentiond in another thread.  I believe I linked that particular thread in my previous posts.

---

