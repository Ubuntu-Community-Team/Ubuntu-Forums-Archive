---
title: "MythBuntu Wireless Networking"
date: 2008-04-14
forum: Mythbuntu
---

### Post by MARKYB0Y on 2008-04-14
Hi All,

I have just installed MythBuntu and I currently have it running on a wired network connection fine, however I wish to use it wirelessly using a USB stick I have, I am totally new to Ubuntu and so can anyone point me in the direction of how to go about setting it up.

There does not seem to be any plug and pray going on

thanks in advance

---

### Post by ghuber on 2008-04-14
For me I chose a wireless USB stick that worked with the Kernel.  I forget the brand off the top of my head.   


It was plug and play in that when I plugged it in I then got a eth1 show up in /dev

yeah me.

So to get it to connect to my wireless network I created a script and put it into
/etc/init.d

and did chmod to execute it.

My script looks like:

sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "MY_SSID"
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

Now when I boot I get a IP and can it just works.

I "think" that was all I had to do....

Geoff

---

### Post by MARKYB0Y on 2008-04-15
Hi geoff, thanks for the reply.

after a little more playing last night I now have it so that it does see the wireless networks

however I have to enter the password each time the machine boots, does it not save the network settings anywhere?

I would like to have the machine boot and connect to the wireless network with nothing required from the user

thanks

---

### Post by laga on 2008-04-15
Set the password to an empty string. Just don't put anything in the box when it asks you to set the password.

---

### Post by MARKYB0Y on 2008-04-16
Laga, that is not very secure is it

I need to have it passworded

---

### Post by ghuber on 2008-04-17
I just filter based on MAC address...   I'm not too worried about people sniffing packets in my area and my signal does not reach all that far.

---

### Post by laga on 2008-04-17
> **MARKYB0Y said:**
> Laga, that is not very secure is it

I need to have it passworded

I'm not sure we're understanding each other here. I'm not suggesting that you disable the encryption for your network.

I'm suggesting that you disable the password for gnome-keyring so the key for your network can be accessed without having to enter a password.

That's not terribly secure, but I imagine that it should be OK for a MythTV box in a private network.

---

