---
title: "Wifi Not Working / Slow, Tried Fixing, Reading"
date: 2012-10-25
forum: Networking &amp; Wireless
---

### Post by Lereh on 2012-10-25
Using Ubuntu 12.10
Realtek RTL8187 Wireless 802.11b/g 54Mbps USB 2.0 Network Adapter

Mostly my internet won't connect now.  For a while (before I started trying to fix it), it would connect, but the pages would barely load (mostly not load... sometimes at first, it would load a full page, sometimes even two, but then would load like a title, very rarely, but mostly nothing at all).

Now, though, it can't connect to the network at all.  It tries.  It can see all the wireless networks in the area.  Won't connect.

I don't have the problem using the same card on other machines.

Thanks, in advance.

I've been reading a lot, and trying to fix this.  I've kept track of what I've done so far.  But before I say what I've done, I'll list what questions I have (and if they're not relevant / won't work anyway, feel free to say so).


Questions:

1) Someone says to make sure you've installed all updates (Can't do this because can't connect to net).  Is it possible to install updates from USB (Load updates from another machine onto a flash drive, and then load the updates onto the machine with Ubuntu)?

2)  Someone said, "then in the DNS servers field: type the IP Address of your wireless router or default gateway. Mine was 192.168.0.1 for example."

-- How do I find out the IP Address?

3) Someone says, "I changed my DNS sever to 8.8.8.8, 8.8.4.4. I also switched back to dynamic ip. This seems to have fixed the problem."  

-- How do I change my DNS server?



What I've done already (note that I am quoting, excerpting what I've read, and was able to do):

1) "sudo pico /etc/pm/power.d/wireless

The above command opens the wireless file for editing as a root user.

In this file add the following lines and save the file and exit. That’s it.

#!/bin/sh

/sbin/iwconfig wlan0 power off"


2) "sudo gedit  /etc/nsswitch.conf

This will open the nsswitch.conf file in the text editor. Then simply change the following line

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

to the below line and save the file.

hosts:          files dns"


3) "Type the following in a terminal: lsmod | grep ipv6. If you see anything mentioning IPv6, then you have it enabled. [I saw nothing...] If not then you can proceed with the next issue mentioned.


Disable IPv6 - ...

Edit the file sudo nano /etc/default/grub and find the line that says GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and add to it ipv6.disable=1.
 It should look like this afterwards: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1". Save it and type sudo update-grub. After this reboot the PC."


4) "In some cases it may be some misconfiguration gone wild. Try this:

1.1 - Type ifconfig and look for the txqueuelen option. Normally it says 1000. Lower it to 500, 200, 100 or 50 just to test if it gets better: sudo ifconfig eth0 txqueuelen 50."


5) "If you ran a packet capture while you browse slow website, you should see AAAA DNS queries that never answer and hang.

One thing in Firefox is the ocsp feature. When you browse a SSL website it will start to query the ocsp. The problem is ocsp is not ipv6 yet... at least not in the options configure by default in firefox.

So to prove that and see if it's your issue, you can go to tools -> options -> Advanced -> encryption (tab), then click on validation button and uncheck 'use the...'"  

(although it was edit -> preferences -> advanced -> etc..., not tools -> options..)


6) I could keep going, and I s'pose I will, but thought I'd start a forum thread at this point.  =)

---

