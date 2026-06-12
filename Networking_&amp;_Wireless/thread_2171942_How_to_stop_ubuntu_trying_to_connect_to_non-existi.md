---
title: "How to stop ubuntu trying to connect to non-existing wifi card after wake-up"
date: 2013-09-02
forum: Networking &amp; Wireless
---

### Post by Juergen_Singer on 2013-09-02
After Ubuntu 13.04 wakes from sleep it tries to connect to the net via WiFi, though there is no WiFi-card in the machine. It stays in this mode until I switch it off. Regular shutdown does not work either, I have to push the power button. The problem is annoying, since my PowerFolder Cloud Software stops synchronizing,
even though both gigabit ethernet ports stay connected (but cannot be disconnected from the menu). This only happens after a wake-up from sleep, not when
booting.

How do I prevent Ubuntu from trying to connect to a non-existing WiFi-card.  ifconfig wlan0 down won't do.

-- Juergen


Machine:  MacPro Spring 2008, CPU: 2 x 4-core Xenon,  64 bit, 8 GB Ram

---

### Post by varunendra on 2013-09-03
Welcome to the forums Juergen !

> **Juergen_Singer said:**
> After Ubuntu 13.04 wakes from sleep it tries to connect to the net via WiFi, though there is no WiFi-card in the machine.

That is weird. Is this a direct installation on the machine or did you migrate an installation to it?
Does Network Manager show any wireless connections in its settings (NM drop-down menu > Edit Connections > Wireless tab)? Delete if there are any. If not, or if it gets re-created, please post back the following outputs -

```
lspci -nnk | grep -iA2 net
lsusb
cat /etc/udev/rules.d/70-persistent-net.rules
ls /etc/pm/sleep.d
ls /usr/lib/pm-utils/sleep.d
```

Also, as soon as the machine comes back from sleep and starts trying to connect, run and post the outputs of -
```
cat /var/log/syslog | egrep -i 'network|wlan' | tail -40
```

---

### Post by Juergen_Singer on 2013-09-05
Here ist the requested information (appended below).

I noticed that eth0 does not come up again. it is directly connected (dhcp) to our computing center, which brings up the line only after a 60 sec delay, but ubuntu stops trying after 45 sec.
eth1 is connected via my local hub with a private IP, so the 60 sec delay does not apply.

---

### Post by varunendra on 2013-09-06
Didn't get any hints about a wireless connection attempt. How do you know it is trying to connect via (non-existent) wifi?

There only thing that looks 'slightly' suspicious is the "50unload_alx" script. It doesn't exist by default but "alx" is an ethernet driver. Nevertheless, you may try to disable it for a test -
```
sudo chmod -x /usr/lib/pm-utils/sleep.d/50unload_alx
```
although I doubt if it'll help.

If, as expected, it doesn't make any difference, please reboot > send it to sleep > wake it up, then post the full copies of dmesg and syslog. To archive them -
```
cd /var/log
tar -cjf ~/Desktop/logs.tar.bz2 syslog dmesg
```
This will create a "logs.tar.bz2" archive file on your desktop whose size will, hopefully, be much less than the forum limit for tar.bz2 attachments. Attach this file in your next post.

It is recommended to check the files in the archives yourself before posting here and delete/obscure lines that may contain potentially sensitive information (for example, MAC addresses).

---

