---
title: "Is my hardware weak for a media center?"
date: 2012-03-02
forum: Multimedia Software
---

### Post by Jabss on 2012-03-02
Hello,

I wanted a new media center for my living room. Instead of buying a game console or any other closed system I though in buying a small PC with linux. This way, it would be a future-proof, upgradable solution where I could also play some basic games like tuxracer or similar... 

:popcorn:

So I bought the following:
MB Asrock A75M-ITX (with HDMI out - socket **[B][B]FM1**[/B][/B] - uses graphic cards within the processor)
Processor AMD A4-3400 2.7GHz dual core 64 Bits (with ATI RADEON HD6410D inside)
4 GB RAM, from which 512Mb are dedicated to the Video card HD6410D.

I know its not the best HW available but I though it would be enough to play 1080p movies in my phillips 37pfl9603d_10 LCD without any problem... Well, it seems not...

I have installed the latest ubuntu version (64 bit):

> Linux blackpearl 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64.

With the standard setup (I think its the open source drivers), the movie image is kind of acceptable but without any sound. Therefore, I installed the ATI proprietary drivers from the GUI (Settings --> additional drivers). The GUI fetches info from the net and identifies two possible drivers: Release drivers and post-release drivers. I have tried to activate both but only the first one is successful. But even so, this first driver is correctly installed after a reboot and I can use the amdcccle GUI to configure the image settings.

However, whenever playing a HD movie with VLC, the image is not continuous.... How can I say this? It produces some kind of quick hangs. It depends on the movie scene but it stops for a couple of milliseconds around 2 or 3 times every 5 seconds.

I have tried many configurations in amdcccle and in the settings GUIs, but with no success... I have also tried several ways of reinstalling the drivers - via the Ubuntu settings GUI and downloading from AMD site and compiling for AMD64, but the result is always the same. 3D games like tuxracer work fine, though.

I could accept that maybe my hardware is too weak for this kind of application, but with the "top" command I can see the processors are around 30% usage.

ATI RADEON HD6410D should also be enough for HD movies, right? 

I believe something is wrong with the drivers as the Linux support for ATI boards has a loooong story, but before 

So, before blaiming the drivers, I'd like to ask the community what is the opinion about this problem: Could it be lack of HW resources, or could it be definitely driver problems?

Any suggestion?

Thanks in advance,
Jabss

---

### Post by inobe on 2012-03-02
>  the image is not continuous.... How can I say this? It produces some kind of quick hangs


ati/amd falls behind in video acceleration.

i seen folks here find ways to get it working, many have issues with this graphics chips.

[https://www.google.com/search?aq=1&oq=ubuntu+XvBA&ix=hcb&sourceid=chrome&ie=UTF-8&q=ubuntu+xvba-va-driver](https://www.google.com/search?aq=1&oq=ubuntu+XvBA&ix=hcb&sourceid=chrome&ie=UTF-8&q=ubuntu+xvba-va-driver)

[http://askubuntu.com/questions/87395/how-can-i-enable-hardware-acceleration-for-an-ati-radeon-hd](http://askubuntu.com/questions/87395/how-can-i-enable-hardware-acceleration-for-an-ati-radeon-hd)

edit: > I believe something is wrong with the drivers as the Linux support for ATI boards has a loooong story

linux has nothing to do with nvidia or amd, these are proprietary boards/chips that have proprietary drivers, that said the vendor is fully responsible for lack of support.

---

### Post by Jabss on 2012-03-03
Any other opinion?

Is this HW really bad or am I having bad luck with the OS choosen?

I didn't mean to say its linux/ubuntu fault with the drivers. I just wanted to reinforce the fact that who owns ATI/AMD boards has much more problems with linux than the NVIDIA ones...

Thanks, 
Jabss

---

### Post by nd456 on 2012-03-03
Ati and Linux don't get along very nicely (unfortunately) you could try giving your meidia player a higher process priory but thats a stretch...

---

### Post by Jabss on 2012-07-04
I'm now able to play 1080p movies with no noticeable problems after upgrading to Ubuntu precise and by following the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)

I also activated the Hardware Video Decode Acceletation (experimental).
[B]
[/B]Now I just need to have the surround working. Opened a bug report [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1014897](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1014897)

:popcorn:

Cheers,
Jabss

---

