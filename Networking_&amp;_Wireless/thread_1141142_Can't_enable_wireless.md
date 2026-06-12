---
title: "Can't enable wireless"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by steve1955 on 2009-04-28
I've been dual booting XP and Ubuntu 8.04(LTS now) for 12 months or more on a Medion laptop - with absolutely zero wireless problems, everything worked flawlessly from day one, with the only setting up: adding a WPA key.

A few days ago (I think following an update)My wireless was suddenly disabled and I can't enable it. The wifi is greyed and it's just not possible to check the box. I went through the forums and the troubleshooting official documentation. Tried loads of actions and different advice. I've reformatted and now installed 9.04 and I've still got exactly the same problem.

Yes I do have a wifi button on the laptop - it has no effect  using Ubuntu, I might add everything works in XP including the button both on and off.

The Intel ipw2200 card is recognized, it has a driver attached I've gone through [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide), all seems to be there until I get to 'sometimes the cards recognized everything seems to be working refer to/check forums etc etc' 

Hope someone's been here before - Thanks

---

### Post by xanderp123 on 2009-05-07
I think I am having a similar problem. I recently upgraded my 3-year old Dell laptop and Acer Aspire One netbook to Jaunty and everything seemed to work fine (including the wireless). 

A couple days ago I right clicked on the Network Manage applet and unchecked "enable wireless" on my laptop. (I used to do this a lot to force it to use either the wired or wireless connection when I am connected to both). But, after unchecking the box, the item disappeared from the Network Manager context menu and I can't seem to reenable my wireless!! This has happened on BOTH computers I upgraded to Jaunty!! I have already spent a while searching the net for solutions to this problem, but no one else seems to have reported it yet. I guess the next step is to create a bug report.

---

### Post by xanderp123 on 2009-05-08
Update:

On my Acer Aspire One netbook, I had compiled and installed the madwifi driver for my Atheros card and configured /boot/grub/menu.lst so that the kernel for which I compiled the driver would boot by default. To fix the netbook, I un-blacklisted the ath5k driver in /etc/modules.d/blacklist-ath_pci.conf and rebooted using the latest Jaunty kernel. So far so good.

As for my laptop, the "Enable Wireless" item mysteriously re-appeared in my Network Manager applet context menu today but it was greyed out. After playing with the wireless hardware switch, the item became enabled and I was able to check the box. I'm still puzzled as to why I couldn't get the "Enable Wireless" item to show up in the menu for a good week, but it seems to be working now.

---

