---
title: "wlan0 static ip won't connect"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by houserparker on 2010-05-18
Hi there,

I'm trying to configure a static ip address so that I can run servers on my lucid Desktop. 

```
ifconfig
``` returns wlan0 as the wireless interface.

When I enter 

address 192.168.0.10 (desired static ip)
netmask 255.255.255.0 
gateway 192.168.0.0 (router gateway)

I can no longer connect to the web with wlan0

I have been able to setup static ip with eth0 on other pc's many times.

Can anyone help?

---

### Post by houserparker on 2010-05-18
There must be guru out there that knows how to solve this one.:)

---

### Post by lisati on 2010-05-18
My preference is to set static IP addresses in my router. Details vary according to which make and model you are using.

---

### Post by houserparker on 2010-05-18
Thankyou for replying.

I have a netgear DGN2000 router/modem and the gateway is 192.168.0.1

Static ip has worked in the past with the below configuraion on my laptop:-

auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

The difference now being on my desktop the interface is now wlan0?

I have used the below settings in Network Manager to no avail.

address 192.168.0.20
netmask 255.255.255.0
gateway 192.168.0.1

---

### Post by houserparker on 2010-05-19
somebody, anybody?

---

### Post by N00b-un-2 on 2010-05-19
I'm having the same problem you are.  I'm assuming that you're trying to configure samba?  I've gotten it set to where if I use a static IP address and set the netmask to 255.255.255.0, I can access shared files over the network but I can no longer get on the internet.  Setting the IP address back to DHCP lets me access the internet, but then I can's see shared files.  WTF?  And why doesn't Samba effing WORK OUT OF THE BOX?  This is a major pain in the *** for linux users.  It would be one thing if it just didn't interoperate with Windows by default, but not being able to share files PERIOD is a huge detriment.
It's a bit of a hack if you ask me since you should be able to use the default network that is in the main menu and on the desktop, but I've had good luck with NFS.  The thing about NFS is that you HAVE to set static IP addresses on the router, but leave your network settings as DHCP on your computer.  NFS tends to be much faster than Samba too, in my experience.

---

### Post by houserparker on 2010-05-20
Yeah I'm trying to configure Samba and others Servers that rely on a static ip. 

I've scoured the forums and google to try and find a solution but theres no specific documentation. 

And your right Samba does seem overly complicated for what is does.

I had a look at NFS after you suggested it and it seems to be the way to go.

All I need to do now is find out how NFS will work with static ip's from my router.

Thanks for the tip.

---

### Post by N00b-un-2 on 2010-05-20
I can't speak for every router out there, but on mine (it's a Netgear A/B/G wireless w/ 5 ethernet ports) you just go to the LAN settings tab and it has a tab where you can reserve IP addresses by the MAC address that is connected to it.  NFS is a quick and dirty way to get the basic functionality that seems to be broken in Ubuntu.  BTW, have you tried using the "connect to server" function that is just below "Network" in the main menu?  I was very surprised to find that by entering in the IP address of the computer with the samba shares I was able to connect.  Now why is it that this doesn't work using the default dialogue in Nautilus?
Oh, and just in case you're wondering it is possible to set up NFS on a Windows machine, you just require one of the premium versions of Windows (Windows 7/Vista Ultimate, XP Pro, or any of the Server versions available).  There are plenty of tutorials out there for setting up NFS on a Windows box, just google them.  I hope that this was helpful to you.

Oh, and before I forget.  You can also install the package "Gshare" which sets up a shared folder on your network via FTP.  It defaults to a folder it creates called "Shared Folder" in your home directory, but you can use gconf-editor to change the directory it shares to whatever you would like.  Personally, on my home network I like to be able to share any file in my home directory with other users so I simply set it to '~/'

sorry for the long reply, but I just want to let people know about the networking options available.

---

### Post by houserparker on 2010-05-20
Yep I have a NETGEAR DGN2000 and following your instruction found the LAN tab and was finally able to assign my Desktop a static ip. Your legend.

And good job spreading the word that's the only way people find about these things.

Job well done.

---

### Post by houserparker on 2010-05-20
For anyone out there that's having trouble assigning a static ip with interface wlan0 in Ubuntu stop looking. Just assign the ip through your router.

---

### Post by N00b-un-2 on 2010-05-23
I'm really glad that I was able to help you out.  I figure why make someone else beat their head against the wall when I already did?  NFS really seems to be the best, albeit not the most 'user-friendly' way to network on Linux.  I've been messing with the Gshare application which takes a lot of the work out of setting up filesharing between linux machines, but I have run into some issues with file permissions and ownership.  Oh well... If we wanted 'user-riendly' we wouldn't be using Linux now would we?  lol

---

### Post by escipio on 2010-05-30
Hi all,

I am having the same problem with static IP.
"Interfaces" worked properly until I updated to 10.04.
I've been reading what you said, but the problem is that my router does'nt allow to asign static IP.

What I am now doing is starting my xomputer with a dynamic IP and, once connected, change the "interfaces" file (the new one with an static ip configured)  and restart the network.

I should be careful of changing again the "intefaces" before leaving Ubuntu, in order that the computer get connected after reinit.

Any solution?

Thank you, very muc.

Best wishes,

---

