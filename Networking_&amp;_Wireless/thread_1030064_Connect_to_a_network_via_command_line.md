---
title: "Connect to a network via command line?"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by kevin11951 on 2009-01-04
Im very close to creating a server, but I will need to connect wirelessly to my router, is it possible (easy) to connect to a wireless network via command line?

by the way, my wireless network is encrypted via "WPA-PSK [TKIP]" if that makes a difference?

---

### Post by kevin11951 on 2009-01-04
sorry to bother all of you, google answered my question, finally:
[http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html](http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html)

---

### Post by aesis05401 on 2009-01-04
> **kevin11951 said:**
> Im very close to creating a server, but I will need to connect wirelessly to my router, 

Is the router or your server providing DHCP, or is the lan static addressed?

If the router is handling DHCP (probably the simplest option) then first configure your network interface device (eth0 for my wired box configured via ifconfig commands), then run the dhclient <dev> command to poll for DHCP information.  

If this completes successfully you should be seeing the network from your server.

As for the encryption, I use wired networks to avoid the wireless encryption protocols.  I imagine setting the keys is just a matter of passing the right parameter when applying for network credentials.

---

### Post by kevin11951 on 2009-01-04
new problem:

when i type: sudo iwconfig wlan0 key <my key>

it doesn't work

it outputs that "<my key>" is an invalid argument...

---

### Post by zmjjmz on 2009-01-04
Install ceni.

---

### Post by kevin11951 on 2009-01-04
> **zmjjmz said:**
> Install ceni.

hm? What is that? its not in the repo.

also: w/o internet?

---

### Post by zmjjmz on 2009-01-04
I'm hoping you can get a temporary ethernet connection. 
It can be found here.
[https://launchpad.net/~inx-devel/+archive](https://launchpad.net/~inx-devel/+archive)

---

### Post by aesis05401 on 2009-01-04
I have never used Ceni, but have heard good things about it.  I think Sidux.com is the place for more info, right?  

Before installing a new tool though, the OP might try passing the key differently.

So, Kevin11951, what are you doing before attempting to assign the key?  Are you running sudo iwconfig essid <networkname>?

Are you using any characters that need to be escaped in the parameters you are passing?

I do not use wireless, but there are threads I have read on needing to set a restricted flag for routers that only accept encrypted sessions.

More info might help us find an instant solution, but installing a tool like Ceni might make your life easier in the long run anyhow...

---

### Post by melojo on 2009-01-04
Is the key in hex or ascii?

---

### Post by p_quarles on 2009-01-04
Moved to Networking and Wireless. 

+1 for Ceni.

---

### Post by kevin11951 on 2009-01-04
> **melojo said:**
> Is the key in hex or ascii?

ascii

---

### Post by aesis05401 on 2009-01-04
> **kevin11951 said:**
> (it doesn't matter if you all know the password)

Just a quick security note: revealing any password is dangerous because it shows a bit of your thought process. 

Edit: Kevin11951 - done and done.  Good luck on your networking issues.  See you 'round :) 2600.

---

### Post by kevin11951 on 2009-01-04
> **aesis05401 said:**
> Just a quick security note: revealing any password is dangerous because it shows a bit of your thought process. 

In this case you are going the extra mile to implement a security feature on your lan, then assigning a password that any script kiddie could brute force inside of five minutes ;)  Did you take more care with your UbuntuForums account password?  

Plenty of trolls will mess with you just to have a good time.  Taking the info provided by your password (a potential last name to go with the first name in your forum sig), and utilizing google I come up with an interesting amount of info about the '<snip>' of the world.  

Of course, +50 points to you if your name is not <snip>.  Maintaining credible but false net identities was always one of my favorite Hacker Challenge activities.

fine, remove my password from your quote, as well as my full name, and i will do the same to my OP.

---

