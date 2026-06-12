---
title: "Dumbdown to 10baseT"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by werDZiPiLE on 2008-12-03
I know this sounds weird but for some reason... and i just believe its just the cabling but thats not really the points... I need to dumbdown my network settings on Ubuntu 8.10 to 10baseT. I know im kinda new to Ubuntu but know i need to do stuff in the command line aka terminal :P .. just wondering what the commands were?

---

### Post by puppywhacker on 2008-12-03
mii-tool eth1 -F 10baseT-HD

---

### Post by werDZiPiLE on 2008-12-08
i get ...

```
usage: mii-tool [-VvRrwl] [-A media,... | -F media] [interface ..]
    -V, --version               display version information
    -v, --verbose               more verbose output
    -R, --reset                 rest MII to poweron state
    -r, --restart               restart autonegotiation
    -w, --watch                 monitor for link status changes
    -l, --log                   with -w, write events to syslog
    -A, --advertise=media,...   for specified media technology
media: 1000baseTx-HD, 1ooobaseTx-FD,
       100baseT4, 100baseTx-HD, 1oobaseTx-FD,
       100baseTx-HD, 100baseTx-FD
       (to advertise both HD and FD) 1000bastTx, 100baseTx, 10baseT
```

so what does that mean? .. still cant connect :P

---

### Post by gTinker on 2008-12-08
[QUOTE=werDZiPiLE]I know this sounds weird but for some reason... and i just believe its just the cabling but thats not really the points... I need to dumbdown my network settings on Ubuntu 8.10 to 10baseT. I know im kinda new to Ubuntu but know i need to do stuff in the command line aka terminal :P .. just wondering what the commands were?[/QUOTE]

You shouldn't need to "dumbdown" anything. A network card runs at the speed it and/or the network is capable of. 

There is a possibility that you have mis-diagnosed the issue that you are trying to correct. Did you see a lot of collisions, is that why you decided? Otherwise, tell us more about any error messages you received or more about the network you are trying to connect to, all we know so far is that you can't connect, you haven't mentioned how you are trying to connect or if your network interface is "up" or really anything to get an idea of what might be happening.

Perhaps start with the results of the command, ifconfig -a.

---

### Post by werDZiPiLE on 2008-12-08
it was linksys that told me its 10baseT just because I use a router. i believe im using plane old cat5. and im using onboard NIC. thing is this problem doesnt just occurr on my desktop... it actually happends to my desktop, my dads, my moms, everyone in the house that doesnt use wireless.

from the ifconfig -a ....

```

eth0    Link encap:Ethernet HWaddr 00:508d:e9:bf:6c
        inet6 addr: fe80::250:8dff:fee9:bf6c/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST MUT:1500 Metric:1
        RX packets:577 errors:1381 dropped:0 overruns:0 frame:0
        TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:53410 (53.4 KB) TX bytes:3888 (3.8 KB)
        Interrupt:18 Base address:0x8000

eth1    Link encap:Ethernet HWaddr ff:7f:ff:7f:ff
        BROADCAST MULTICAST MUT:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
        Interrupt:17 Base address:0xa000

lo      Link encap:Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:510 errors:0 dropped:0 overruns:0 frame:0
        TX packets:510 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:32368 (32.34 KB) TX bytes:32368 (32.3 KB)

pan0    Link encap:Ethernet HWaddr e6:1f:93:40:35:b3
        BROADCAST MULTICAST MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```

---

### Post by jonobr on 2008-12-08
Hello


10baseT means that you want to use twisted pair (the T) using a baseband signal (base) at a speed of 10mpbs (the 10)

Most devices used in the home would be 10/100 auto sensing meaning if you plug in your device it will know whether your card is 10 mbps or 100mpbs a will try to support the speed.

Your Cat5 cable no doubt has two RJ45 connectors on either end and connects into your router.

If your linksys service person told you to dumb down your device to 10mbps,
(an odd expression) it almost sounds as if they are saying the linksys you are connecting to is a 10mbps device.
Is that correct?

When other machines connect do they show 100 mpbs or 10?

Which interface are you using on your machine? Eth0 or eth1?

In either case I would expect to see a IP address on your eth and its not there,
Are you using DHCP or static IP addresses?

Does the link light on your router come on when you plug it in?

Is there any id on the router what ports it supports?
It sounds like this may be just misconfiguaration of your network on your desktop side

---

### Post by werDZiPiLE on 2008-12-08
> **jonobr said:**
> Hello


10baseT means that you want to use twisted pair (the T) using a baseband signal (base) at a speed of 10mpbs (the 10)

Most devices used in the home would be 10/100 auto sensing meaning if you plug in your device it will know whether your card is 10 mbps or 100mpbs a will try to support the speed.

Your Cat5 cable no doubt has two RJ45 connectors on either end and connects into your router.

If your linksys service person told you to dumb down your device to 10mbps,
(an odd expression) it almost sounds as if they are saying the linksys you are connecting to is a 10mbps device.
Is that correct?

When other machines connect do they show 100 mpbs or 10?

Which interface are you using on your machine? Eth0 or eth1?

In either case I would expect to see a IP address on your eth and its not there,
Are you using DHCP or static IP addresses?

Does the link light on your router come on when you plug it in?

Is there any id on the router what ports it supports?
It sounds like this may be just misconfiguaration of your network on your desktop side

Im using a WRT160N (wireless N) router.
should be at least 10/100... possible 1000 too just dont have the box around.

when connecting other devices and when they are set to autosence, 100baseT FD, or 100baseT HD the device just wont connect.

ubuntu is trying to run with eth0 or at least thats what shows up on the network settings.

yes the light on my router shows up... cuz im also dual booted with XP (which im on now) and i have to dumb it down to 10mbps to connect.

but i believe linksys told me the 10baseT is the signal im getting from the router... not necessarily my actually speed.

also i have been having/dealing with this problem for the about uhhh the past 8+ years

people have told me its my mobo ethernet drivers but thats wrong cuz its for all my comps... even if i wanted to plug in my laptop directly.. and all my drivers are always up to date.

ohh also the ethernet cable i use is about 25feet in length.. but there is also another cable that runs up to 50feet. but i know from networking that cable signal should be good upto 300feet.

---

### Post by gTinker on 2008-12-09
[QUOTE=werDZiPiLE]Im using a WRT160N (wireless N) router.
should be at least 10/100... possible 1000 too just dont have the box around.[/QUOTE]

[QUOTE=werDZiPiLE]
ubuntu is trying to run with eth0 or at least thats what shows up on the network settings.[/QUOTE]

As the poster jobonr mentioned, from the results you showed us, your interface hasn't obtained an IP address.


[QUOTE=werDZiPiLE]
also i have been having/dealing with this problem for the about uhhh the past 8+ years[/QUOTE]

Well, that is confusing because above you said you have a wireless "N" router and they haven't been around 8 years so what you're saying doesn't track.

---

### Post by werDZiPiLE on 2008-12-09
how do i get an IP with ubuntu then?

the problems been around for 8+ years yes.. had problem with my B router, G router, and still have it with N router. if someone could solve that problem i would name them the smartest person alive. cox cable says its linksys problem, linksys says thats the speed of the router signial, network teacherS say I should work at 100 and dont understand why im even getting the problem. next weekend i might just bit the bullet and rewire the whole house with cat6... well at first downstairs to make sure it fixes it. but ive had no clue on whats wrong and whenever i try to get help on it its always someone elses fault.

---

### Post by werDZiPiLE on 2008-12-10
ok wow is all i have to say... wow... so i was building this new comp for my neighbor... while at the store i decided to get a cat6 cable. had some problems at first with the drivers on the mobo but once i got them all installed i decided to check if i had the net. right away boom i was on google. then checked net settings... AUTO !!!! seems like all along after 8 years i was right... just never did anything about it lol. i am now going to have to rewire the whole house with cat6 now.. but that will have to wait about a whole week... finals are next week :P

---

### Post by jonobr on 2008-12-10
Respectfully,

Im am really lost with this post,

Cat 6 cabling is built to a higher spec then cat 5 and builds in a lot more resilience against things like crosstalk.

I know Cat 6 is backwardly compatible to previous iterations and cat 5 can go up to 1000base (gig) however , using cat 6 to accommodate 10baseT when you had cat 5 and the first works , the other doesn't, 
does not make a whole lot of sense to me unless .

Maybe someone on this thread can explain it to me.

---

### Post by jonobr on 2008-12-15
Hey there,

Recommend you mark this thread solved and post conclusions

Thanks !

---

### Post by werDZiPiLE on 2008-12-16
yeah sorry.. to answer your first question the cat5 cable i was using i guess was rated for 10mbps and thats what was causing me to dumbdown my network... i havent installed cat6 throughout my house so that is why i didnt put this as solved yet... also i have finals tomorrow and then next day so i will be installing it the day after finals if its not raining. im pretty sure this IS solved just to my standards it isnt.

---

