---
title: "Wired network suddenly doesn't exist"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by stwstl5926 on 2011-11-04
I'm running Ubuntu 10.10 64-bit. About an hour ago, Firefox crashed on me (a YouTube video froze up), and instead of going into the system monitor and killing the process like I should have, I restarted the computer. Now my computer seems to think I don't have an ethernet port at all. I've tried imitating the settings from another computer connected to the same network, but it still simply will not show anything related to a wired connection. I really, REALLY don't want to format and start over, as I just went through that process a month ago, and just now got things the way I like them (yes, a month ago. I refuse to switch to Ubuntu 11, so I dug up my old 10.10 disc). Help?

---

### Post by stwstl5926 on 2011-11-04
Slight update on the issue: when I ran sudo lshw, the only network adapter that showed up was something linked to VirtualBox. Strange, I know. So, logically, I uninstalled VirtualBox, which I never really used anyway. Still no internet, though now my real network adapter is showing up in lshw as it should be. Also, the network manager has found my ethernet port once again. I had deleted it from the list of connections, trying to do it manually. It found it again, but it still won't connect to it. There's not even an option to connect to it from the manager.

---

### Post by pqwoerituytrueiwoq on 2011-11-04
i had a issue with the Ethernet vanishing once reboots did nothing it was a new computer build i thought i was goign to have to get a pci card or rma it i cut the power to it for 5 minutes and then it worked when i powered it on

make sure it networking is enabled (right click icon near the clock)

---

### Post by Kronalias on 2011-11-04
I had this problem of losing ethernet a year or so back. Here's what I wrote up for myself - hope it helps!

-------------------------------------------------------------------

Ubuntu Lucid 10.04 lost eth0 after an upgrade. Do this:

From a terminal open interfaces file
sudo gedit /etc/network/interfaces
 
add the following two lines if missing (they were):
auto eth0
iface eth0 inet dhcp
 
restart networking:
 sudo /etc/init.d/networking restart

Find out what ip you are:
ifconfig

From a remote PC go to a terminal and type:
ping 192.168.1.6 (or whatever ip you found)

That should prove that you can at least ping the PC.

If that's ok then continue. If not then try something else.

NetworkManager is the network icon in the Gnome top bar.
It didn't have any active network connections (although the network was up)
Tap on it - I saw Wired Network, and a line under it saying 'device not managed'

Edit /etc/NetworkManager/nm-system-settings.conf
and change:
[ifupdown]
managed=false
to:
[ifupdown]
managed=true

Reboot and hopefully ethernet is up and available.

---

### Post by stwstl5926 on 2011-11-04
> **pqwoerituytrueiwoq said:**
> i had a issue with the Ethernet vanishing once reboots did nothing it was a new computer build i thought i was goign to have to get a pci card or rma it i cut the power to it for 5 minutes and then it worked when i powered it on

make sure it networking is enabled (right click icon near the clock)

Yes, networking is enabled. This is a much more advanced problem than "Make sure it's turned on."

---

### Post by stwstl5926 on 2011-11-04
Thanks for trying, Kronalias, but my problem appears to be different, because that didn't work. In the interests of "I need a working computer by tomorrow," I'm just going to have to format and deal with it. *sigh* I love Ubuntu and all, but when it crashes on me, it sure knows how to crash.

---

### Post by praseodym on 2011-11-04
Hi,

what hardware is that?

```
lspci -nnk | grep -iA2 net
ifconfig -a
uname -a
lsmod
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by stwstl5926 on 2011-11-04
> **praseodym said:**
> Hi,

what hardware is that?

```
lspci -nnk | grep -iA2 net
ifconfig -a
uname -a
lsmod
cat /etc/udev/rules.d/70-persistent-net.rules
```

It's a Realtek something or other, but it doesn't really matter, because I've discovered that the port itself is basically dead. The computer sees that it exists, but the indicator lights show nothing no matter what's going on.

---

### Post by praseodym on 2011-11-04
Please show the output of the first line, if it is a Realtek 8168B you need to install a better driver.

---

### Post by stwstl5926 on 2011-11-10
> **praseodym said:**
> Please show the output of the first line, if it is a Realtek 8168B you need to install a better driver.

That would make sense, except that it's been working for several months now on that same installation, and booting various live Linux CDs yielded the same result. The port is just dead.

---

