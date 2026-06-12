---
title: "Internet issues on fixed LAN connection"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by paulocr on 2009-04-15
Hello,

I have Kubuntu running on a desktop machine (different one than where I am posting).
This machine is connected to a LAN in the company I work for so I can't tell you much about the server firewall, etc.

First issue:
The computer sometimes has internet connection and sometimes it doesn't.

Second issue:
When it does have internet connection MANY websites fail to be opened, they throw a Page can not be found or similar errors even if the website is up.

Here's my etc/network/interface file:

*# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
#iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet dhcp


this is a fixed IP machine so I don't need any fancy configurations to detect the network, also it's a desktop so the wireless configurations are not necessary either.

Can someone please help me determine where I need to look or perhaps a way to auto-configure the network?

Thanks,

Paulo

---

### Post by paulocr on 2009-04-15
For example, I can access google.com and can connect to Kopete but can't access ubuntuforums.org (I am posting from a different computer obviously :p)

---

### Post by chili555 on 2009-04-15
First of all, I would fix your */etc/network/interfaces* to correct an error and make it a whole lot less 'busy':```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```Next, inability to reach websites sometimes is a symptom of problems with DNS nameservers. They are stored in a file called */etc/resolv.conf*. Please show us:```
cat /etc/resolv.conf
```

---

### Post by paulocr on 2009-04-15
Thanks for your comment, I can not see a difference in what you're asking me to put and what I had except that one of the lines is commented in my file, are you asking me to uncomment the line "iface lo inet loopback" ?

auto lo
#iface lo inet loopback
auto eth0
iface eth0 inet dhcp


Here's the contents of my resolv.conf file:

nameserver 200.91.75.5
nameserver 208.133.206.44

---

### Post by chili555 on 2009-04-15
> are you asking me to uncomment the line "iface lo inet loopback" ?Most definately. It needs to be included and ***not*** commented out. I doubt that the error has much to do with your inability to reach certain websites, however.

The nameservers are not pingable from the outside world and are, I highly suspect, DNS nameservers run internally by your employer. How do these compare to the DNS servers set in a Windows machine? Are both nameservers working correctly, that is, pingable from your Ubuntu machine?```
ping -c3 200.91.75.5
ping -c3 208.133.206.44 
```

---

### Post by paulocr on 2009-04-15
Ok I uncommented it, thanks for that.

About the pings, guess what..they can not be pinged from my Ubuntu machine so I have no idea how they got there:


paulo@ubuntu:/$ ping -c3 200.91.75.5
PING 200.91.75.5 (200.91.75.5) 56(84) bytes of data.

--- 200.91.75.5 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2012ms

paulo@ubuntu:/$ ping -c3 208.133.206.44
PING 208.133.206.44 (208.133.206.44) 56(84) bytes of data.

--- 208.133.206.44 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms

---

### Post by chili555 on 2009-04-15
And what are the nameservers on the Windows machines there at ICE?

---

### Post by paulocr on 2009-04-15
How can I find out those nameservers?

I jumped a little ahead and since those IPs were not pingable so I deleted them from the resolv.conf file and rebooted and the connection seems to be much better now (I can access websites that I couldn't before), was this a wrong step that I took? I backed up the file anyway.

---

### Post by paulocr on 2009-04-15
Actually I just noticed that after the reboot the nameservers get added automatically all over to the resolv.conf file :confused::confused:

paulo@ubuntu:~$ cat /etc/resolv.conf
nameserver 200.91.75.5
nameserver 208.133.206.44

---

### Post by chili555 on 2009-04-15
> How can I find out those nameservers?Please check here: [http://www.ncsu.edu/resnet/windows/ipconfig/](http://www.ncsu.edu/resnet/windows/ipconfig/) Please notice that the *ipconfig /all* command lists DNS nameservers.> the nameservers get added automatically all over to the resolv.conf fileYes, sir. That's the way it is supposed to work; whenever you get an IP address from the gateway, it also supplies DNS server addresses.

You might temporarily try the OpenDNS servers. If it works well for you, you can add them permanently and stop DHCP from changing your */etc/resolv.conf* file. Try making your resolv file look like this:```
nameserver 208.67.222.222
nameserver 208.67.220.220
```It will take effect immediately so you can try it. If it works well, these instructions will make it permanent: [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by paulocr on 2009-04-15
That seems to have done it :)

I am posting from my Ubuntu box right now.

Thanks so much my friend!

---

### Post by paulocr on 2009-04-15
That seems to have done it :)

I am posting from my Ubuntu box right now.

Thanks very much my friend!

---

