---
title: "No Internet on ieee"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by Ellswj on 2010-07-01
I have an IEEE 900 ha running netbook remix 9.10. I am unable to connect giant type of connection, nothing is even showing up in my network fields. I've tried everything, wired to the router and the modem and wireless. Nothing even shows a connection. This is my first exsposure to Linux, coming from windows. Right now I'm posting from my iPhone, because it's my only source of Internet at the moment. Any help would be greatly appreciated. TIA

---

### Post by Ellswj on 2010-07-01
Anyone?please help I'm dying with no interenet!!!

---

### Post by gareththered on 2010-07-01
Ellswj,

You need to post information and not a plea for help; although posting command outputs will be very difficult from an iPhone!  First of all, run a command that will tell you what network devices Ubuntu thinks you have.  Type the following at a terminal:-> ip addrYou should see an entry for 'eth0' for the wired (or maybe 'eth1'). If your cable is connected you should see the word CARRIER in the line and hopefully UP.  Also, check that the LED on the router lights up when you plug in the cable.  If the cable is not connected correctly, then you will see NO-CARRIER in the output above.  If you don't have the word UP, then try> sudo ifconfig eth0 up(Substitute 'eth1' or whatever your ethernet port is.)You will need to enter your password.

If you get the wired working first, then you will have Internet access with which to Google and read Ubuntu forums to fix your wireless!

Good luck!

Gareth

---

### Post by Ellswj on 2010-07-01
When I put in th ip addr it gives me this-        1;   lo: <LOOPBACK, UP, LOWER_UP> mtu 16436 qdisc noque state UKNOWN     inet 127.0.0.1/8 scope host lo inet 6: :1/128 scope host.           Valid_lft forever preferred_lft forever.  Then when I put the Sudo ifconfig eth0 up. It says error while getting interface flags: no such device. I've tried different routers and cables that all work when connected to my xbox but nothing seems to work

---

### Post by gareththered on 2010-07-01
Hi,

From your results, it seems that no network device has been picked up other than the loopback device 'lo'.

Try> lspcior> lshw -short and check if you see an ethernet device in there.

Regards,

Gareth

---

### Post by Ellswj on 2010-07-05
If it doesn't show a NIC, what is the next step? I am very new to linux and unsure what to do

---

### Post by gareththered on 2010-07-06
Hi,

Is there a switch/button to enable wireless/ethernet?  Is there an option in the BIOS to enable/disable them?

Type 'lspci' at a terminal and look for Network Controller or Ethernet Controller.  If nothing is found, double check switches/BIOS settings.

Regards,

Gareth

---

