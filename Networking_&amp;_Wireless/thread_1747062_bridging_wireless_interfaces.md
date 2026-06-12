---
title: "bridging wireless interfaces"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by lizzard8 on 2011-05-02
Hello people!
Im trying to create a network bridge between a wireless pci interface and the two integrated wired interfaces on the motherboard in ubuntu-server.
 
This proved to be a lot harder than i thought it would be (or perhaps impossible?). 
 
After installing ubuntu i have eth0, eth1 and wlan0.
I used iwconfig to set up the wireless settings on wlan0 and i can connect to my acces point fine with wlan0 in managed mode.
 
The problem starts with when i try adding wlan0 to a network bridge.
brctl addif br0 wlan0
can't add wlan0 to bridge br0: Operation not supported
Adding any of the other interfaces to a bridge works fine.
 
Anyway i figured after some reading that wireless interfaces cannot be bridged in ubuntu for some reason unkown to me. So i tried get around that by installing Madwifi drivers for atheros wifi cards so i could create a wireless network interface that appear as a normal one in the system. 
 
So i tried:
wlanconfig ath0 create wlandev wlan0 wlanmode sta
And i got:
wlanconfig: ioctl: Operation not supported
 
In windows this is supereasy and works like a charm. So i dont really understand why this isnt possible in ubuntu.
My question would be how am i gonna go about creating a bridge involving one wireless interface?
 
Ive tried this on both:
ubuntu-10.10-server-amd64
ubuntu-11.04-server-amd64
same results.

---

### Post by selfstranger on 2012-01-03
Hello!

I have the same problem (Kubuntu 11.10):
```

~$ sudo brctl addif br0 wlan0
can't add wlan0 to bridge br0: Operation not supported

```

I've explored the web searching for solutions but there are a lot of questions and a lack of answers. The problem seems to be quite old, common for ubuntu, fedora and arch distributions (according to the survey) and it's notable that it has no good solution.

I've tried this [advice]("http://ubuntuforums.org/showpost.php?p=10470463&postcount=4"):
```

sudo iw dev wlan1 set 4addr on

```
applied it to my wlan0 interface and got the message of right using this command :confused: - it means that it's not right. Now i'm trying to figure out how to fix it.

If somebody has managed with this problem, please help!

Thanks in advance

---

### Post by selfstranger on 2012-01-03
It's notable that there is no problem with interfaces of other types: eth0, tap0, etc. - every can be added to the created bridge. Except wlan

---

### Post by Marogian on 2012-02-11
I have this exact problem right now- has anyone found a solution to this?

Thanks...

---

### Post by Cheesehead on 2012-02-11
Your solution may differ.

In my case, the wireless driver required the 'hostapd' package to function usefully in Master mode. And, unfortunately, hostapd requires a bit of finesse when creating/destroying bridges.

This is my /etc/network/interfaces:```


# The ethernet jack and wi-fi antenna
# in bridged server mode
iface eth0 inet manual
iface wlan0 inet manual

     # Brings up mon.wlan0 upon 'ifup wlan0'
     up hostapd -B /etc/hostapd/hostapd.conf

     # Brings down mon.wlan0 upon 'ifdown wlan0'
     down ifconfig mon.wlan0 down

     # hostapd becomes a zombie when the wlan0 interface closes - kill it.
     down pkill hostapd

auto br0
iface br0 inet static
     bridge_ports wlan0 eth0
     address 192.168.1.12
     broadcast 192.168.1.255
     netmask 255.255.255.0

     # Brings up mon.wlan0 upon startup or 'ifup br0'
     up hostapd -B /etc/hostapd/hostapd.conf

     # Brings down mon.wlan0 upon shutdown of 'ifdown br0'
     down ifconfig mon.wlan0 down

     # hostapd becomes a zombie when the interface closes - kill it.
     down pkill hostapd

```

Again, your similar symptoms may be casued by an entirely different problem.

---

