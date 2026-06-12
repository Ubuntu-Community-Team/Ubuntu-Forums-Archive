---
title: "Restoring bcm43xx as default Broadcom wireless driver in 8.04, Hardy Heron"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by trevornetley on 2009-03-09
This is the information I would have been grateful to find clearly presented in one place when I came to install ubuntu 8.xx (having neglected to upgrade 6.10 when it was still possible), so I hope it may be useful to others. Despite my best efforts with the firmware I was unable to get the new b43 driver to work in either 8.04 or 8.10 and my chipset is not compatible with the STA/wl driver. I also faced two obstacles: although my chipset (bcm4306 ver3) has been shown to work with b43, I have it in a PCMCIA card, and my hard-wired ethernet connection has failed (I believe due to a hardware problem in the laptop). I may have another go when Jaunty is fully released. I also tried the new Open-Source firmware (see linuxfans below), but it failed even more completely. Meanwhile the 'deprecated' bcm43xx works for me and I propose to stick with it until the situation becomes clearer. My suspicion is that b43 itself does not cover all PCMCIA eventualities (support for PCMCIA was only introduced in June/July 2008 ).

I have reported the problem to [email]bcm43xx-dev@berlios.de[/email] with diagnostics and will send a report to the web forum shortly.

It is worth giving again the two main sources of information for Broadcom wireless:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) and [http://linuxfans.betaserver.org/](http://linuxfans.betaserver.org/). The first is brisk and clear, but perhaps overly optimistic ... The second is more based in the real world and is expanding.

Note that of 8.04, 8.10 and 9.04, only Hardy (8.04) actually retains a copy of bcm43xx **(comment please)**. Thus if you have problems with b43 and/or STA/wl, I would suggest sticking with Hardy until b43 is sorted for you. The comment that b43legacy replaces bcm43xx (see linux wireless link above) is misleading, if technically correct. The choice of b43 or b43legacy is made for you by the new ssb module and that's fine if it works for you; if not, I suggest you stick to bcm43xx (if you can) while the problems are resolved. Note that Intrepid and newer have substantially different versions of Ndiswrapper as they do of the b43 firmware, so use what is tailored for where you are if you go those routes.

Here is what to do to restore bcm43xx as default to Hardy (repeat: does not work for Intrepid or Jaunty).

Open the terminal and open an edit screen for the blacklist:

```

gksudo  gedit /etc/modprobe.d/blacklist

```

then you need to find the line where bcm43xx is blacklisted and comment it out (precede that line with a hash mark #). Add to that section blacklists for b43 (which includes b43legacy) and ssb, so it now reads:

```

#blacklist bcm43xx
blacklist b43
blacklist ssb

```

(but see [thread]885847[/thread] as below re possible dificulties blacklisting ssb if it has a dependency and how to check that) then save and quit. The changes now need to be fixed using

```

sudo update-initramfs -k all -u

```

and the bcm43xx firmware needs to be installed, see  [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

again for detailed instructions, or use your previous firmware if you've had bcm43xx working before (it remains unchanged).

Then reboot and you should find that Network Manager is in a position to connect you to your chosen SSID using the specified security protocol.

This post is heavily based on [thread]885847[/thread] **Comprehensive ndiswrapper troubleshooting guide** by 'pytheas22' to whom many thanks, and that's also useful if you need to use Ndiswrapper with a Windows driver rather than bcm43xx (either because it doesn't work or because you need extra speed or additional features not supported by bcm43xx). The main Ndiswrapper link is given in linuxfans. Note also comments about possible difficulties blacklisting ssb.

Reversal should be obvious if you need to re-instate b43 - just restore the blacklist to its original state, update-initramfs as above and reboot.

---

### Post by kevdog on 2009-03-09
Its obvious you have done a fair amount of research and troubleshooting into this matter, however I find it confusing that your 4306 rev03 card does not work with b43 or openfwwf.  I have the exact same chipset with the card being made by Linksys.  I suspect your problem may not be with the chipset itself but the actual manufacturer of the card.

---

### Post by trevornetley on 2009-03-11
It's worse than that! According to the published list, the Asus PCI card of the same description also works. Which is why  I'm suggesting that the PCMCIA implementation in b43 may have a problem. Thanks anyway.

I have now posted a report at [thread]1093354[/thread], since this is not really the appropriate thread for it.

**(Problem now solved - trying to use European channel 12 which is not supported by Hardy or Intrepid versions of b43 - now moved to 10. I will edit and shorten 1093354 appropriately.)**

---

