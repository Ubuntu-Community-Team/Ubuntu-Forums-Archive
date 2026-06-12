---
title: "how do i wireles ssh..."
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by zander1013 on 2009-02-16
hi,

how do i wireless ssh between to laptops with ubuntu 8.10 wifi that works without having a wlan router?

i am thinking some kind of ad-hoc network but i don't know.

i can wireless ssh now but i need a wlan with a router to connect. i want to connect the machines completely wireless without a switch or hub.

please advise.

zander

---

### Post by dzark on 2009-02-16
Open up (with sudo) you /etc/network/interfaces (remember to backup first!)

and change ```
auto wlan0
iface wlan0 inet dhcp
```

to

```
auto wlan0
iface wlan0 inet static
         wireless-key 1234567890
         wireless-channel 6
         wireless-mode ad-hoc
         wireless-essid 'Wireless Connection'
         address 192.168.0.2
         gateway 192.168.0.1
         netmask 255.255.255.0

```


remembering to use the correct name for your wireless interface, which you can get with ```
iwconfig
```

and then finally restart networking

```
sudo /etc/init.d/networking restart
```


See also:
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

---

### Post by zander1013 on 2009-02-16
cool outrageous!

it looks like will i still be able to auto wireless dhcp addresses from a wlan
and i guess i do this for every machine too yes?

thank you,

zander

---

### Post by dzark on 2009-02-17
change the 'static' to 'dhcp' and remove the 'address', 'gateway' and 'netmask' :)

but... have found it to be more of a hassle than it's worth as it doesn't always play nice...

---

### Post by zander1013 on 2009-02-17
okay,

we will give it a try! i am doing this to setup a cluster using the hadoop framework on some old laptops that i have. hadoop uses ssh to pass data.

the laptops have 3g broadband modems onboard. i plan to get a broadband account for the head node so that will be the primary means of reaching the web. with the wifi cards used only to pass data and jobs between the nodes (eventually).

will there be any issues with broadband and the wifi prescription you have given?


thank you, thank you again!:popcorn:

zander

---

### Post by dzark on 2009-02-17
Just refer to [https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless) and you should be fine

---

