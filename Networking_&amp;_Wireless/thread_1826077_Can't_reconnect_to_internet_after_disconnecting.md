---
title: "Can't reconnect to internet after disconnecting"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by madosaentisutou on 2011-08-16
Good day. Here is my problem:
I can reconnect to internet after disconnecting (this happens every 3-4 hours)** only** if I manually poke out and in ethernet cable to network adapter **or** reboot ubuntu.
Even restarting network-manager not helps.
My provider provides internet over pppoe. I have "DSL-connection 1" item in network managers gui menu. And that item disappears after disconnection.

And my second related question:
pppd runs with following arguments: lcp-echo-failure 3 lcp-echo-interval 20
So where can I change this parameters, where is that configuration file?

---

### Post by praseodym on 2011-08-21
Hello,

can you post the following outputs:

```
cat /etc/network/interfaces
lspci -nnk | grep -iA2 net
route -n
cat /etc/resolv.conf
lsmod
ifconfig -a
```

---

### Post by spiky001 on 2011-08-21
I know you tried restart network try
```
sudo ifconfig eth0 down
```
then
```
sudo ifconfig eth0 up
```
"Providing eth0 is your network"

---

### Post by dineshs on 2011-08-23
> Even restarting network-manager not helpsHope you used ```
sudo service network-manager restart
```
> And my second related question:
pppd runs with following arguments: lcp-echo-failure 3 lcp-echo-interval 20
So where can I change this parameters, where is that configuration file? Run ```
gksudo nautilus /etc/NetworkManager/system-connections
```Doubleclick the corresponding file to open it/edit
Please also post what you get for ```
cat /etc/network/interfaces
```

---

### Post by bjbraams on 2011-11-19
I believe that I have a related problem. I am using Ubuntu 11.10 and I have my wireless set up; it connects automatically when I boot up Ubuntu and log in to my account. If I explicitly disconnect then I can easily reconnect; the menu under the wireless icon shows my network (and other nearby wireless networks too) and I just click on it.

My problem is when I leave my computer unattended and it goes into power save mode. After some time it then drops the wireless and now I can't reconnect. Under the wireless icon's menu it doesn't show my network, it doesn't show any wireless networks. The only thing that I know to do then is reboot my machine, which rather defeats the purpose of the power-save standby mode.

To be clear, I don't mind it that the wireless is dropped after some time of inactivity, in power-save mode. I just want to be able to reconnect to it without hassle.

---

