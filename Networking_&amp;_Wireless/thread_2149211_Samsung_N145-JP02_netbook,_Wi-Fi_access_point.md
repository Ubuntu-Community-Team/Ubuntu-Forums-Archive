---
title: "Samsung N145-JP02 netbook, Wi-Fi access point"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by horonitel on 2013-05-28
[B]Preamble:
[/B]Hello everyone. This is my first post here. 
I'm ashamed, because I'm unable to solve the problem by myself (google always solved 99,9% of my problems), and I ask for your help.

[B]Hardware:
[/B]1) Samsung N145-JP02 netbook
2) Huawei E398 3G modem (works perfectly with network-manager)
3) Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01) (it can work as AP, I managed to do this on Win7).

[B]Attempts:
[/B]I tried to create an access point via network-manager, no success.
I installed wifi-hostapd-ap from ppa. It starts with no problem, but when I click the button which should turn on access point, it fails with segfault.

**Solutions?**
Possibly I can manage to create AP from console, but seems like network-manager needs to be completely disabled for it, but I want to keep it. Also I want to make AP started and stopped easily, in 1 click.

Any ideas how to solve my problem?

---

### Post by scbingham on 2013-05-28
I've been exploring this subject, unfortunately I need a new PCIe controller that can act as an AP. :(

This article looks useful:
[http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/](http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/)

Please post any results/findings.

---

### Post by horonitel on 2013-05-28
> **scbingham said:**
> I've been exploring this subject, unfortunately I need a new PCIe controller that can act as an AP. :(

This article looks useful:
[http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/](http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/)

Please post any results/findings.

Thank you for your reply.
I did everything by this guide, now i'm stuck with running hostapd with little test config. "service hostapd start" gives me the following output:
> ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported


I'm lucky to have absolutely the same wifi card as described in this article. But still no AP :(
I thought it might be kernel problem, so I booted to 3.9.3-pf kernel instead of generic kernel, but it changed nothing.

---

### Post by scbingham on 2013-05-28
I've just bought an AR5B95 which is supposed to be the same as AR9285, so should be able to try at the w/e if it arrives.

In the guide, he is using the ath9k driver, I wonder if that's your problem?

Not sure if much of this will help but...

If you run sudo lshw, under *-network, what is listed next to capabilities?

If you run iw list, under *-network, next to configuration, your driver should be listed.

He does mention replacing ath9k with your driver.

---

### Post by horonitel on 2013-05-28
My bad,  I forgot to specify correct config file for hostapd.
Now I did all by the guide, it works great and I'm able to connect my LG P705 to netbook AP!
I used dnsmasq as DHCP server, this variant is described here: [http://nims11.wordpress.com/2013/05/22/using-hostapd-with-dnsmasq-to-create-virtual-wifi-access-point-in-linux/](http://nims11.wordpress.com/2013/05/22/using-hostapd-with-dnsmasq-to-create-virtual-wifi-access-point-in-linux/)
Thank you very much for your replies, my problem is solved :)

I've read this thread - [http://ubuntuforums.org/showthread.php?t=954716](http://ubuntuforums.org/showthread.php?t=954716)
I still can't understand how do I mark thread as solved. I do not see such an option in thread tools menu. Any ideas?

---

### Post by scbingham on 2013-05-28
:D Glad I could help. I'm looking forward to trying it.

Yes, his dnsmasq article is linked to the hostapd article.

Unfortunately I don't know how to mark as solved. I thought it was under 'thread tools'

---

### Post by wildmanne39 on 2013-05-28
Hi, this link will tell you how to mark the thread solved!
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by horonitel on 2013-05-29
Thank you, it worked :)

---

### Post by horonitel on 2013-05-29
Here comes my own version of hotspot script. After doing everything by the manual, you can try this script to start a hotspot, instead of the original one.
I changed the script so it can check for internet connection. Also it checks if your wireless device is on. And some fancy output :)

I hope it might be useful for someone.
```

#!/bin/bash
#############################
# My custom /usr/sbin/hotspot
# For me and ubuntuforums.org
# Dmitry Horonitel 29.05.2013
#############################


# It"s better to start dnsmasq at the end, let"s disable it for now
service dnsmasq stop > /dev/null 2>&1


# Checking internet connection
echo " * Starting internet connection check..."
if ! [ "`ping -c 1 google.com`" ]
then
echo "Your internet connection / DNS does not work, check it and try again."
exit 1
fi


# Set network parameters
echo " * Starting network configuration..."
ifconfig $1 up 10.0.0.1 netmask 255.255.255.0 > /dev/null 2>&1
if [[ $? -ne 0 ]]
then
echo "Unable to bring up $1, check that the device is enabled and try again."
exit 1
fi


# Wait for 2 seconds...
sleep 2


# Enable NAT
echo " * Starting NAT & port forwarding..."
iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
iptables --table nat --append POSTROUTING --out-interface $2 -j MASQUERADE
iptables --append FORWARD --in-interface $1 -j ACCEPT
sysctl -w net.ipv4.ip_forward=1 > /dev/null 2>&1


# Start hostapd
service hostapd start


# Start DHCP server
service dnsmasq start


echo "Wi-Fi hotspot is on."
read -p "Press enter twice to turn it off..."
read


# Stop hostapd
service hostapd stop


# Stop DHCP server
service dnsmasq stop
exit 0

```

---

### Post by scbingham on 2013-05-29
If I have success with my new wifi card, I'll try your script. Although I might change the check for an internet connection as I want the option to run a hotspot without providing connection to the internet.

---

### Post by horonitel on 2013-05-30
[COLOR=#000000]scbingham, please let me know how does my script work for you, I want to be sure that it's suitable for everyone.[/COLOR]

---

