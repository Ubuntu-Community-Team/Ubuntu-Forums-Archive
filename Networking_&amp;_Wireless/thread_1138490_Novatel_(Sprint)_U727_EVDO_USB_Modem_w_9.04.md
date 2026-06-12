---
title: "Novatel (Sprint) U727 EVDO USB Modem w/ 9.04"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by briguynyc on 2009-04-26
I've just installed Ubuntu 9.04 on my laptop... and am now trying to bring up my USB EVDO modem...  I have the U727 from Sprint/Novatel.

In looking online, there appears to be multiple ways of setting this up, however I have not been able to find a method that works -- or it appears that certain kernel module changes have occured between 8.10 and 9.04.

Is there a new method for this with 9.04?  Should I be using airprime, and if so, does this still need to be compiled seperately?

Thanks...

---

### Post by mwiseley on 2009-05-04
[ Replacing an initial reply posted during the 20 minutes in step 6... retracted. ]

The U727 is working for me in 9.04. Here's what I did:

1. Right click on the Network connection list that appears to the left of the current date at the top of the screen. 
2. Choose Edit Connections...
3. Go to the Mobile Broadband tab.
4. Click Add
5. Give it a name. I called mine "Sprint" and left everything else with defaults. 
6. Wait 20 minutes. This had me really stumped, and then it was just there. Now after rebooting, it shows up right away.
7. Click the Network task bar icon (from step 1) and click the connection you created to connect.

It's interesting to note that I didn't have to do all this when running 9.04 from Wubi - Ubuntu just found it, created a connection for it, and it worked.

UPDATE: I've noticed what caused the 20 minute wait... it was waiting for me to unmount the U727's built-in USB drive. After connecting the U727, go to Places -> Home to open a file system browser. Then look for the USB drive mounted by the device and click the Eject icon next to it to unmount it. In a minute or so, the Mobile Broadband connection shows up. Apparently both of these can't be used by Ubuntu simultaneously.

Matt

---

### Post by mwiseley on 2009-05-06
After using this a bit, I've found Ubuntu's ability to recognize and provide a connect option for the U727 to be very fickle. For example, it gets lost on suspend/resume and requires a reboot. There's a bit of a ritual required:

1. Disconnect the U727.
2. Reboot.
3. Connect the U727.
4. Wait for the volume icon to appear on the desktop. Right click it and choose Eject (Unmount won't do the trick).
5. Then the connection option appears in the Network Manager dropdown menu.

I would hugely appreciate somebody providing some command line tips to perhaps force the Network Manager to load the module for the device and  avoid the need to reboot. Restarting the network and NetworkManager daemons doesn't do anything. Also, if somebody knows a way to tell Ubuntu not to automount this specific drive (something in fstab?) it would save the Eject step.

One additional note: Ubuntu is even more fickle with the U727 when its plugged into a USB hub. I had it working once, but usually I have to plug it directly into my laptop.

Matt

---

### Post by brianmck on 2009-05-21
I have this modem on a laptop and desktop with U9.04. using Bell Mobility in Canada which works the same as Sprint USA. The laptop works fine. To get it working straight away use  "sudo eject /sr1". However the desktop connects but drops off after a minute or so. Seems to be a problem with the extra usb ports and built in hubs. If often locks my usb mouse but not the keyboard (also usb). Unfortunately there is no ps2 mouse port to try. The motherboard is a Asus M3N78 PRO. The logs seem to give no clue as to what's happening. Any help appreciated

Thanks

---

### Post by ulfj on 2009-05-21
what mwiesley said,but I found that I also had to click on the network icon and disable the wireless card or the aircard would disconnect.I'm using a Verizon USB720 it was disconnecting just as your is until I did this.Hope this helps.

---

