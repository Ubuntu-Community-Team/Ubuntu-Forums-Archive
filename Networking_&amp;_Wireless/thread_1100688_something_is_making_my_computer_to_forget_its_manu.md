---
title: "something is making my computer to forget its manual ip"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by Meow27 on 2009-03-19
hi, im trying to set up a local homepage server for my network, i'm using ubuntu 8.10 but i have encountered a problem of which, i don't know the cause.

so to the topic, this computer forgets the manual if i assign it after i restart it (network manager-gnome). i cant figure out the cause, i need to use this computer as i remote desktop it. 

is there a .conf file that handles static ips that i can assign to it. i really don't like the fact that it keeps forgetting the ip that its supposed to have


thanks in advance

---

### Post by Meow27 on 2009-03-20
bump. c mon just tell me if there is a conf file i could use.

---

### Post by Iowan on 2009-03-20
Network Manager keeps its files in /etc/NetworkManager. Older versions (like I'm using) used /etc/network/interfaces file. There are a few How-To's around for setting up static address... I'll see if I can find some.

---

### Post by Meow27 on 2009-03-22
bump :/

---

### Post by jbrevik on 2009-03-22
Post your hardware specs.

---

### Post by chili555 on 2009-03-22
If this is a home server, you don't want or need Network Manager. You aren't planning to waltz the server down to the library or the coffee shop and connect to their network, are you? I suggest removing Network Manager and dhcpcd using Synaptic. Then amend */etc/network/interfaces* to look like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
```Substitute your details as needed. Be sure to select an IP address outside the range of addresses used by the router for DHCP. If it is set to start at 192.168.1.1 and assign up to 16 addresses for DHCP, your static address should be x.17 or higher. Reboot and enjoy!

---

### Post by rplantz on 2009-03-22
> **Meow27 said:**
> hi, im trying to set up a local homepage server for my network, i'm using ubuntu 8.10 but i have encountered a problem of which, i don't know the cause.

so to the topic, this computer forgets the manual if i assign it after i restart it (network manager-gnome). i cant figure out the cause, i need to use this computer as i remote desktop it. 

is there a .conf file that handles static ips that i can assign to it. i really don't like the fact that it keeps forgetting the ip that its supposed to have


thanks in advance
I was trying to do the same thing as you. I got it to the point where it would hang for 5 minutes trying to configure the network interfaces. This sent me to the thread, [http://ubuntuforums.org/showthread.php?t=1101468&page=3](http://ubuntuforums.org/showthread.php?t=1101468&page=3). In post #22 Detonate has posted a howto that worked for me.

I also noted in the thread (#7) that in the Synaptic comments about NetworkManager it says "NetworkManager ... is intended only for the desktop use-case, and is not intended for usage on servers."

---

### Post by Meow27 on 2009-03-23
thanks you guys for the help

(post #6 was exactly what i was looking for)

[/solved]

---

### Post by ZefQ on 2009-03-23
i had the same problem yesterday, so i thought i would add a solution done in desktop. i had to go system->settings->network and add a new connection and configure the new connection with the right settings. 

that worked for me at least

---

### Post by Aped on 2009-05-24
Would this work on a wireless network too? I'm leery of just straight-up deleting Network Manager... sounds like asking for a whole asston of frustration down the road.

---

### Post by chili555 on 2009-05-25
> **Aped said:**
> Would this work on a wireless network too? I'm leery of just straight-up deleting Network Manager... sounds like asking for a whole asston of frustration down the road.Perfectly well. The laptop I am answering from now uses a static IP address and had Network Manager removed the very first thing after installation. In my opinion, and mine only, NM is a hindrance rather than a help. YMMV.

If you decide to undertake this, we will be glad to help you if you run into a snag.

---

### Post by Aped on 2009-05-25
> **chili555 said:**
> Perfectly well. The laptop I am answering from now uses a static IP address and had Network Manager removed the very first thing after installation. In my opinion, and mine only, NM is a hindrance rather than a help. YMMV.

If you decide to undertake this, we will be glad to help you if you run into a snag.

I just told my router to always assign certain mac addy's specific IPs, what benefits would I gain from doing it via the computer? I'm pretty lazy when it comes to things that are already working (sort of) but I would love to learn a little bit about how non-NM would work. Is there a guide to this somewhere?

My ath9k is pretty buggy as it is though, I feel like the tenuous grasp that it has on my 11G signal (it doesnt even recognize the draft-N) might be jeopardized by too much tampering...

---

