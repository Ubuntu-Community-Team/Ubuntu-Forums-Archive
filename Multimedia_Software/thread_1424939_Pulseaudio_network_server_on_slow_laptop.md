---
title: "Pulseaudio network server on slow laptop"
date: 2010-03-08
forum: Multimedia Software
---

### Post by AcIDx0 on 2010-03-08
Hi all,

I have got an ancient COMPAQ Presario 1247 laptop which has an AMD K6 3DNow! processor and (i think) 64Mb ram. It has a DLink wifi g pcmcia card for networking.

I decided to turn it into a networked sound card i.e. run dedicated pulseaudio server to accept connections from the network.

I installed Debian lenny on it, with pulsaudio (0.9.10), avahi and alsa packages, and configured everything.

When I use paplay to play a local file, the sound is not choppy and everything plays fine.

When I stream sound from another computer - the playback is choppy. I googled and found several guides on tuning the values in /etc/pulse/daemon.conf but those did not help.

Is there anything to do, or is this machine just too old for that? If it is too old, will adding another 64mb ram really help?

Thank you.

---

### Post by AcIDx0 on 2010-03-12
Bump. Really? nobody knows? I googled minimal requirements for pulseaudio server, but the pages seem to talk about packages, and not hardware. The audio plays fine when it's local, so the problem is with streaming. 

Once, I have installed same configuration on a desktop PIII with 256MB ram, and it was a wired connection. This worked fine. 

Anyone has any insights on how I could make the system not skip the sound?

Thanks.

---

### Post by markbuntu on 2010-03-13
Run top and see if maybe something, like the wifi, is hogging the cpu or ram. That is not very much ram, it can easily get filled up by the wifi or pulseaudio buffers not to mention the kernel or xorg.

---

### Post by me13221 on 2010-03-17
> **AcIDx0 said:**
> Hi all,

I have got an ancient COMPAQ Presario 1247 laptop which has an AMD K6 3DNow! processor and (i think) 64Mb ram. It has a DLink wifi g pcmcia card for networking.

I decided to turn it into a networked sound card i.e. run dedicated pulseaudio server to accept connections from the network.

I installed Debian lenny on it, with pulsaudio (0.9.10), avahi and alsa packages, and configured everything.

When I use paplay to play a local file, the sound is not choppy and everything plays fine.

When I stream sound from another computer - the playback is choppy. I googled and found several guides on tuning the values in /etc/pulse/daemon.conf but those did not help.

Is there anything to do, or is this machine just too old for that? If it is too old, will adding another 64mb ram really help?

Thank you.

Would you mind explaining how you got the system set up?  I would like to stream audio from one device to another running a pulseaudio server but I don't know how.

Also, it doesn't seem like any computer (less than 15 years old) could be "too slow" to play sound-- it seems more likely to me that you have a bad network connection.  I know my laptop (a Lenovo x200 - the saddest heir to the great Thinkpad lineage ever built) will simply crap out on wi-fi for seconds at a time.  

Does the problem go away on a wired configuration?

---

### Post by AcIDx0 on 2010-04-14
> **me13221 said:**
> Would you mind explaining how you got the system set up?  I would like to stream audio from one device to another running a pulseaudio server but I don't know how.

Also, it doesn't seem like any computer (less than 15 years old) could be "too slow" to play sound-- it seems more likely to me that you have a bad network connection.  I know my laptop (a Lenovo x200 - the saddest heir to the great Thinkpad lineage ever built) will simply crap out on wi-fi for seconds at a time.  

Does the problem go away on a wired configuration?

me13221,

There are hundreds of howtos. Here, start by doing [this]("http://tinyurl.com/y3v7lmq").

---

### Post by AcIDx0 on 2010-04-15
> **markbuntu said:**
> Run top and see if maybe something, like the wifi, is hogging the cpu or ram. That is not very much ram, it can easily get filled up by the wifi or pulseaudio buffers not to mention the kernel or xorg.

Thanks for the great and so obvious idea which I did not think of (at least I googled everything I could think of)

Anyway, I discovered CPU was ~1% at rest, and about 50% at work occupied mostly by pulseaudio. However, there is about 1mb :) of memory left free. I guess I need to try to add new memory to the laptop. It seems like pulseaudio is really on the edge. 

Do you think trying a wired connection will use less CPU, and thus work better?

---

### Post by AcIDx0 on 2010-04-15
Hi all,

So I added another 128mb of ram. Now up to 160. There are ~90mb of ram free at all times. The audio is still unbearably choppy.

Still have to try wired connection (don't have a wired PCMCIA, need to borrow from somewhere)

Anything else I can do? 

The audio is really choppy for no apparent reason.

Thanks.

---

### Post by markbuntu on 2010-04-16
There can be a number of problems. Stop pulseaudio and run it from a terminal like this

pulseaudio -vvvv

This will give you a lot of messages from pulseaudio about what it is doing and maybe help you figure out what is going on.

---

### Post by AcIDx0 on 2010-04-17
There are no apparent error messages when I do that. Except "Memory block too large for pool"

But they come out on startup, and not during play....


I played with the buffer size, namely 
default-fragments = 
default-fragment-size-msec =

and set them to bigger values. It became better, but still the interruptions are very noticeable. 

I googled the buffer size issue extensively, but did not come to a solution. I still have not tried a wired card - I don't know where to get one. I don't want to buy only to try.

---

### Post by AcIDx0 on 2010-05-29
Well, got a wired NIC for this, but still no banana. I guess this processor is too slow to do networking and sound together, although it is really strange.

Does anyone have any suggestions on how to fix it?

I think I am going to turn this thing into a picture frame and get a faster laptop for pulseaudio server.

---

### Post by DerSkw on 2010-08-27
Hey AcIDx0,

I just found this thread and I'd like to know if you've made any progress.
I'd also like to set up an old laptop as a pulseaudio server for my new apartment and I'm trying to find out the minimal resources needed to let it run ;)

---

### Post by AcIDx0 on 2010-08-27
Unfortunately, no banana.

That computer was OK to play sound with pulseaudio, but not streaming and playing. In my experience you need at least PIII 700mhz with 0.5G RAM, and a wired NIC. 

With the above minimal config. you will still need to enlarge the buffers to max and have a delay. Consider adding more memory and a bit faster proc. Old P4 should do fine.

Hope this helps.

---

### Post by AcIDx0 on 2012-01-25
Thanks for reviving this thread. I feel like the information here about the minimal requirements should be added to some sort of howto. Anyway, I haven't tried moving pulseaudio to a ramdisk, but all in all pulseaudio server is a pretty heavy software. Even with two Core 2 Duo machines, it did not work properly until I switched to wired network.

---

