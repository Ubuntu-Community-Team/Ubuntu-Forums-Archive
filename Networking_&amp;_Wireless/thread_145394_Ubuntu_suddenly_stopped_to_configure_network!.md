---
title: "Ubuntu suddenly stopped to configure network!"
date: 2006-03-16
forum: Networking &amp; Wireless
---

### Post by dtygel on 2006-03-16
Hi all,

   I've been using Ubuntu for almost a year, without any problems with networking: during the boot process, the steps "configuring network" and "waiting for network do tome up" worked without problems (sometimes it took quite a while for the "waiting for network to come up". Now, after this last kernel upgrade which happened yesterday, network simply doesn't get configured automatically anymore.

   In XP the network works seemlessly, nothing changed. Here is my ipconfig /all result (only the eth0 part):

Connection specific DNS suffix: linkexpress.com.br 
Description: Realtek RTL8139 Family PCI Fast Ethernet NIC #2
Physical Address: 00-08-54-17-55-c8
Activated DHCP: yes
Automatic configuration activated: yes
IP Adress: 200.196.104.223
Sub-net mask: 255.255.255.0
Default gateway: 200.196.104.1
DHCP Server: 200.196.99.20
DNS Servers: 200.196.99.2
                  200.196.99.34
                  200.196.99.3

   When I do ifconfig -a in Ubuntu, I get the same physical address, but haven't copied the other infos. There is only a eth0 infos and a lo infos. How can I copy those infos?

   Do you have any clue of what's going on? How can I debug and solve the problem?

     Thank you,

             daniel tygel

---

### Post by fabiodasoghe on 2006-04-02
Hi all.

I have dxactly same problem: I've just updated to kernel 2.6.12-10.30 (my previuos one was 2.6.12-10.28) and the first new reboot the network stopped working (very long time at the "waiting for network to come up" step).
The odd thing is that issuing the command "lspci" it lists all devices as unknown, which i don't think was correct.

I'm digging into the forum searching for any help, but today I was not lucky. Any help or hint would be very appreciated, thanks.

Fabio

---

### Post by jamesr on 2006-04-02
> When I do ifconfig -a in Ubuntu, I get the same physical address, but haven't copied the other infos. There is only a eth0 infos and a lo infos. How can I copy those infos?

There are are at least two ways ```
sudo ifconfig -a > file
```and the file contains the output or 
if you Gnome running you should be able to copy and paste from the terminal window to a text file. I have used both when first setting the KDE system up and now with a server that is console only so I transfer to a another system for internet access.

---

