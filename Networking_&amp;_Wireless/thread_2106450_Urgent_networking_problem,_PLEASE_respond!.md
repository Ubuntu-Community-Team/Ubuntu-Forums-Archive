---
title: "Urgent networking problem, PLEASE respond!"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by zesterer on 2013-01-19
Hi,

I have a problem with my laptop. I tried to follow instructions to edit etc/network/interfaces to allow me to have a static IP. It didnt work, and now when I boot my PC it says: Waiting for network configuration, and then Booting without network configuration. I have tried editing interfaces again, but I have only mucked it up even more tbh. How can I get my Internet back? I need it really fast to do some work! Can I reset its default values or something? I'm a little new to Linux, and I have been using my iPod for Internet.

Thanks,

Barrysmith

---

### Post by chadk5utc on 2013-01-19
> **zesterer said:**
> Hi,

I have a problem with my laptop. I tried to follow instructions to edit etc/network/interfaces to allow me to have a static IP. It didnt work, and now when I boot my PC it says: Waiting for network configuration, and then Booting without network configuration. I have tried editing interfaces again, but I have only mucked it up even more tbh. How can I get my Internet back? I need it really fast to do some work! Can I reset its default values or something? I'm a little new to Linux, and I have been using my iPod for Internet.

Thanks,

Barrysmith

Yes you can change the original settings back to the default. but it would really help us to help you if we knew a little more about your network settings you have?  Can you post that information? Perhaps the contents of /etc/network/interfaces

---

### Post by zesterer on 2013-01-19
I don't really need a static IP tbh. I just want the settings back to how they were (I never touched the network settings before). How can I return them to default? :S

---

### Post by chadk5utc on 2013-01-19
The contents of this file should look something like this for default
> 
# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp
once thats change then
> sudo /etc/init.d/networking restart

---

### Post by Elfy on 2013-01-19
You should really backup system files you are editing prior to fiddling ;)

You can do that from a file manager easily enough. You'd need to run it as root to copy it back.

With a terminal

```
sudo cp /path/to/original /path/to/backup
```

for example 

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

I use nano to edit files, running it with -B creates a backup.

```
sudo nano -B /etc/network/interfaces
```

My interfaces file is 

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

---

### Post by chadk5utc on 2013-01-19
I agree with Elfy on that always a good idea to make a back up prior to edit.

---

### Post by zesterer on 2013-01-19
It works in that it no longer boots up strange, and there is now a wireless icon, and I can connect to my router. But I still can't access the Internet for some reason or another.

Thanks for the MASSIVE help guys, you're lifesavers :)

---

