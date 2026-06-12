---
title: "Networking and Internet connection sharing using a USB mobile (Cellular) bband modem"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by Neill_R on 2009-10-06
This is a request for guidance. I am new to Linux.
 
 Internet -> Option ICON 225 -> HP 5271 Pavillon Laptop =>DLink 660 PCMCIA Card. =>LinkSys Wrk54G  
                                                          (FireStarter with ICS)                                                      WAN Accessport
 
 Once connected the network is stable.
 
 The problem is at boot up. When  the PC is shutdown (requires manual Power Off). The PC will not then reboot with the Network as shown above running correctly. The eth0 connection connects but not the hso0 connection. 
 
 Sometimes a simple 
 
 [COLOR=#ff0000]sudo /etc/init.d/NetworkManager force-reload [/COLOR]
 
 will restart the network but on other occasion as today the USB Dongle has to be [COLOR=#ff0000]unplugged[/COLOR] first. Usually once replugged and the USB stack has reconfigured then connection can be obtained.
 
 Visible notification from the NetworkManger in terms of what is seen on the Taskbar are;
 
[LIST]
[*]Twin stacked PCs
[*]Twin stacked PCs with red X
[*]Twin Grey Dots and stationary "Spinning Comet"
[*]Twin Grey Dots and "Spinning Comet"
[/LIST]
      Either
   [INDENT]   [INDENT]     
[LIST]
[*]Twin Dots one green and  "Spinning Comet"
[*]Twin Green Dots and  "Spinning Comet"
[*]Radio Tower (success)
[/LIST]
   [/INDENT] [/INDENT]        or 
 [INDENT]   [INDENT]     
[LIST]
[*]Twin stacked PCs (failure)
[/LIST]
   [/INDENT] [/INDENT]  
 Why is this important it is simple to fix as stated above, well I am planning on replacing my gateway PC with a Linksys NSLU2 ([http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)) device and would really just like it to work without having to connect to the NSLU2.

 If once connected, I then reboot the PC (No hard power off), it does so and the Windows PC have access to the Internet. I do not have to log in to the Xubuntu 9.04 PC which is of course what I want. I do not however to intent to or wish my gateway to be powered continuously or indeed continuously connected to the Internet.

I hope this adequately describes my problem.

[COLOR=#ff0000]Is there some command I can place in my gateway PC's startup script that will perform the same as unplugging the ICON 225?[/COLOR]

---

### Post by Neill_R on 2009-10-07
I find that if I power off and then unplug the USB modem when I restart the Network works. leads me to beleive this is a shutdown/USB issue

---

### Post by Neill_R on 2009-10-14
Update.

This Morning I switched on and login in but the NetworkMmanager refused to make the mobile broadband connection. I tried force reload, unpluging the USB modem, stop then start and repeatedly  force reload to no avail. I was about to reboot into Windows XP when I gave xubuntu another go and it worked The PC had connected to my ISP without any intervention on my part.

Can anyone suggest what is going on? 

I know there is a chance that my ISP network was not working and in the time it took to reboot was fixed but how likely is that.

---

### Post by Bucky Ball on 2009-10-14
Don't boot with the USB dongle plugged in. That can cause problems. Maybe unmounting and removing before shutdown would also help.

---

### Post by Neill_R on 2009-10-14
But I have done exactly that rebooted USB dongle connected and it has worked.  I will repeat this several times and see if it works every time.

---

### Post by Neill_R on 2009-10-14
I have just completed 3 complete reboots of my laptop and Each time the connection has been made successfully. With This laptop if I shutdown I have to physically switch it off. I have seen that then unplugging the USB dongle before restarting resulted in a successful connection also a force-reload will sometimes do it too but not always.

Any ideas please ?

---

### Post by Neill_R on 2009-10-14
switched on tonight and all was fine. I had unplugged the modem after switching off
Why is it not always this way

---

