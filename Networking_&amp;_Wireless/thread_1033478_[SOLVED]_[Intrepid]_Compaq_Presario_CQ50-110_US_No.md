---
title: "[SOLVED] [Intrepid] Compaq Presario CQ50-110 US Notebook PC"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by wirewrapped on 2009-01-07
I'm using a Compaq Presario CQ50-110 US Notebook PC. And I'm fed up.

I've tired the latest ath_pci included "out of the box". This doesn't seem to work with my chipset. So I've tried madwifi. Many times, after reinstalling, following steps like blacklisting ath_hal. I've even tried the new ath5k driver. It has worked in weird ways.

The first time I tried ath5k It worked. Cold Reboot and it was off. I tried many instructions to keep it loading at boot, such as modprobe. I've reinstalled some many times just to see ath5k work once, or just show wireless, but not connect even when I have the correct key to a Netgear router I administer. ](*,)

It has connected before, but If anyone has the same type of Notebook as I do please tell me how to get the ath5k driver to work continuously. I really want to install my FF extensions, apps, and other things I enjoy from Ubuntu (all used in Hardy). But, Internet, especially wireless is essential. W/o it, any os that doesn't use it is useless to me. #-o Which is sad. I love even the standard gnome-based, minimal Ubuntu.

Please, please help. I can't wait another few months for Jaunty. I have my college semester coming up.  :frown:

EDIT: I have reinstalled for the 12th time. Atheros ath5k connect to unsecured networks, but will not connect to any secure WEP network with a 10 Char password. Any ideas. I do it through Intrepid's fresh install, where I updated for 01/07/09 3:00pm and using the Network Manager Applet in the default bar. Thanks!

Edit2:
Easy fix. Reinstall. I don't recommend reinstalling for anyone who is coming from Hardy or Earlier.
It pretty much needs to be a complete write over, at least partition wise, because blacklisting doesn't seem to work for me.

```

sudo apt-get install linux-backports-modules-intrepid-generic

```
This is by far the easiest way to get ath5k working on earlier chipsets such as this one I'm using. Madwifi just doesn't seem to work.
And I did not have to enable "backports" in Software Sources. That's a plus.

Thanks Ubuntu. For after three days of torture, you are awesome again.
Now if only I could get that blue light on...:biggrin:

---

