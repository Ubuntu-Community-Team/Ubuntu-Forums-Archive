---
title: "No wireless after clean install"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by user1397 on 2011-05-19
Here is my output of lspci: ```
$ lspci
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller (rev 10)
``` I connected via ethernet just fine, but wireless is crucial for this laptop, and the additional drivers GUI program says nothing (or at least it finds nothing).

Am a bit stuck on what to do, any suggestions?

---

### Post by Charlietje on 2011-05-19
what is the output of

```
ip a
```

---

### Post by user1397 on 2011-05-19
> **Charlietje said:**
> what is the output of

```
ip a
```
here it is: ```
$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000
    link/ether 70:5a:b6:c7:64:2e brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 70:f1:a1:1e:d6:61 brd ff:ff:ff:ff:ff:ff
```

---

### Post by Charlietje on 2011-05-20
The good thing is that you wireless is recognized.

What you can do to activate the wireless card is:

```
ifconfig wlan0 up
```



Now, you wireless should work via the GUI.

---

### Post by user1397 on 2011-05-20
> **Charlietje said:**
> The good thing is that you wireless is recognized.

What you can do to activate the wireless card is:

```
ifconfig wlan0 up
```

Now, you wireless should work via the GUI.
```
$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
$ sudo ifconfig wlan0 up
[sudo] password for user: 
SIOCSIFFLAGS: Operation not possible due to RF-kill
$
```hmm... :(

One thing to note is that pressing the wireless hardware switch on my keyboard does absolutely nothing, although it works in Windows 7.

---

### Post by Charlietje on 2011-05-20
try this:

check if the wifi card is blocked:
```
sudo rfkill list all
```

then try:
```
rfkill unblock wifi
```

and recheck:
```
sudo rfkill list all
```


if everthing is on "no", then:

```
sudo ifconfig wlan0 up
```

---

### Post by user1397 on 2011-05-20
> **Charlietje said:**
> try this:

check if the wifi card is blocked:
```
sudo rfkill list all
```then try:
```
rfkill unblock wifi
```and recheck:
```
sudo rfkill list all
```if everthing is on "no", then:

```
sudo ifconfig wlan0 up
``````
$ sudo rfkill list all
[sudo] password for user: 
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
$ rfkill unblock wifi
Can't open RFKILL control device: Permission denied
$ sudo rfkill unblock wifi
$ sudo rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
```My hardware switch isn't a physical switch like on some keyboards, it's invoked by pressing fn+f2, I don't know if that helps at all.  Thanks for keeping up with me btw

---

### Post by Charlietje on 2011-05-20
try

```
sudo rfkill unblock 0
```

---

### Post by Charlietje on 2011-05-20
also what kind of laptop do you have?

---

### Post by user1397 on 2011-05-20
sudo rfkill unblock 0 didn't work :(  I have a gateway nv59c09u

---

### Post by Charlietje on 2011-05-20
I'm almost out of options.

try this:
```
sudo rm /dev/rfkill
sudo shutdown -r now
```

If this didn't work
try this:

Shut down the machine with the wifi button in the “off” position.
Boot ubuntu, once booted move the wifi button to the "on" position.

---

### Post by user1397 on 2011-05-20
> **Charlietje said:**
> I'm almost out of options.

try this:
```
sudo rm /dev/rfkill
sudo shutdown -r now
```If this didn't work
try this:

Shut down the machine with the wifi button in the “off” position.
Boot ubuntu, once booted move the wifi button to the "on" position.tried both and still no luck :(

i'm going to see if this is kubuntu specific, i'm going to try to install regular ubuntu natty alongside it and see if it works out of the box or with minimal configuration

---

### Post by Charlietje on 2011-05-20
one more thing.

When you shutted down windows... Was the hw button on or off?

---

### Post by user1397 on 2011-05-20
> **Charlietje said:**
> one more thing.

When you shutted down windows... Was the hw button on or off?
I tried booting into windows and turning the hardware switch off, and then booting into kubuntu but still no luck.

but in a weird turn of events, i just installed regular ubuntu and wireless works out of the box...hmm

still not the ideal solution as I wanted kubuntu to work on this lappy, but maybe kde hates me for some reason hehe

---

### Post by cespinal on 2011-05-20
KDE is like that... sometimes lacks on hardware support.... 

I just installed it in my laptop and wireless is not working either. Im abroad right now but I'll just run all the updates vie ethernet when I get home and will see if any drivers are there for me in it... otherwise hello Unity...

---

