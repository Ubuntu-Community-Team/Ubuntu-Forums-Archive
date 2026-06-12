---
title: "Ubuntu 10.10 to 11.4 network  issue"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by burtgoogly on 2011-05-14
[INDENT]  After an update yesterday from Ubuntu 10.10 to 11.4 after a reboot the  network is only briefly available then goes off.  I am able to ping it  for about 6 replies then nothing.  I am using it as my webserver and the  pages load then are not available.  Might somebody be able to point me  in the right direction with this please? (best to warn I am a beginner)
 
Thanks[/INDENT]

---

### Post by irv on 2011-05-14
Need a little more information. Is this a wire or wireless connection? If it is a wire connection, take a look at this link and see if this would help. [http://www.webupd8.org/2009/06/how-to-manually-set-up-your-wired.html]("http://www.webupd8.org/2009/06/how-to-manually-set-up-your-wired.html")
If it is a wireless I can give you some other things to try. Also if it is a Wireless it would help to know what card you are using.

---

### Post by burtgoogly on 2011-05-14
Hi,

Its a wired connection, hosted on a HyperV.  This is what my /etc/network/interfaces looks like:


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.22.60.2
netmask 255.255.252.0
gateway 10.22.63.254

Thanks

---

### Post by irv on 2011-05-14
Your interface file looks good, I compared it with my server interface.

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.1.105
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.1.255
 gateway 192.168.1.1


I am not sure what the problem is. I don't think doing a manual install of the network will help. Maybe someone else has something you can try.

Edit: I just noticed you do not have a network ip or broadcast ip setup. I don't know if that has something to do with your problem.

---

### Post by burtgoogly on 2011-05-14
Thanks for your time irv :-)

---

### Post by irv on 2011-05-14
> **burtgoogly said:**
> Thanks for your time irv :-)

I just added this edit to my above post: 
I just noticed you do not have a network ip or broadcast ip setup. I don't know if that has something to do with your problem.

---

### Post by burtgoogly on 2011-05-14
Not sure that is does matter...I have put the interface back to dhcp to test and I still get the same behaviour :-(

---

### Post by irv on 2011-05-14
> **burtgoogly said:**
> Not sure that is does matter...I have put the interface back to dhcp to test and I still get the same behaviour :-(

I believe your 
Network ip = 10.22.60.0
Broadcast ip = 10.22.60.255

Maybe worth trying to add them to see if it will fix the problem.

Edit: if you make these changes you will need to restart your network:
```
sudo /etc/init.d/networking restart
```

---

### Post by burtgoogly on 2011-05-14
Changes made and rebooted but still no change.  I also deleted the the virtual network connector on HyperV and remade, still the same behaviour.  Maybe worth mentioning that I have other Ubuntu installs running on the the same HyperV and they are ok (although they are still on 10.10).

What I dont get is why I can briefly get the website then it drops.  It's as if something is loading and blocking it...

---

### Post by burtgoogly on 2011-05-14
Just another update if anyone is following this.  I have added another network adapter on HyperV and added it to be DHCP.  My DHCP server has issued it with an address no worries but like the static IP I cannot ping it.

---

### Post by irv on 2011-05-14
There has been many network issues with 11.04; wire and wireless. I am using 11.04 on my laptop, but I stayed with 10.04 on my server and will wait until I need to change it in the future. When it comes to server I believe if it is not broke just leave it alone. I know this does not help you at this point, but I would just backup to what was working.

I hope someone else will just on this one if they have something else to add that might help.

---

### Post by burtgoogly on 2011-05-14
Thanks irv.

I have just done a brand new install of 11.4 on my HyperV and guess what...I can't ping it but it has been given an IP from my DHCP...

I cannot get out to the internet either (I am behind a proxy but have put the settings in and exported them)

Sounds like there are issues with 11.4 :-(

---

### Post by Inigo Montoya on 2011-05-27
do the LIC modules load correctly (hv_vmbus, hv_netvsc, hv_blkvsc, and hv_storvsc)? do a lsmod to look it up.
have you tried a legacy network interface instead of the standard one in hyperv? (see [http://guyellisrocks.com/hardware/hyper-v-with-vista-x64-and-ubuntu-linux-desktop-x64/](http://guyellisrocks.com/hardware/hyper-v-with-vista-x64-and-ubuntu-linux-desktop-x64/))

---

