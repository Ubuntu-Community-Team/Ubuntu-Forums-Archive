---
title: "Installing Ubuntu on a windows networking environment."
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by shorthand on 2010-02-08
what I did to configure the network:

1) remove network manager

sudo apt-get remove networkmanager

2) make ip address entries in /etc/network/interfaces and /etc/resolve.conf files.

/etc/network/interfaces

------------
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.79
netmask 255.255.255.0
gateway 192.168.0.200
------------

/etc/reolve.cong

name server 202.56.215.54
name server 202.56.215.55


when I do networking restart it is showing 

"reconfiguring network"       [OK].  

However Google.com is an unknown host. I am getting the feeling I am missing something. The network adapter is showing green led . Does it have something to do with the microsoft networking that's running in my office?

Will greatlty appreciate all help from a Linux newbee but a Unix old timer.

---

### Post by suseendran.rengabashyam on 2010-02-08
Hi,

Network Manager can be uninstalled using the following command

```
sudo apt-get remove network-manager
```

After uninstalling you can check whether the package was removed properly by entering

```
sudo dpkg -s network-manager
```

In the status you should find "deinstall ok ....", which means that you have properly uninstalled your NM.

I see that your /etc/network/interfaces file is proper but you need to make some minor changes in your /etc/resolv.conf file paying attention to the spelling. Also the file itself should be spelt as resolv.conf!

It should read

```
nameserver 202.56.215.54
nameserver 202.56.215.55

```
Restart your network by entering

```
sudo /etc/init.d/networking restart
```

Check if the setup is working by first pinging your nameserver IPs, then resolving a few hostnames and then pinging a few other hosts on the Internet by using their names.

Please let me know if you were successful.

---

### Post by shorthand on 2010-02-08
Suseendran,

It works perfectly well. 

I did a reinstall of Ubuntu from the Wubi installer and followed the steps I previously tried. 

And in no time I could connect to Google using my favourite browser, Chrome which I then downloaded and installed quite easily. Just like in Windows, following the given instruction.

Thanks for helping me (how do u guys remember these big commands? I guess it's about using them all the time)

Thanks & Regards
Indrajit

---

