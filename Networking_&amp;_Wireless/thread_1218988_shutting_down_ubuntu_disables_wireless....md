---
title: "shutting down ubuntu disables wireless..."
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by akimatsu123 on 2009-07-21
hi,

i own a lenovo x200 tablet. i dual boot vista ultimate and ubuntu. i have a very strange problem with my wireless card. 

in its working state in vista, no matter how many times i shutdown/restart, the wireless card continues to work. however, once i boot into ubuntu and then shutdown/reboot, wireless stops working accross both OS's, and even on a LiveCD.

By "stops working" i mean wireless completely disappears. no error messages of any sort, my computer just behaves as if there are absolutely no wireless cards plugged in...which of course there is, because the card is built in. i get no wireless device under device manager in windows, and nothing under iwconfig in linux. 

to reset this problem, i have to take the battery out of my computer. once i take it out and plug it in again, wireless works, until of course, i next shut down ubuntu. 

does anyone have any advice?

thanks

---

### Post by martinbaselier on 2009-07-21
Don't you have a button on your laptop to switch wireless on/off ?

To determine the cause of the problem it would be interesting to know what kind of wireless card you have. 

lspci will show you all the the pci-devices. 

Then use sudo lspci -s **cardnumber** -v to show details about the wireless card. 
replace cardnumber, with the number of your card. 
example : 
```

lspci 
...
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
**06:03.0** Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
06:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
...
sudo lspci -s **06:03.0** -v

```

Use the right mouse button menu to copy from/paste to the terminal.

---

