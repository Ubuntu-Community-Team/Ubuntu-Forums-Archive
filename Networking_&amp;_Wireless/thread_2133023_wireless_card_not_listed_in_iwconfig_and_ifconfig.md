---
title: "wireless card not listed in iwconfig and ifconfig"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by jordanloveslinux on 2013-04-06
I recently installed ubuntu linux on my old compaq presario r4000 and the wirless driver is not listed in iw/ifconfig.When I had Windows installed the wirless worked fine.How do I fix this?Thanks in advanced!

---

### Post by Azrayal on 2013-04-06
There might be a newer way of doing this but your laptop has I believe a broadcom adapter, as a result you will have to install  ndis wrapper [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)  and following that you can install the correct driver.

---

### Post by wildmanne39 on 2013-04-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.

[COLOR="#FF0000"]Ndiswrpper is almost never needed anymore and should be left as the last resort.[/COLOR]
Thanks

---

### Post by jordanloveslinux on 2013-04-08
Great but what driver do I install?

---

### Post by wildmanne39 on 2013-04-08
We do not know until you post what I asked for.
Thanks

---

