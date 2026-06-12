---
title: "Unable to Install Drivers for Netgear WG311v2 Wireless NIC"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by sgalland on 2006-06-14
Greetings,

I am inquiring on how to install the drivers for a Netgear WG311v2 Wireless NIC. I was able to download NDISWRAPPER and have tried several tutorials, only to have problems installing various utilities and haven't even come across a suitable INF file. 

Also another issue I have that is possibly related is my connection to my router via a regular NIC keeps dropping the connection but I can reconnect when I open the networking application and close it.

Any help is appreciated!

---

### Post by noname101 on 2006-06-14
Did you search?
[http://ubuntuforums.org/showthread.php?t=196069](http://ubuntuforums.org/showthread.php?t=196069)
If you need more help then my post on there, then reply here and i'll try to help. I'm using the same card, so the instructions there should work.

---

### Post by sgalland on 2006-06-14
Thanks for the reply!

I tried all the commands up until sudo modprobe ndiswrapper and I got the following error:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

Every other command worked like a *charm*.

---

### Post by noname101 on 2006-06-14
Did you compile and install ndiswrapper yourself? Or are you using the prebuilt module?

---

### Post by sgalland on 2006-06-14
Its a prebuilt... also I rebooted any now my wireless in networking is gone.

---

### Post by noname101 on 2006-06-14
Well since you rebooted. Does sudo modprobe ndiswrapper work now?
Also what does ndiswrapper -l display if it doesn't?

---

### Post by sgalland on 2006-06-14
Thanks for helping me. It did fail again and here is the results it dumped about drivers:

Installed ndis drivers:
pciid   invalid driver!

Oh... wait... I tried to do a reinstall "just in case I am being an idiot" and I got the driver to install for TNET1130.INF. Woot! I ran the modprobe again on ndiswrapper and boom it worked. Now everything is working right... this is odd, I have done a lot of regular nic configs and haven't had this much trouble then your directions pointed me in the right direction and linux didn't like them, now linux is loving them up... wierd.

But so far all is well, I hope it says that way! :KS

---

### Post by sgalland on 2006-06-14
Another question regarding this issue, I am trying to go to google.com in Firebox and other websites and they will not load. However I can browse any ubuntu site and forums just fine and the internet is fast on these pages. Any reason why this would occur? Also Gaim and other internet applications can't detect their servers however if I go back to networking, load it, and close it, it all works again. Wierd eh?

---

### Post by noname101 on 2006-06-14
There could be something wrong with /etc/resolv.conf. Does it have the same name servers as your router?

---

### Post by sgalland on 2006-06-14
This is what appears in resolve.conf:
search domain.actdsltmp
nameserver 205.171.3.65

I am missing the second nameserver 205.171.2.65 if that matters.

---

### Post by sgalland on 2006-06-14
I also just noticed that whenever I go into networking and look at the DNS servers there it adds a IP on my network of 192.168.0.3 which doesn't go to anything. If I delete it and close network it works for a while and then the problem comes back after about ten minutes or so. That would explain the seemingly "dropped" connection issue.

Note: I rebooted the system and it put back the local IP of 192.168.0.3 and deleted my addition of my other nameserver. How do I stop it from manually doing that?

---

### Post by sgalland on 2006-06-14
I did a search in the forums and it said something about editing a resolve.conf/<some other file that starts with a b> and I tried to edit it and save it as per instructions with the two nameservers but it said the file doesn't exist when saving. Any other idea's?

---

### Post by noname101 on 2006-06-14
If you give it a static ip address and specify the dns servers. Then maybe it won't automatically update the dns servers.

---

### Post by sgalland on 2006-06-15
Dumb question, is my gateway my internal router IP?

---

### Post by noname101 on 2006-06-15
Your gateway is most likely the router's ip address. So for me it'd be 192.168.1.1.

---

