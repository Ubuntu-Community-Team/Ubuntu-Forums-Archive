---
title: "wireless deactivated when rebooting"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by aldegaz on 2006-06-28
Every time I reboot my wireless is not active, so I have to go to system/administration/networking and activate it.

This is a PCMCIA card in a Gateway Laptop, wasnt it doing it before, so I guess I messed up with something, but I just dont know what.

Any help will be appreciated!

---

### Post by Dr. Nick on 2006-06-28
not sure if this will help or not, but its a idea.

Does it also have a wired ethernet card? Sometimes the wired card will take prefrence. open the net control panel and hit wired eth0 and uncheck enable this connection if you dont use it. Then hit enable this connection on the wireless and see if that helps

---

### Post by stupidkid on 2006-06-28
Please post your /etc/network/interfaces.

---

### Post by aldegaz on 2006-06-28
I tried disabling the wired network but it would come again with the same problem after rebooting.

Here goes my network interfaces:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet dhcp
wireless-essid kkkkk

auto wlan0
iface wlan0 inet dhcp

---

### Post by Eversmann on 2006-06-28
Try leaving the file this way:

auto lo
iface lo inet loopback

iface ath0 inet dhcp
wireless-essid kkkkk

auto ath0

---

### Post by aldegaz on 2006-06-28
will this give me any trouble with my wired connection?

---

### Post by stupidkid on 2006-06-28
Yes probably, don't do that all you need is to add auto ath0.

---

### Post by stupidkid on 2006-06-28
oops double post, the touchpad isn't very fun to use. 

Oh how do I delete a post?

---

### Post by aldegaz on 2006-06-28
DONE!

Thanks, you helped me get my wireless back again from start.

Now that you have helped me here, could you please take a look to another problem with a [Ubuntu Desktop here?]("http://ubuntuforums.org/showthread.php?p=1191180#post1191180")

thanks!

---

