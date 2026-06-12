---
title: "Connection Sharing in NetworkManager"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by xnevermore on 2009-01-29
So, apparently NetworkManager 0.7 now includes [support for Internet Connection Sharing]("http://blogs.gnome.org/dcbw/2008/12/15/everyone-gets-a-networkmanager/"). An example of sharing an ethernet connection through wireless is demo'd [here]("http://magazine.redhat.com/2008/10/16/video-fedora-10-connection-sharing/").
A few questions:
[LIST]
[*]How do you do it the other way around? (i.e. sharing a wireless connection through ethernet). I assume it has something to do with creating a new wired connection in NM and then using the "Shared to other computers" option in IPv4 settings, but then what? 
[*]How do you set up DHCP? 
[*]How do you pick which wireless connection is shared? 
[*]Why isn't this documented anywhere? 
[*]In fact, why isn't NetworkManager really documented at all? 
[*]Come to think of it, what does the "Link-local only" setting do?
[/LIST]

So many questions, so few answers...

---

### Post by Post Monkeh on 2009-01-29
read my post [http://ubuntuforums.org/showthread.php?t=1050695]("http://ubuntuforums.org/showthread.php?t=1050695") there.

those settings allowed me to share my laptop's wireless link to my router with my desktop via lan.

i think i also used firestarter to configure my firewall to allow the connection, but that's pretty much self explanitory during the install, just connect the network adapters up before your first run of firestarter and make sure you select the right adapters for your local network and internet connected device

---

### Post by xnevermore on 2009-01-29
Thank you for the workaround. However, I'm really trying to figure out how to do this natively in NetworkManager, because it looks like it DOES have ICS builtin, but its undocumented, so I can't figure out how it works.

---

### Post by Post Monkeh on 2009-01-29
when i say i had to use firestarter, i only have to use it once to configure the firewall, i haven't loaded it since, once it's set up that's it - every time the laptop loads everything just connects immediately

---

### Post by xnevermore on 2009-01-29
Right, but I like the idea of having NetworkManager... well... manage my network settings. I *could* use system config files to work around NM's limitations, but why should I have to when NM is supposed to have this support builtin? What if I don't want eth0 to always have a static IP, but only in some situations? I would have to edit /etc/network/interfaces for every situation.

---

