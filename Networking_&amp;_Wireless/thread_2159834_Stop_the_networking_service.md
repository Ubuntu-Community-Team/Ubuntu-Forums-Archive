---
title: "Stop the networking service"
date: 2013-07-04
forum: Networking &amp; Wireless
---

### Post by TheOnlyChosenOne on 2013-07-04
Hi

I'm working on a script that can stop all internet traffic. What I did was stopping the eth0 and wlan0 interface. The problem is that Ubuntu tries to restore these interfaces automatically. So, I want to stop the entire networking interface. But when I try
```
sudo service networking stop
```
I get this
```
stop: Unknown instance:
```
error, while
```
sudo service lightdm stop
```
works.

How can I stop the networking service properly?

Thanks.

---

### Post by sanderj on 2013-07-04
Which Ubuntu version? Check with:

```
lsb_release -a
```

What is the output of

```
sudo /etc/init.d/networking stop
```

---

### Post by TheOnlyChosenOne on 2013-07-05
```
lsb_release -a
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

```
sudo /etc/init.d/networking stop
```
There is no output. It just crashes gnome 3. (And yes, there is no internet connection.)

Edit: Apparently, this is a [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1072518"). Bringing down the network-manager service also does the job.
```
sudo service network-manager stop
```

---

