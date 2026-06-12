---
title: "ACX 111 wireless chipset still not working"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by AirborneDude on 2006-02-28
I followed the instructions on this link [http://acx100.sourceforge.net/wiki/Firmware](http://acx100.sourceforge.net/wiki/Firmware)

it didn't work however.  Do I need to install the files some how? 

I have a ACX 111 Chipset.  Can someone help me?

I download the firmware, renamed the files, copy the files into /lib/hotplug/firmware/   and rebooted the machine, tried messing with the network configuration gui and still nothing.

PLEASE HELP???

Thanks...

---

### Post by Jova on 2006-02-28
You do not have to install firmware... ubuntu have it in /lib/modules/..... oh! Not saim place as in acx100 driver README :).

Don't use System->Administration-Networking.. doesn't work for acx111 instead edit  /etc/network/interfaces and add

iface wlan0 inet dhcp
wireless_mode managed #working mode
wireless_essid B1KBCnet # essid (sid) of your network
wireless_nick RS101 #How you like to other se you :)
wireless_rate auto #Transfer rate auto,  1M...11M etc
wireless_txpower 10 #Txpower in dBm

After that try
# iwlist scan 
to see what networks you can see

---

### Post by AirborneDude on 2006-03-01
I will try it, thanks for your help.  I will post again if I have problem or if I get it working.

Thanks again.

---

### Post by AirborneDude on 2006-03-01
JOVA, SHOULD I ADDED THE FIRMWARE TO THE /lib/modules/ ???  The link said /lib/hotplugs/firmware...

????

Just wondering...

---

### Post by AirborneDude on 2006-03-01
That didn't work.

And when I went to scan it said,

lo  interface doesn't support scanning

---

### Post by gannic on 2006-08-05
This worked for me...

[http://www.ubuntuforums.org/showthread.php?p=1342453#post1342453](http://www.ubuntuforums.org/showthread.php?p=1342453#post1342453)

---

