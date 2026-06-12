---
title: "network angriness..."
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by Turd Flop Down M'leg on 2005-12-16
I just installed ubuntu (Breezy Badger) and while I love everything about it I've been having lots of networking problems (which I'm not sure are due to ubuntu or something else).

1. Hostname wont show up in my router client table (linksys befw1154), just a blank is shown.  Checked all the regular places for hostname (/etc/hostname /etc/hosts/ etc....:ahem:)

2. Samba wont work (probably due to 1.)  Ubuntu can see my windows box and it's shares, but windows cant see ubuntu.

3. Ubuntu pings, netstats, traceroutes as if everything is fine and dandy with around 20~30ms response times, but loads simple webpages (say [www.google.com](www.google.com)) very slowly.  It downloads fine, and once I've sshed into another machine everything runs fine, even when exporting displays.

I've tried shoving ubunto onto different local ip's (192.168.1.101 or 192.168.1.102) but no change.. swapped the cable no change.. dont really want to swap the nic if that isnt issue.. stupid case is hard to open and harder to close. :rolleyes: 

Thanks for any help.

---

### Post by moon2js on 2006-01-05
I have the same problem. My ubuntu machine's hostname doesn't show up on the router's DHCP client tables, only its IP address. Samba doesn't seem to work either.

Anyone have any advice?

---

### Post by Lambert on 2006-01-05
My hostname doesn't show up either but it hasn't caused any problems for me.

Not knowing where you looked for samba help here are some links.
[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

If you have slow internet via browser look at turning off ipv6. This turns it off globally on your system.

[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

---

### Post by Turd Flop Down M'leg on 2006-01-05
well, as for #3, another forum user posted this nugget

[QUOTE=Saiboogu]
Try typing about:config in your Firefox address bar. Type ipv6 in the "Filter:" box, find the option that says "network.dns.disableIPv6". If it reads "False" right click and toggle it to True. Should give you a slight speedup in your browsing.
[/QUOTE]

Turns out it was just a problem with Firefox and IPv6,  thanks Lambert.

But, still cant get samba to work tho (I followed the [https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba) howto when I first set up samba, but it still doesnt work).  Hostname probably doesnt have anything to do with samba not working after all.

Edit:
ah crap.  I hate random fixes.  I toggle a setting firefox and samba starts working too.  I KNOW that's not what really fixed the problem, but I didnt do ANYTHING to my ubuntu box (except leave it off for two weeks).  I suppose I'll be posting again when the problem comes up again.

---

