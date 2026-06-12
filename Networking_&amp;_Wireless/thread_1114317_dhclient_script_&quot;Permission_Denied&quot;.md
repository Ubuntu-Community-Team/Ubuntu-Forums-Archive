---
title: "dhclient script &quot;Permission Denied&quot;"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by Monster_user on 2009-04-02
I've run into a little issue. I just upgraded from Intrepid Ibex, to Jaunty Jackalope, and now I can't get an IP address.

After running a few commands in the terminal, it says (network is down). It also says gives me a permission denied error for dhclient-script.

Where can I find the dhclient scripts, and what are the permission supposed to be?

Also, for a few brief moments the adapter will accept commands from "iwconfig", including the ESSID, and WEP key. Then it just forgets them, and refuses any other attempt. Yet the KDE Network Manager still detects the wireless router.

I'm running,...

Kubuntu 9.04 Beta - Jaunty Jackalope
A TrendNET 424UB USB wireless adapter
Ndiswrapper

---

### Post by binbash on 2009-04-02
I have same error!DHCP does not work on wireless but does on ethernet.

---

### Post by Monster_user on 2009-04-02
I just read on the Kubuntu forums, that it is an issue with the Kernel not being updated in Grub.

Open a terminal

Alt-F2 -> xterm

Then type

```
uname -r
```

Make sure it is 2.6.28 or later.

Once I updated Lilo (or GRUB in your case), the networking began to work.

---

### Post by binbash on 2009-04-02
2.6.28-11-generic

I am updating grub but i don't think it will solve my problem

---

### Post by Monster_user on 2009-04-02
It sounds like a different issue then. Perhaps you should create your own thread, with the information on your system.

The make and model of your Wireless adapter, or Laptop/motherboard if it is built-in.

Whether or not you are running NDISwrapper.

The output of 

"sudo iwconfig"

and 

"sudo ifconfig".

---

### Post by superprash2003 on 2009-04-03
i've faced a similar error, restarting networking helped.. type **sudo /etc/init.d/networking restart**

---

### Post by Monster_user on 2009-04-04
I seem to be experiencing another issue. I have to have the KWallet open on KDE, for the network to connect.

---

