---
title: "Static DNS?"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by avacomputers on 2009-03-26
I would like to make the switch to linux, but a couple things stoping me. Is there anyway I can set a static DNS, as I can in windows. Or do I have to keep doing it each time. I am using Ubuntu 8.10.

---

### Post by trecool999 on 2009-03-26
You can make it static, but I've forgotten how you do it.

---

### Post by avacomputers on 2009-03-26
I actually just found this. Do you think it will work?

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by trecool999 on 2009-03-26
It looks like it, but you should just be able to change it in the network configuration tool.

---

### Post by eloydark on 2009-03-26
Yes it will work but you have to disable the network manager so that it will not overwrite your settings before you begin. To do that go to /etc/NetworkManager/nm-system-settings.conf and change
```

[ifupdown]
managed=true
```
to ```

[ifupdown]
managed=false
```

if you find it easier just do a
```

sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

I would also recommend not to use vi or nano since you are new to linux, instead replace it with gedit

---

### Post by avacomputers on 2009-03-26
Thanks Guys. One more thing. Is there a password manager for Linux?

---

### Post by trecool999 on 2009-03-26
Sort of.
You can set the password to the root and your account, but that's about it. I don't know what other passwords you would need.

---

### Post by eloydark on 2009-03-26
For internet purposes or for overall?
If your question is for internet then firefox, opera and all the popular web browsers have password managers. If your question is for overall then I would ask why would you need one? You only have two passwords, yours and your super user, and the super users pass is not to be entered automatically... your password is only needed at logon and this can be disabled if you wish (automatic logon)

---

### Post by avacomputers on 2009-03-26
I meant for online. With windows I use Roboform, so I was looking for something like that. Is the password manager that comes with Firefox, any good? If I clear my history, does it go away?

---

### Post by eloydark on 2009-03-26
I prefer opera but firefox is also good. Its' password manager is not that good, it simply stores the passwords but it's better than nothing. When you clear your history it will ask you if you want to clear the passwords as well ;-)
Opera's pass manager is much better, it allows more than one passes on a site and pop up a window to let you choose which one to use to login.
Also there is [sxipper]("http://www.sxipper.com/") for firefox. Never used it but seems to do the job quite well!

---

### Post by avacomputers on 2009-03-27
> **eloydark said:**
> Yes it will work but you have to disable the network manager so that it will not overwrite your settings before you begin. To do that go to /etc/NetworkManager/nm-system-settings.conf and change
```

[ifupdown]
managed=true
```
to ```

[ifupdown]
managed=false
```

if you find it easier just do a
```

sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

I would also recommend not to use vi or nano since you are new to linux, instead replace it with gedit

I opened the above location and it is already set to false. I then tried following the article at the link I provided. When I open up network/interface this is what it reads

auto lo
iface lo inet loopback


That's it. Nothing else.

---

### Post by eloydark on 2009-03-27
This is normal, this happens because the network manager is now controlling your ethernet card. If you write the text I will provide you the network manager will stop controlling it (the setting false you saw).

So to help you even more here is what you will do:

```
ifconfig
```

It will show you all the network cards that are identified in your system. It will have lo eth0 wlan0 vmnet1 and stuff (some you might not have!)
the eth# will be your ethernet cards
the wlan# are your wireless
the vmnet are your virtual networks (if you have vmware)

most of the times your network card is eth0 but just to be sure it's good to check that the "0" is indeed correct.

So now that you have checked that eth0 is correct it's time to enter it in interfaces
Simply do a
```
sudo gedit /etc/network/interfaces
```
and add after the
```
auto lo
iface lo inet loopback
```

this text
```
auto eth0
iface eth0 inet static
address YOUR.IP.ADDRESS.XXX
netmask YOUR.NET.MASK.XXX
gateway YOUR.GATE.WAY.XXX
```

this way you have configured your ethernet card to connect with static address but you have not yet specified your DNS Servers. Personally I prefer this method but there are other methods as well to do that. It's important to left click on the network manager icon on your taskbar and disable the "enable networking" cause it might ruin your settings. After you have done this just run

```
sudo gedit /etc/resolv.conf
```

and add in the file the following text

```
nameserver DOMAIN.NAME.SERVER.XXX_1
nameserver DOMAIN.NAME.SERVER.XXX_2
nameserver DOMAIN.NAME.SERVER.XXX_3
```

and so on depending how many DNS you like. Two are enough though ;-)
As you have guessed, the caps with the dots in between is where you put the IP addresses...
After that you can enable the network with 
```
sudo ifup eth0
```
and disable it with
```
sudo ifdown eth0
```

The network of course will automatically be enable on boot ;-)
Hope this works for you ;-)

---

### Post by avacomputers on 2009-03-27
Ok. BUt I only want to change my DNS. I would like the DHCP to still provide Ip address.

---

### Post by avacomputers on 2009-03-27
Any one, want to help?

---

### Post by eloydark on 2009-03-28
then add this on your /etc/network/interfaces

```
auto eth0
iface eth0 inet dhcp
```

and edit resolv.conf as mentioned above

---

### Post by avacomputers on 2009-03-28
So do I leave out the info for the Ip?

---

### Post by avacomputers on 2009-03-28
Ok. Now I think I screwed it up. I overwrited my settings. Now I can't get internet on the machine. There are no connections.

---

### Post by eloydark on 2009-03-28
> **avacomputers said:**
> So do I leave out the info for the Ip?

You don't leave it out, you write:

```
auto eth0
iface eth0 inet dhcp
```

the dhcp part is very important. Your network is not screwed up.
When you have done this and saved it you enable the network by running

```
sudo ifup eth0
```

if by any chance this does not work you can get back to your old settings simply by removing the text

```
auto eth0
iface eth0 inet dhcp
```

from your /etc/network/interfaces file. It is important that you understand what and why you are doing it, this is why I used so many details the first time. If there is something that you do not understand you can ask, this way when you meet another problem you can explain it better here in the forum.

---

### Post by eloydark on 2009-03-28
> **avacomputers said:**
> Ok. Now I think I screwed it up. I overwrited my settings. Now I can't get internet on the machine. There are no connections.

There are connections, you have just disabled the network manager that appears in your taskbar. The network manager is really buggy so by disabling it you have been saved from a lot of trouble and potential problems. The network/interfaces is a more straight forward and correct approach to connect to the internet and will work on any linux distro you might use!

---

