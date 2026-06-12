---
title: "Loosing static ip information after reboot."
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by mattsid1 on 2009-09-14
First of all I'm a relative newb, but have been able to sort out most problems with the help of Google and the command terminal. 

After running Ubuntu 9.04 successfully on my home pc for the last month, I decided to dual boot my work PC.

After installation I had no network, but kind of expected it since my work pc runs off a static ip address. I then did the following

clicked on the connection icon, highlighted the Auto eth0 and clicked edit. 
clicked on the ip4v tab, selected manual connection, edited the appropiate ip, netmask and gateway and DNS. Clicked 'Apply'. Rebooted, still no internet. 

Did some searching on the net and then did the following.

sudo gedit /etc/network/interfaces

original looked like this.

auto lo
iface lo inet loopback

I then added the following 

auto eth0
iface eth0 inet static
address 210.110.148.126
netmask 255.255.255.0
gateway 210.110.148.1
broadcast 210.110.148.255
network 210.110.148.0

issued a sudo /etc/init.d/restart networking command and voila I had internet. 

Rebooted my pc, but on restart I had nothing. I clicked on the network icon and the 'Auto eth0' card that had been there before had disappeared. I tried manually adding it again, getting my MAC address using ifconfig, but no luck. 

So I quickly installed ubuntu again, to check if it wasn't some sort of glitch. Did exactly the same thing again.

Any ideas, because I need network for my job.

---

### Post by shredder12 on 2009-09-14
Look I think you created a kind of confusion for the Network manager.

When you changed the settings for auto eth0 by clicking on the network icon..
that would have been enough. 

But when you changed the /etc/network/interfaces after the reboot you network manager read that file and thought that you are manually managing your network connections on eth0 interface... 

so it backed off..
Now, you can open the /etc/network/interfaces file and comment out the lines... that concern eth0 interface.. 

> 

#auto eth0
#iface eth0 inet static
#address 210.110.148.126
#netmask 255.255.255.0
#gateway 210.110.148.1
#broadcast 210.110.148.255
#network 210.110.148.0


then reboot.. this time configure the connection manually from the network manager.
since you have commented out the eth0 line you won't see an auto eth0 connection now..
jst right click on the network icon and click on edit connections then add a connection, fill the manual configuration and save it..

It will work..

>>> Actually I think even if you don't change the /etc/network/interfaces file now and try running commands like

```
sudo ifconfig eth0 up
```
```
sudo /etc/init.d/networking restart
```

you will probably get connected to Internet...
you can check it in your browser..

---

### Post by mattsid1 on 2009-09-15
Thanks! That worked great, simple as well. 

For the benefit of anybody who gets in the same mess it was resolved exactly as suggested.

I just restored the network interfaces file to it's original state

auto lo
iface lo inet loopback

Then manually added a new connection via the network manager. 

At first a sudo /etc/init.d/restart networking command didn't work. But a simple reboot did.

---

### Post by shredder12 on 2009-09-15
Actually I once got into a similar problem when i manually configured my ADSL modem..
and after days of search could found out.. the cause of the problem..

---

