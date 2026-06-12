---
title: "How to connect to DSL connection"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by thenailedone on 2009-12-18
Hi, 

Browsed the forum until I found a way to connect to the internet using 'sudo pppoeconf' and then running 'pon dsl-provider'...

Now the problem is the network manager applet does not see that I am connected to the internet and I am trying to use UltraVPN... what am I missing?

All assistance greatly appreciated...

---

### Post by shredder12 on 2009-12-18
You are actually facing a very basic problem.. 
When you run sudo pppoeconf it means that you are manually handling your network connection.. at least ther wired connection..
you can view the changes in /etc/network/interfaces file done after using this command..
Once you do this and reboot.. after looking at the changes done in /etc/network/interfaces file by pppoeconf your network-manager shows that wired connection is unmanaged thinking that you are manually handling the wired  connection.. 
And that's why it doesn't know (or show) that you are connected to Internet or not.

And as far as your vpn problem goes.. i think you can still manage VPN connections using network-manager...
have you tried configuring it.

---

### Post by thenailedone on 2009-12-18
> **shredder12 said:**
> You are actually facing a very basic problem.. 
When you run sudo pppoeconf it means that you are manually handling your network connection.. at least ther wired connection..
you can view the changes in /etc/network/interfaces file done after using this command..
Once you do this and reboot.. after looking at the changes done in /etc/network/interfaces file by pppoeconf your network-manager shows that wired connection is unmanaged thinking that you are manually handling the wired  connection.. 
And that's why it doesn't know (or show) that you are connected to Internet or not.

And as far as your vpn problem goes.. i think you can still manage VPN connections using network-manager...
have you tried configuring it.

Hi,

Yes... it is configured (used an online tutorial) and it does show when I click on the network manager icon... even started it in terminal but I can't see anything happening... I want my folding@home apps to connect via the proxy so they can get work units but they still don't connect...

Neil

---

### Post by shredder12 on 2009-12-18
I am not sure about configuring VPN connections..
but if you are unable to connect and ppp settings seem to be the problem then you can comment out all of the lines in /etc/network/interfaces file.. except the 2 concerning "lo" interface..
your file should finally look something like this..
```
auto lo
iface lo inet loopback

```
Reboot.. or just restart the network-manager..
```
sudo /etc/init.d/network-manager restart
```

I am doing all this to remove the settings of pppoeconf so that NM takes over the wired network and you can finally check if you are able to use VPN now or not..

---

### Post by thenailedone on 2009-12-18
> **shredder12 said:**
> I am not sure about configuring VPN connections..
but if you are unable to connect and ppp settings seem to be the problem then you can comment out all of the lines in /etc/network/interfaces file.. except the 2 concerning "lo" interface..
your file should finally look something like this..
```
auto lo
iface lo inet loopback

```
Reboot.. or just restart the network-manager..
```
sudo /etc/init.d/network-manager restart
```

I am doing all this to remove the settings of pppoeconf so that NM takes over the wired network and you can finally check if you are able to use VPN now or not..

Did all the above and it did give NM control over the wired network... but for some reason it doesn't want to connect... shows it is trying then says disconnected?  Could there be a setting or something I am missing when setting up the connection?  It works manually (but I can't remember all the settings I used when configuring it)...

(Thanks thus far btw, been most helpful!!)

---

### Post by shredder12 on 2009-12-18
I don't know much about configuring VPN connections.. but it seems pppoeconf is not the culprit..
have you tried rebooting... (jst a silly thought).

---

### Post by thenailedone on 2009-12-19
> **shredder12 said:**
> I don't know much about configuring VPN connections.. but it seems pppoeconf is not the culprit..
have you tried rebooting... (jst a silly thought).

:) old school windows user... when in doubt I always reboot :) 

:( which still leaves me with the problem :confused:

---

### Post by thenailedone on 2009-12-21
Just an update and a BUMP!

Installed Kubuntu 9.10 and having the exact same problem... and after starting to write this it has struck me... Ubuntu 9.10, Kubuntu 9.10... duh, difference is desktop environment... duh :(

-1 for me...

---

