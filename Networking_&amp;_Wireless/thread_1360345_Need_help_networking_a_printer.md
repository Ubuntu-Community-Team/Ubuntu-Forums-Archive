---
title: "Need help networking a printer"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by axelhdz2k3 on 2009-12-20
Hello,

My HP printer is connected to my desktop (9.10) and I am trying to figure out how to print from my Laptop (Windows 7). 
The desktop is connected to a Linksys router and the laptop is connected wirelessly to the router. I have been searching all over but the information out there is way too convoluted for me.

Thanks in advance

---

### Post by Bucky Ball on 2009-12-20
What HP printer do you have and is it possible to network that, ie: plug the printer into the router also? This will give it an IP address and then you can connect from any other machine plugged into the router.

---

### Post by axelhdz2k3 on 2009-12-21
Thanks for the reply. I have a 4315 HP and I cannot connect it to the router. It is a usb and the router does not have a USB connection.

---

### Post by Bucky Ball on 2009-12-21
Yep, looks like you can set up a cups server if both computers are on the same network. I am not on a ubuntu but an xubuntu box but I think it is System->Admin or Preferences/printing. 

I am assuming the printer is working ok on machine 1. First tweak the 'Server Settings' on the host box (machine 1). 

Attached is the setup on my client box (machine 2) but my router has a built in printer server so the IP is the router's.

First add a printer then setup like this; I'm assuming you would simply change the part I have highlighted to be the IP of the computer serving the printer (machine 1) so you need to find out what that is. Don't change anything else. 

I also assume there is something at least vaguely similar in 9.10 you can nut out as this is from 8.04 LTS Xubuntu box!

** _Note Well_: The only problem with this setup is your IPs will be changing constantly and therefore you will lose the printer whenever you reboot the CUPS server. A perfect situation for static IPs within the home network. This also makes it a LOT easier to keep track of things when you are setting up file sharing (although Samba handles names ok but I don't like it!). 

Good luck and hope this works for you or gets you a bit closer.

---

### Post by axelhdz2k3 on 2009-12-21
Thanks for the help. I'll try this and will post the results.

---

