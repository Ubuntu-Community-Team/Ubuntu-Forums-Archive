---
title: "Using SSH to manage my home network"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by Volume on 2009-07-27
Hello,

I am learning how to use SSH to manage / play around in my home network.  I have managed to log into my wife's computer remotely (from mine), but when I login, I have to use USERNAME@IPADDRESS, but I would like to be able to type the computer host name instead of the IP address.

Is there a way to do this?  Below is what I have tried.

```
mokrunka@Engineer:~$ ssh jenandsteve@10.0.0.3
jenandsteve@10.0.0.3's password: 
Linux Nurse 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64

```

Thanks!

---

### Post by mediumcool on 2009-07-28
You could add your wifes host name to /etc/hosts on your machine.

example -

10.0.0.3    your-wifes-host-name

---

### Post by vanadium on 2009-07-28
In order for that to work always, you must make sure that your wife's computer each time gets the same ip address when connecting to the network. This is something you can configure in your modem. Usually, modems are set up to provide "the next available" ip address when a computer contects. This means that your ip might vary between different sessions.

---

### Post by mapes12 on 2009-07-28
I'm not sure if this will help but it's a post I have followed to faultlessly network my 2 Ubu boxes:

> **SpaceTeddy said:**
> lets see if i can speak plain english (haven't done it for a while) :)

so, i guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved. I only state this because the solution that i am thinking of writing down here will NOT WORK to access windows machines.

I also do not know if there is a simpler way - this is the simplest way i know.

1.) install the openssh-server
to do that, type this command in both computers and let them run through. They may ask you to confirm the installation - say yes !

```
sudo apt-get install openssh-server
```

2.) find out the IP addresses of your computer
this is important to address the computers. use the following command to obtain your computers IP-Address
```
ifconfig
```

this should give you an output just like this one

> eth0 Link encap:Ethernet Hardware Adresse 00:13:77:04:cd:26
UP BROADCAST MULTICAST MTU:1500 Metrik:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 Sendewarteschlangenlänge:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Basisadresse:0x6000 Speicher:d2800000-d2820000

lo Link encap:Lokale Schleife
inet Adresse:127.0.0.1 Maske:255.0.0.0
inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
UP LOOPBACK RUNNING MTU:16436 Metrik:1
RX packets:992 errors:0 dropped:0 overruns:0 frame:0
TX packets:992 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 Sendewarteschlangenlänge:0
RX bytes:30392 (29.6 KB) TX bytes:30392 (29.6 KB)

wlan0 Link encap:Ethernet Hardware Adresse 00:13:02:0f:83:56
inet Adresse:192.168.18.143 Bcast:192.168.18.255 Maske:255.255.255.0
inet6-Adresse: fe80::213:2ff:fe0f:8356/64 Gültigkeitsbereich:Verbindung
UP BROADCAST RUNNING MULTICAST MTU:1500 Metrik:1
RX packets:237037 errors:0 dropped:0 overruns:0 frame:0
TX packets:200628 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 Sendewarteschlangenlänge:1000
RX bytes:208782489 (199.1 MB) TX bytes:22525126 (21.4 MB)

your output can differ quite a bit, but the imporant information is just the bold bit. Thise four numbers are the address of the machine (do not use the 127.0.0.1 address - there must always be a second).
so, in my case the address would be 192.168.18.143.

3.) Access the other computer
Now, when you want to access a computer from the other, go to places -> connection to server. 
 - Choose SSH as the at the service type
 - the server is the IP of the other computer (the one you want to access)
 - the port can be left blank (this means it assumes port 22)
 - the folder you should put in is /home - but you can leave it blank
 - the username *must* be specified. This would be the user you use to log into the other computer.
 - also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser 

Most imporant - click ok :)
you will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine. 

I hope that was simple enough - like i said, i haven't done simple for a long time :)

hope it helps.

---

### Post by Volume on 2009-07-28
Great HOWTO mapes12!  That worked quite well.  Thank you very much for your post

Steve

---

