---
title: "DHCP client and host."
date: 2005-12-26
forum: Networking &amp; Wireless
---

### Post by Connollyir on 2005-12-26
I want to connect two computers with a crossover cable and use one as a ftp/streaming media server. I am going to configure the DHCP server on the computer with a monitor and thats all well and good but do I have to do anything special on the client's end? 

Its only going to be a 2 computer deal off the LAN or internet so I want to set it up so that the client can only have one ip - a static ip. do I just limit the ip address assignements in the server conf file, or is there another way to do it?


Thanks


-Ian

---

### Post by Koybe on 2005-12-27
I'm just wondering why using dhcp then? You can simply put your to computers with a static ip in the same network ;)

---

### Post by Connollyir on 2005-12-27
[QUOTE=Koybe]I'm just wondering why using dhcp then? You can simply put your to computers with a static ip in the same network ;)[/QUOTE]

There isn't going to be a newtwork to put the computers on, its going to strictly be a crossover between the two nothing more. One box is my dektop, which is in a 4u case in a rack with the rest of my audio gear (theres a lot and I wanted to keep it together), and I made a media bin out of some spare hard disks and a 2u case because it fit. I need to make sure the ip for that computer wont change because there is no monitor out on it and I am going to be depending on access to the files in it. I thought that if i set up a DHCP server in my desktop it could reliably give that computer a static address, but everything I've read about DHCP servers is based on using them for multiple users or web hosting and doesn't show how to configure one the way I want it.


Any ideas?

-Ian

---

### Post by Koybe on 2005-12-27
I'm still thinking as before. Even if it's a "blackout computer", I can't see any reason for you to put un dhcp server.

Configure both PC using a static ip, here is the way to do it :

```

sudo /etc/network/interfaces
  auto eth0 
  iface eth0 inet static 
    address 192.168.1.10
    netmask 255.255.255.0
    network 192.168.1.0
```

Restart your network service and check it with ifconfig
```
/etc/init.d/networking restart
ifconfig
```

If I'm right, all you need is accessing the "audio pc" as a jukebox. So I don't understand why you absolutely want a dhcp server. You're making you task more complicated then it looks ;)

Anyway it's just my opinion.

---

### Post by Connollyir on 2005-12-27
[QUOTE=Koybe]I'm still thinking as before. Even if it's a "blackout computer", I can't see any reason for you to put un dhcp server.

Configure both PC using a static ip, here is the way to do it :

```

sudo /etc/network/interfaces
  auto eth0 
  iface eth0 inet static 
    address 192.168.1.10
    netmask 255.255.255.0
    network 192.168.1.0
```

Restart your network service and check it with ifconfig
```
/etc/init.d/networking restart
ifconfig
```

If I'm right, all you need is accessing the "audio pc" as a jukebox. So I don't understand why you absolutely want a dhcp server. You're making you task more complicated then it looks ;)

Anyway it's just my opinion.[/QUOTE]


I tried changing the network interfaces file to that same setup before but it never stuck, as in after rebooting it wouldn't work. Would that be because my router overrode it (I originally configured the hard disk and transfered files with it in a different computer that was networked)?

---

### Post by Koybe on 2005-12-27
Could you copy/paste you interfaces file? It shouldn't be overwritten if you don't use dhcp.

---

### Post by Connollyir on 2005-12-27
[QUOTE=Koybe]Could you copy/paste you interfaces file? It shouldn't be overwritten if you don't use dhcp.[/QUOTE]

That depends on how long you are going to be around... I just transfered the drive into its future home (under the assumption I would be using DHCP and wouldn't have to worry about the address) and I am recieving boot errors which I am convinced are coming from the lack of graphics card. At any rate, I need to take the mobo out and mount it on something nonconductive to set up the ip and fix the bios alarms.

---

### Post by Koybe on 2005-12-27
OK. Nevermind i'm looking quite often the forum and I think I'm not the only one who can help you, so take your time. Once you'll have it working nicely come back for help if needed ;)

---

### Post by Connollyir on 2005-12-27
[QUOTE=Koybe]OK. Nevermind i'm looking quite often the forum and I think I'm not the only one who can help you, so take your time. Once you'll have it working nicely come back for help if needed ;)[/QUOTE]

Well here it is for whomever or whenever you get back:

my /etc/network/interfaces file originally contained:

# The loopback network interface
auto lo
iface lo inet loopback

and I changed it to what you wrote. After I do that and restart the networking hardware I get a (*Reconfiguring network interfaces....          [fail]). When I enter ifconfig I don't recieve anything, none of the usual network information ITS BLANK. I tried to force an ip using sudo ifconfig eth0 192.168.0.1, after which I tried to ssh into the system but it said: 

e@IansDreamMachine:~$ ssh e@192.168.0.10
ssh: connect to host 192.168.0.10 port 22: No route to host
e@IansDreamMachine:~$

Its like it doesn't see my network hardware that I have installed - I tried using the nic that I did the install with and the onboard chip but i got the same results with both.

?

-Ian

---

### Post by Connollyir on 2005-12-27
Ok I did get it to work.... I changed pci slots and realized that I was putting the directions you gave me under the loopback device and not the primary device - which was in fact eth0. So it works and I did transfer some files. BUT HERES THE KICKER > now I have no wireless which is where my internet is coming from :???: . 

I'm checking out the configuration of my computer as we speak but i really don't know what I'm looking for....

-Ian

---

### Post by Koybe on 2005-12-27
The loopback interface should still be on.

You whole file should look like this :

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0 
iface eth0 inet static 
    address 192.168.1.10
    netmask 255.255.255.0
    network 192.168.1.0

If ifconfig is not returning anything, you won't be able to ssh into the computer. 


And What if you do this :
```
sudo dmesg | grep eth
```

---

### Post by Koybe on 2005-12-27
Ok I did not see your previous post. Maybe at the same time as mine ;)
For your wireless network, you'll need to have another interface... so you'll have lo, eth0 and... another one. 

But there i can't help you I have no expereince with wireless card. Try looking for some tutorial, or create another topic asking for wireless help :)

---

### Post by Connollyir on 2005-12-27
[QUOTE=Koybe]Ok I did not see your previous post. Maybe at the same time as mine ;)
For your wireless network, you'll need to have another interface... so you'll have lo, eth0 and... another one. 

But there i can't help you I have no expereince with wireless card. Try looking for some tutorial, or create another topic asking for wireless help :)[/QUOTE]

We might be ok. I got the ip to stick to the server and I think i just reconfigured my wireless to take precedence over the ethernet connection. I can ping both and get results, but the weird thing is I can no longer ssh into the server like I did when it was on the LAN. In fact I can't connect to it for anything. I am going to start a new thread under a more accurate title.

Thanks a bunch.

)an

---

