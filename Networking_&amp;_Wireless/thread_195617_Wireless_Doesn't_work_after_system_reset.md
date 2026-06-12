---
title: "Wireless Doesn't work after system reset"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by BlueSS57 on 2006-06-13
G'day fellow Ubuntu users,

I've been playing around the Ubuntu since last week, i actually started using Mepis (I'm a Windows/Dos guy from way back - first time Linux), anyway i couldnt get the wireless working with Mepis and after searching around on google for a bit found ubuntu and thought i would give it a shot... glade i did, so far liking it a heep better than Mepis... and Winblowz

To the point... I have a Belkin F5D7000AU Wireless G Network Card in my desktop PC, the one with the Rt2500 setup.. i couldn't get it to work with Ubuntu straight out the box so after hours of stuffing around managed to get the thing setup and running using ndiswrapper (thanks for the guys on here, it was info from other posts that got me up and running).

I thought all was ok, however everytime i shut the system down and then reboot the damn thing won't connect. In order to get it connected i have to go into a terminal window and do the following:

#sudo iwconfig ra0 mode Managed
#sudo iwconfig ra0 essid Home (network name)
#sudo ifconfig ra0 up
#sudo dhclient ra0

(Note: Router is a Netgear DG834G, currently using MAC address filtering, did have WEP on aswell but switched it off as i thought it may have been the issue but wasn't).

As soon as thats done, get a new IP from DHCP and all connected and up and running... until i shut down, then have to repeat the process again.

Anyone got any ideas on how to fix this one?

Thanks in advance..

Trent.

---

### Post by BlueSS57 on 2006-06-14
Well i seemed to have fixed the problem, not sure how but its now working each time i switch on the PC.

---

