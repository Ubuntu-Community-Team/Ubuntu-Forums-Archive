---
title: "problems with Hauppauge pvr500"
date: 2007-11-19
forum: Mythbuntu
---

### Post by kingjos on 2007-11-19
Has anyone out their ever heard or know anything about using Hauppauge pvr500 tuner card that causes the system to reboot after about 10 seconds of using it?

---

### Post by foxbuntu on 2007-11-19
How do you know its the card? Please provide more details

---

### Post by kingjos on 2007-11-19
I know its the card because the system will only reboot when I'm watching live TV.  It also reboots ( but not as frequently as Live tv) when  I have scheduled recordings in the system.  Also, from the couple of fragmented recordings I did get ( due to the system rebooting) I could watch those recordings as much and as many times as i wanted without the system rebooting.  I would be happy to post the contents from log file from my system if someone could help me out on witch log files I should be looking in?  I'm a noob by the way :-)

Thanks for all the help..

---

### Post by ickyb0d on 2007-11-19
I've had this card for almost a year now and have not experienced anything as harsh as the system rebooting.  It also might help to know if you have the phillips (old) or samsung (new) tuners on it.  Or perhaps this might have to do with how you have your video capture devices configured?

---

### Post by kingjos on 2007-11-19
When I configured my tuners in mythtv All I did was add the /dev/video0  device first into mythtv-setup and then /dev/video1 as the second video device.  I have done some google searches on the topic and found a couple of posts talking about how the VIA chipset used on some motherboards might have some incompatibility issues with the IVTV drivers when configured with a pvr500 boaard.  Seeing as how I am using an older AMD based motherboard with a VIA chipset I'm wondering if this could be part of my problem.  Has anyone else had a problem like this in the past?  Also, I some other posts talking about how if some modules for the IVTV drivers are overlapping each other when the Kernel was compiled that this could also cause the system to be unstable and cause a sudden reboot.  Anyone ever heard of anything like this before?

---

### Post by superm1 on 2007-11-19
> **kingjos said:**
> When I configured my tuners in mythtv All I did was add the /dev/video0  device first into mythtv-setup and then /dev/video1 as the second video device.  I have done some google searches on the topic and found a couple of posts talking about how the VIA chipset used on some motherboards might have some incompatibility issues with the IVTV drivers when configured with a pvr500 boaard.  Seeing as how I am using an older AMD based motherboard with a VIA chipset I'm wondering if this could be part of my problem.  Has anyone else had a problem like this in the past?  Also, I some other posts talking about how if some modules for the IVTV drivers are overlapping each other when the Kernel was compiled that this could also cause the system to be unstable and cause a sudden reboot.  Anyone ever heard of anything like this before?
Can you perhaps put this card into another computer to make sure that it won't be a problem with the card itself?  I suspect it to be one.  I haven't heard of anyone with VIA chipset issues for a long long time (but that can still be a possibility too)

---

### Post by kingjos on 2007-11-19
I could try testing it out this weekend on my other desktop this weekend when I get more time.  I was doing some looking around with google and i came across this link.  I'm interested in the part where he talks about motherboards not responding to DMA resets correctly.  I wonder if my motherboard could be having the same kind of problem as this guy was having?  How would I go about finding signs of problems with the IVTV drivers?  Are there log files that I could view that would have messages about IVTV problems or maybe DMA problems with my system?  Also how do I go about figuring out what version of the IVTV drivers my system is using?


[http://www.mythtv.org/wiki/index.php/IVTV](http://www.mythtv.org/wiki/index.php/IVTV)

---

### Post by dougsnell on 2007-11-20
If you have a K8V chipset from Via, I can attest to some difficulties in getting it to work.  I'm trying to remember back that far.

I do remember getting rebooted with an earlier version of "standard" ubuntu  (and K8v), but the latest mythbuntu disk worked with an irregular sound problem (I could fix it by manually changing settings regarding razzing/tinny problems, but rebooting or even waking from sleep mode would bring it back).  I haven't recently tried booting to regular ubuntu on that machine, but many months ago I couldn't even successfully launch the installation off a LiveCD.

---

