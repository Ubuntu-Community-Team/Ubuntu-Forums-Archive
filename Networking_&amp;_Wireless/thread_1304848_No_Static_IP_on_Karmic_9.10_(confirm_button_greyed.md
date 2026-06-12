---
title: "No Static IP on Karmic 9.10 (confirm button greyed out)"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by irvin on 2009-10-29
Hi

I installed 9.10 Desktop 32-bit in Virtualbox. When I try to change from DHCP to a static IP, the button to confirm is greyed out and I can't save this settings. Anyone with the same Problem or ideas to solve this ?

---

### Post by bswilson on 2009-10-30
You're farther along than am I.  Network Manager seems to automatically detect my 2 NIC cards, but I cannot change them from DHCP.  I had to create a new connection (named `Wired`) but I cannot ensure it is always used at boot time.

---

### Post by sp0nge on 2009-10-30
While I haven't upgraded to 9.10 yet, I have stopped using network manager for some time preferring to modify the files manually.

```
sudo vim /etc/network/interfaces
```

will let you modify the dynamic settings

```
sudo vim /etc/resolv.conf
```

to manage nameserver info.

Then simply restart the network and the problem is solved :)

---

### Post by irvin on 2009-11-04
I edited

sudo vim /etc/network/interfaces

and put my stuff in it like i did it a time ago but after restart my network doesn't work anymore. After I deleted the input it won't start anymore.
Does nobody has this Problem ? It's now since 8.10 that the network manager doesn't work any good. It's strange because that's what should work to go in the internet with static ip ?!
I you can't use DHCP...

---

### Post by bastubis on 2009-11-09
It seems to be even worse in Karmic than in 8.10 and 9.04, I can't make any sense of the Karmic networking applet at all now - eh???   

This worked for me on Karmic, I now have a static IP: [http://ubuntuforums.org/showthread.php?t=1309835](http://ubuntuforums.org/showthread.php?t=1309835) 

You have to remove network-manager and network-manager-gnome before you set up the static IP manually or your changes will just be ignored.

---

### Post by gordintoronto on 2009-11-09
> **irvin said:**
> Hi

I installed 9.10 Desktop 32-bit in Virtualbox. When I try to change from DHCP to a static IP, the button to confirm is greyed out and I can't save this settings. Anyone with the same Problem or ideas to solve this ?

I think you mean the "apply" button?  It worked 100% for me, if the button was greyed out, you didn't have all the required settings entered.

---

### Post by gordintoronto on 2009-11-09
> **irvin said:**
> I edited

sudo vim /etc/network/interfaces

and put my stuff in it like i did it a time ago but after restart my network doesn't work anymore. After I deleted the input it won't start anymore.
Does nobody has this Problem ? It's now since 8.10 that the network manager doesn't work any good. It's strange because that's what should work to go in the internet with static ip ?!
I you can't use DHCP...

If it didn't work, then you didn't set it up properly.  Post your interfaces file and perhaps someone can tell you how to fix it.

---

### Post by irvin on 2009-11-10
Now I removed the network Manager

sudo apt-get remove network-manager network-manager-gnome

and added this to the interfaces file

auto eth0
iface eth0 inet static
address 192.168.2.16
network 192.168.2.0
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1

Now, it works

But, I did a lot of new installations and I could never make a static IP with the Network manager (always greyed out).

But Now I edited the interfaces file to its original settings and installed the network manager via Synaptic again.

And now, surprise it works with the Gnome Network Manager :-)

---

