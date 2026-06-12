---
title: "Network Manager is broken."
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by BurningSludge on 2010-06-22
[FONT=Comic Sans MS][SIZE=3]After I connected to my printer once successfully, after one reboot, network manager wouldn't recognize my mobile broadband nor my wifi. It simply doesn't list either option. I can still get on the Internet using a USB 760 but I have to have it in before I start the machine for it to work on Ubuntu 10.04. In addition when I do get my Toshiba Satellite on line on Ubuntu 10.04 it doesn't list the USB 760 as being used. It doesn't seem that the hardware went bad. 
[/SIZE][/FONT]

---

### Post by BurningSludge on 2010-06-22
[FONT=Comic Sans MS][SIZE=3]I think 11 hours is long enough to be bumped.[/SIZE][/FONT]

---

### Post by Iowan on 2010-06-22
Did you power down - or did machine sleep/hibernate?  
A few threads (like [this]("http://ubuntuforums.org/showthread.php?t=1505217") one) recommend:>  service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start
Dunno if you need **sudo** with that...
Once/day is generally considered adequate for bumping :)

---

### Post by BurningSludge on 2010-06-23
[FONT=Comic Sans MS][SIZE=3]I think some configurations are waked out. I purged network manager and reinstalled it from one of my live disk and that didn't fix the problem. I also did what you told me to do and one of those things may have got my mobile broadband re detected. Are there any configuration I think some configurations are waked out. My printer's Wifi hasn't shown up[/SIZE][/FONT][FONT=Arial Black][SIZE=3] [FONT=Comic Sans MS](haven't seen the wifi panel). My hardware is still being detected.[/FONT][/SIZE]
[/FONT]

---

