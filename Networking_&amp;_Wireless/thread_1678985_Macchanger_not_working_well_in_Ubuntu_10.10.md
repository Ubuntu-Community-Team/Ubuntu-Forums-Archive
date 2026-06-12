---
title: "Macchanger not working well in Ubuntu 10.10"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by MWesten on 2011-01-31
Hello friends, I have a problem, hope you can help me, I really love Ubuntu and it always works fine, this is my issue:

I'm testing some settings on my network, so I'm using "macchanger" so I can change my MAC Address (Wlan0), it has always been working fine, but now, the mac changes, but after some time (say 20 mins) it suddenly changes again to the original one. This is happening in Ubuntu 10.10 because in 10.04 never happened before. Thanks for your help.

I'm using:
sudo ifconfig wlan0 down
then: macchanger -m xx:xx:xx (some mac) wlan0
and finally: sudo ifconfig wlan0 up

I get the message that everything was ok and if I type ifconfig I can see the MAC I put on wlan0, but, like I say, after some short time and without me doing something, the MAC goes back to the original one.

The issue is happening in UBUNTU 10.10, can you please help me?

Thanks a lot, I really love Ubuntu and its great community.

Michael

):P

---

### Post by Kirboosy on 2011-01-31
Well you could also manually edit your network interfaces.

```
sudo gedit /etc/network/interfaces
```Then once you have the file open just add
```
auto eth0
iface eth0 inet dhcp
       hwaddress ether 01:02:03:04:05:06
```then in order for the changes to take place you need to restart your networking address
```
sudo /etc/init.d/networking restart
```This is permanent but you can always remove that line whenever you want the real MAC address to come back. :D

~Drew

---

### Post by MWesten on 2011-01-31
Thanks a lot for the quick answer!
And for example, if I want to change the mac for my wireless device (wlan0):


auto **wlan0**
iface **wlan0** inet dhcp
       hwaddress _**ether**_ 01:02:03:04:05:06
What do I need to put insted of "ether" or do I leave it like that?

So as long as I leave the line in  /etc/network/interfaces the changes are going to be permanent? 

**Thanks again for the help and quick reply and hope you can solve this doubt I have.**

Michael

---

### Post by Kirboosy on 2011-01-31
I think it should still work.

Yes as long as you leave that line in the file the changes will be permanent. 

You could also spoof on the fly with 
```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether 00:11:22:33:44:55
sudo ifconfig wlan0 up
```If you are interested in hacking/penetration testing you might want to check out [Backtrack]("http://www.backtrack-linux.org/downloads/") They are about to release the new version but I use it regularly for my security testing. It has every tool known to man for hacking already installed in it.

~Drew

---

### Post by MWesten on 2011-02-03
Thanks for your help Caboose885, as soon as I get to my home, I'll try it and I'll post the results.

Thanks.

---

