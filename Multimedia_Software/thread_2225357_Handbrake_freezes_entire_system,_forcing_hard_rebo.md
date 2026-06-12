---
title: "Handbrake freezes entire system, forcing hard reboot"
date: 2014-05-21
forum: Multimedia Software
---

### Post by fighterhayabusa on 2014-05-21
I'm running a fully updated Xubuntu 14.04 system and I'm having problems with Handbrake.

When I start to encode a ripped DVD (or anything else for that matter, transcoding from FLV to MKV for example) with Handbrake it takes about half a minute or less and then my entire system freezes and locks up. I can't move the mouse, keyboard is not responsive and I can't log in via SSH from another computer either. Total freeze. I have to force a hard reboot to get back in.

I have tried both the version of Handbrake in the official repos and the latest version from the developers. Same result. The system freezes every time.

Am I the only one experiencing these problems? In any case I really need help to troubleshoot this since I have no idea where to start.

This is my hardware (if that helps):

CPU: Intel Core i7-4770K 3,5GHz Socket 1150
Memory: KINGSTON 16GB 1600MHZ DDR3 CL9 DIMM (2X8GB) XMP HYPERX BEAST
Motherboard: GIGABYTE GA-Z87X-OC Z87 S-1150 ATX
Graphics: ASUS GEFORCE GTX 660 OC 2GB

---

### Post by mdalacu on 2014-05-21
Video encoding is a very CPU intensive task, so check CPU temperature. (sudo apt-get install lm-sensors && watch sensors).

---

### Post by monkeybrain20122 on 2014-05-21
I experienced that as well, it seems to be some kind of gtk bug. Problem solved after disabling the tray icon from handbrake's preferences (the pineapple thingy on the panel that shows you progess)

---

### Post by fighterhayabusa on 2014-05-22
> **monkeybrain20122 said:**
> I experienced that as well, it seems to be some kind of gtk bug. Problem solved after disabling the tray icon from handbrake's preferences (the pineapple thingy on the panel that shows you progess)

Thanks, I tried that and first I thought it was working. I encoded two DVDs without a hitch but when I started on a third one the computer froze about halfway through. Any ideas on how to trouble-shoot this? It is really very annoying.

---

### Post by fighterhayabusa on 2014-05-23
So it seems that it's not Handbrake that is the problem. Last night I had the system freeze up while using Ogmrip (to do what I usually do with Handbrake) so I started looking into the CPU-situation, and I'm a bit baffled by my findings.

It turns out that my CPU is running a bit hot. When running a test job in Handbrake it tops out at ~100 degrees Celsius. However, during this particular test run the system didn't freeze but finished the encoding fine.

I then tried running the program stress (apt-get install stress) to really give it to the CPU. It ran for quite a while with all cores at 95-100 degrees Celsius without the system freezing.

After I let the CPU cool down I ran another test run with Handbrake and this time the system froze and I had to do a hard reboot.

After rebooting I went into the BIOS and "underclocked" the CPU to 2GHz, instead of 3.9GHz which it was running at (according to the BIOS). After underclocking I've not had any trouble with the system hanging. I queued up 8 previously DVDs for encoding in Handbrake and it went through them all without a hitch.

So apparently I'm having some sort of CPU issues but it doesn't seem to have anything to do with temperature? I'm really at a loss here and not sure how to proceed with the trouble-shooting. Any help would be appreciated.

(Btw, I will still look into the heat situation since it's not good to have a CPU running hot. Probably get some better cooling in the next couple of days)

---

