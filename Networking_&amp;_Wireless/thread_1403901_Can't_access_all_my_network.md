---
title: "Can't access all my network"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by asharpham on 2010-02-10
I have a successfuly operating network at home which includes a laptop, a wireless modem/router, a printer and an ATA for voip telephony. All works wonderfully well but I am unable to access the ATA or the laptop by entering their respective IP addresses.

Now obviously I don't need to access the laptop this way (although it is odd that I can't) but I do need to access the ATA in order to change a setting.

I've tried accessing in wireless mode and hooked up by LAN cable but neither works. As I said, everything is operating fine, but I should be able to access all items on the network via their IP addresses. I have no problem accessing the wireless modem/router this way or the printer. But not the other 2 items.

Any ideas would be greatly appreciated

Alan.

---

### Post by Iowan on 2010-02-10
Access how - **ping**, FTP, SSH, HTTP?

---

### Post by asharpham on 2010-03-05
I've been entering the IP address into the Firefox address bar and I just get the "Unable to Connect" error. This is either in Ubuntu or Windows. I can enter my own computer's IP address as well and it gives me the same error message. However, if I enter the modem/router's IP address or the printer's, I can reach both of those.

In Windows I use the command prompt to ping. To do that in Ubuntu, do i use the Terminal?

Alan.

---

### Post by Iowan on 2010-03-05
> **asharpham said:**
> In Windows I use the command prompt to ping. To do that in Ubuntu, do i use the Terminal? That's the easiest way for me... System>Administration>Network Tools also has a GUI'd Ping. 
It's likely that the modem/router and printer have http-enabled setup pages. Your computer generally doesn't (unless you install Apache or something similar)... I'm not familiar with VOIP, so I'm not sure if the ATA would or not.

---

### Post by asharpham on 2010-03-05
I used to be able to reach all my hardware in Windows but that stopped working a long time ago - long before I started using Ubuntu. So it's not an Ubuntu problem specifically. Even when I hook up directly to my ATA (I currently use wireless) it doesn't work. I guess it's back to the drawing board.

Alan

---

