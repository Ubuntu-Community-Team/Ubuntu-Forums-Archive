---
title: "Wireless not working after Breezy -&gt; Dapper upgrade ..."
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by joaocorreia on 2006-06-18
Hello,

I was using Breezy with a compaq wireless card without any problems. I upgraded to Dapper and the wireless card stopped working.

It detects the wifi card but it doesnt get an IP.

I tryed to use another kernel but Ubuntu doesnt boot into X, in command line with another kernel works ok !

Any tips on how to solve this easy ?

Thanks
Joao Correia

---

### Post by deathshadow on 2006-06-18
Sounds like the same problem I had (just on xubuntu)... Card recognized, SSID set properly, even could get a connect...

Is your wireless setup set to WEP shared? If so, this might be your solution

[http://www.ubuntuforums.org/showpost.php?p=1153031&postcount=14](http://www.ubuntuforums.org/showpost.php?p=1153031&postcount=14)

to paraphrase, edit /etc/network/interfaces, and change the line that has your WEP password on it to have the word "restricted" at the END. If you have it in the middle (as a leftover from breezy) remove it.

---

### Post by joplass on 2006-06-18
I have the impression that developers can't seem to make their minds on this wireless issue.  With my initial install ndiswrapper wouldn't work but the system went back to the default driver and he worked until that latest Dapper upgrade.  After the upgrade eth1 disappeared to give way to wlan0 through ndiswrapper that I did not bother to remove.
If you guys were using the default broadcom driver you probably should fall back to ndiswrapper.

---

### Post by deathshadow on 2006-06-18
[QUOTE=joplass] With my initial install ndiswrapper wouldn't work but the system went back to the default driver and he worked until that latest Dapper upgrade.  After the upgrade eth1 disappeared to give way to wlan0 through ndiswrapper that I did not bother to remove.
[/quote]
I think that sounds more like an aspect of something I've found about linux - something that it seems every OS has issues with, even though windows catches the most flack for it... Just because you CAN upgrade, doesn't necessarily mean it's a good idea... You might not have seen your issues on a clean install.

[QUOTE=joplass]
If you guys were using the default broadcom driver you probably should fall back to ndiswrapper.[/QUOTE]

Not Broadcom in my case - I had a Ralink based card, two actually, an RA2500 PCMCIA and a RA2750 USB. Given that RaLink is Linux Emporiums 'product of the year' for linux, and the free software foundation now recommends the RA2500 as the weapon of choice, that niggling little issues like WEP shared has to be hand set REALLY shouldn't continue to be a problem.

Broadcom + Linux = nightmare, as broadcom is not exactly OSS friendly - which is why so many Mac users have issues with linux wireless (given the 'airport/airbus' cards are all broadcom chipset)

---

### Post by joaocorreia on 2006-06-18
I dont use WEP , just simple and plain open AP.

Thanks
Joao Correia

---

### Post by tc10b on 2006-06-24
I think I have a similar problem. I don't use WEP either, it's an open AP

---

### Post by adagio on 2006-06-24
Thanks to deathshadow for that post - my own problem of enabling WEP was fixed after reading the iwconfig manpage.  Passphrases it says are not supported, so instead of using the the System/Admin./Network password option I entered it as straight hex. (copied from the router setting).  Worked fine following that.

:D  <-- happy Ubuntu user

---

