---
title: "eee pc 1001HA lucid lynx not even turning on wireless"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by Jace84 on 2010-05-01
Ok so i updated to lucid lynx from karmic (i could not get wireless to work on that either) with the hope that wireless might actually work but it doesn't, the keys to turn wifi on don't even work with lucid there is no way to get the wireless to even give me a light that says its on. I have tried installing the rt3090-dkms package and it installed fine (took ages) however that has done nothing at all. It is kind of pointless having a netbook without wireless so anyone got any ideas this is getting very annoying I have yet to use wifi since i bought the netbook

---

### Post by lambdacore on 2010-05-01
i have a 1000 ha and my wireless kind of works.

it connects for 2 minutes, deconnects, connects for 2 minutes, deconnects...
and only since i installed 10.04 2 hours ago.

for your wireless not working at all, ive read that it may have been deactivated in the bios.

check that.

---

### Post by msuug on 2010-05-01
hi there,

rather than upgrading from karmic, i did a fresh install of lucid, and after entering my wpa key, i was able to browse the web. i use the asus 1000 so you may have some luck with that. additionally, i used the main ubuntu, not netbook remix, or anything else.

---

### Post by pdc on 2010-05-01
Hi to Jace84

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

here is a wireless diagnostic script; it is used on OpenSuse and analyses your wireless; makes suggestions and the full result can be posted back here;

run it and let us know how it goes

---

### Post by lambdacore on 2010-05-02
ok, i ran the script.
but when i try to paste the .txt here, it keeps saying i have 10 images and can only use 8 images and won't let me post.

is there anything i should look for in that file?

---

### Post by kc600 on 2010-05-02
> **Jace84 said:**
> Ok so i updated to lucid lynx from karmic (i could not get wireless to work on that either) with the hope that wireless might actually work but it doesn't, the keys to turn wifi on don't even work with lucid there is no way to get the wireless to even give me a light that says its on. I have tried installing the rt3090-dkms package and it installed fine (took ages) however that has done nothing at all. It is kind of pointless having a netbook without wireless so anyone got any ideas this is getting very annoying I have yet to use wifi since i bought the netbook

It's strange that it should not work on Karmic. On my Asus Eee 1001HA, everything - including wireless - worked out-of-the-box with Karmic. The light being off probably means it's switched off by that little blue button on the F2 key... :lolflag: Feel free to follow up on this.

---

### Post by m33600 on 2010-05-15
My EEEPC 1000HA is working now. Yesterday I went to lucid from karmic, and no wifi. With no effort, I got the win driver, the .INF file I downloaded from [http://www.atheros.cz/download.php?atheros=AR5007EG&system=1](http://www.atheros.cz/download.php?atheros=AR5007EG&system=1)
Then I opened SYSTEM>>ADMINISTRATION>>WINDOWS DRIVERS FOR WIRELESS CARDS.
It asked where was the .INF file, I pointed it, reboot and I'm here, full speed. It has been online watching films the whole night, ok, ok, ok!

---

### Post by expatal on 2010-05-17
> **m33600 said:**
> My EEEPC 1000HA is working now. Yesterday I went to lucid from karmic, and no wifi. With no effort, I got the win driver, the .INF file I downloaded from [http://www.atheros.cz/download.php?atheros=AR5007EG&system=1](http://www.atheros.cz/download.php?atheros=AR5007EG&system=1)
Then I opened SYSTEM>>ADMINISTRATION>>WINDOWS DRIVERS FOR WIRELESS CARDS.
It asked where was the .INF file, I pointed it, reboot and I'm here, full speed. It has been online watching films the whole night, ok, ok, ok!

@m33600 - this sounds too good to be true!
But how do you get the SYSTEM>>ADMINISTRATION>>WINDOWS DRIVERS FOR WIRELESS CARDS in your menu? - it's nowhere to be found in mine...
The ath9 module is loaded but network manager shows no sign of any Wifi card.

Eeepc 1101HA, newly installed Lucid (kernel: 2.6.32-22-generic), Wifi: Atheros 9285

---

### Post by bkratz on 2010-05-17
> **expatal said:**
> @m33600 - this sounds too good to be true!
But how do you get the SYSTEM>>ADMINISTRATION>>WINDOWS DRIVERS FOR WIRELESS CARDS in your menu? - it's nowhere to be found in mine...
The ath9 module is loaded but network manager shows no sign of any Wifi card.

Eeepc 1101HA, newly installed Lucid (kernel: 2.6.32-22-generic), Wifi: Atheros 9285

It sounds like he used ndiswrapper.  To get the windows wireless drivers selection  to show up in the system admin menu he would have had to install ndisgtk from synaptic. ndisgtk also marks the ndiswrapper files for installation. synaptic is in system administration also.


A really good source for information is;
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
which is a sticky at the top of the page.

---

