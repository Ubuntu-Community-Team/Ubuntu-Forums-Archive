---
title: "setting up network for PS3 media server"
date: 2011-05-23
forum: Multimedia Software
---

### Post by Sylos on 2011-05-23
Hello and thanks for looking.

I have a PS3 that I am looking to connect to my main PC to watch videos, listen to music etc. I am planning to use mediatomb as the media sever as this seems a popular choice. I just have some questions regarding how to set up the network (I've never done any network set up or admin before).

SO....

1. I will soon be downgrading my internet connection package to one with a download limit so I dont want anything being transmitted through this. I assume any info I transfer between the machines will simply go PC > router > PS3 and therfore not eat up my precious download qouta. Yes?

2. Im a little concerned regarding the security implications of allowing something to browse my HDD on the PC through the same port as my connection to the outside world (ethernet cable). Is this a genuine possible issue or my ill informed paranoia?

3. Given my belief on point 2, Im wondering if I could install a second ethernet card (or USB dongle - not sure yet) to connect to the router using a different port for a dedicated connection for mediatomb. That way I would be able to have relative safety of knowing that the permitted connection is only used by the PS3 - not the internet at large. Or... maybe it will be no different as the connection still goes through the router which is connected to the outside world and could therefore still be hijacked. I dont know - im confused.

Please excuse me if these are foolish questions but I really dont understand what I am doing.

and PS - I do see the irony in worrying about the security issue for the connection through the router when PSN got hacked like log recently. :)

Any input welcome...

Cheers

---

### Post by backu on 2011-05-23
I have something similar setup on my network.. got 2 ps3's and using Playstation Media Server (pms-linux) to do the transcoding and what not. It's the only server I've found that works correctly to do a media server to the PS3 for Music and Movies. PMS lets you limit what directories are available to the 'browser'. As far as network concerns, not sure as I have my computers and PS3's behind a openSuSE firewall/router machine.

---

### Post by Sylos on 2011-05-25
Thanks for the reply. Looks like I will give pms a try first and see how it works out.

Researching this it appears I will need an ethernet crossover cable to link the two together. Is that correct?

Also, any ideas on the other questions?

Cheers

---

### Post by aeiah on 2011-05-25
1. your router realises the data is going from machine A to machine B and so doesn't even need an internet connection, so no, it will not affect your internet bandwidth usage

2. by default, ports should be closed to the outside world. id be surprised if this isnt the case with your router unless you've changed something. 

if you wanted to let the outside world connect to your media share (which i presume you dont) you would have to forward the appropriate port (say, 49152) on your router. you'd tell your router "any request from the outside world on port 49152 gets redirected to machine A". by default, if a request from the outside world hits your router, it will just ignore it - which is what you want in this case.

3. you could install another ethernet card or usb card, but there is little point in this situation. you wouldn't really improve transfer speed or security.

---

### Post by Sylos on 2011-05-25
Thanks for the post aeiah.

So it appears that I can simply connect the ethernet of the ps3 to the router and then that can be fed into the existing cable connection from router to PC.

Could you point me in the direction of some information on how a newb person would achieve this?

Thanks

---

### Post by Sylos on 2011-05-29
Ok. So following the advice above I am now trying to use my router to connect the ps3 and my PC using the PMS server (successfully installed). Predictably I have a problem.....

I have a Bt Home Hub and have been trying to set it up to allow the ps3 to connect to the PC. Unfortunately I cant seem to get it to work. The list of Supported Applications does not contain PMS or anything I can see as being similar. I tried creating my own but have no idea what port range to enter etc. I am, therefore, stuck.

Can anyone help me out with how to do this?

Thanks

---

### Post by Sylos on 2011-05-29
Well .... after turning off my firewall I managed to get it to find my PS3 and transfer some media. BUT...after changing my shared folders etc and then restarting the server I have ended up back at the PS3 Not found problem. Same settings - nothing different that I can see. WTH?

Any insights?

---

### Post by Sylos on 2011-05-29
Another reboot seems to have fettled it. Weird!

I still dont understand how my router settings can be correct but if it works it works. If anyone fancies giving an idiot a little lesson it would be welcome.

Cheers

---

### Post by Sylos on 2011-06-02
OK. So it appears that IPBLOCK is preventing me from gaining a connection. If I stop IPblock and connect then it will connect ok but not when IPBlock is running. Oddly though, I can then enable IPBlock and it doesnt prevent information from being sent to the PS3.

Im thinkning I need to whitelist the PS3 connection in IPBlock (as I already have done with Firestarter). I have set my router up to give my PS3 a constant IP address and I have tried entering that into the GUI for whitelisting but it doesnt seem to work - the issue persists. Can anyone tell me how to successfully whitelist it?

Many thanks

---

