---
title: "System freezes after Insertion of PCMCIA card"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by Pixie25 on 2006-07-12
Hello ! 
I installed UBUNTU DAPPER on a Toshiba protege 3440ct (P3 with 128 RAM).
After Installation I installed all that needed to get a PCMCIA card working. The card is D-Link DWL-650+. I used it for 2 days, I did kernel update from 2.6.15-20 to 2.6.15-23, and now the card won't work. 
When I insert the card to the slot the system halts and freezes ! ](*,) it won't work on both kerenels, when booting it halts on 'Loading hardware drivers...'
Help would be apreciated.
10x, Oz.

---

### Post by frock on 2007-04-17
I am having the exact same problem except using Xubuntu.

It freezes during boot.

I am on a Toshiba Sattelite 1805 - using a D-link 650

---

### Post by leibowitz on 2007-04-17
what kernel module are you using, what chipset?

and kernel version.

Also can you revert the kernel update changes back (I suppose you are affected by the same scenario)

---

### Post by RomeReactor on 2007-04-17
Hi. Did you use ndiswrapper to get your card working, and if so, did you blacklist any modules? If you did then, you'll have to do the same with the new kernel (and any subsequent kernel).

---

### Post by frock on 2007-04-19
When booting from Hard drive it just freezes 
Im using Xubuntu on the laptop - kernal 2.6.17-10-generic

This happens when about 5% of the bar on the spash screen loads

When I try to boot from the live cd -
Xubuntu Edgy, Ubuntu Edgy, Ubuntu Feisty Fawn Beta

I get the following error:

ali15x3_smbus 0000:00:08.0:  ali15x3_smb region uninitialized - 
upgrade BIOS or use force_addr=0xaddr
ali15x3_smbus 0000:00:08.0: ali15x3 not detected, module not inserted.

Done some google searching, but so far no answers. 
Im somewhat of a linux noob - around the 6th month mark so please bare with me.

---

### Post by leibowitz on 2007-04-19
it does not seems to be an error, just an output. I means not related to the freeze because this message is printed before loading the freezing module.

Your freezing module is, as far as I understand, related to your D-LINK 650 card. Is that right?

Then I need to know what is the module used by this card. It seems to be a ralink, but I prefer to have confirmation on that.

Then if you know what chip is used, you know what module is used as well. The module is certainly the rt2500

Can you try to boot in recovery mode by selecting the second entry in your boot menu (before booting linux). The boot menu used by Linux is called GRUB and it should have at least two entries like these:
```
Ubuntu, kernel 2.6.17-10-generic
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
```

Just select the second one. This will boot a recovery console with administration privileges. You will not have any graphical interface. In here you can then get informations about your card (lspci -v) and post the output revelant to your WI-FI Card.

And maybe you will need to blacklist the module used by this card to avoid a system freeze on boot.


Note that you can edit your GRUB configuration on the fly, and remove the "quiet splash" options and boot without that to get maximum outpout messages to see what's going on. 


Finaly try to boot without the Wi-Fi card. Does it boot ?
And did you install anything specific to this card  ?

---

