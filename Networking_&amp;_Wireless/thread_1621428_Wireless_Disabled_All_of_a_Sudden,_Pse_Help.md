---
title: "Wireless Disabled All of a Sudden, Pse Help"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by onaridge on 2010-11-14
I have suddenly lost my wireless network. I have done some research but can't fix the problem.

In var/lib/NetworkManager/NetworkMangaer.state:  wireless enabled =false. I changed that to true via gksu nautilus but a reboot causes it to revert back to false.

Rfkill list gives me hard block yes

I read about this being a bug ([https://bugs.launchpad.net/ubuntu/+source/rfkill/+bug/501973](https://bugs.launchpad.net/ubuntu/+source/rfkill/+bug/501973)) but I don't understand what I read. I am still pretty new with Ubuntu. If I boot into an older kernel the same thing happens. 

I have also lost wireless in my Windows 7 partition (dual boot Windows7/Ubuntu 10.04. Seems like the card is turned off.

Help please, I need my wireless working.

---

### Post by chili555 on 2010-11-14
> Rfkill list gives me hard block yesTranslation: "The [COLOR="Red"]hard[/COLOR]ware wireless switch is set to 'OFF'"

Is that true? What kind of computer is it?

---

### Post by onaridge on 2010-11-14
I am an idiot. For once the Windows troubleshooter helped and it was the switch in the side of the laptop! But I learned a lot in the process of figuring this out so it wasn't a waste of time. So yup I hardblocked it. lol

---

