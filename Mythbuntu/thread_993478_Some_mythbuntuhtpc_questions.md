---
title: "Some mythbuntu/htpc questions"
date: 2008-11-25
forum: Mythbuntu
---

### Post by Extricate on 2008-11-25
I am hoping to build a htpc/media box as an all in one solution for streaming HD media/blu-ray,hd-dvd,dvd playback/satellite pvr.

I was wondering if Mythbuntu will fulfil these requirements, specifically:

1. Would it be possible to continually output the satellite to a secondary video output, and watch a film on the primary? This would mean the video signal could be piped to another room and the box could still be used to watch a film on by someone else.

2. Is no DXVA on Linux a concern? Was considering a 780 AMD chipset with as low powered cpu as possible, while retaining ability to play highest bitrate 1080p60-24, will I be able to offload some of the work to onboard decoder?

3. What sort of EPG will I be able to use (absolutely clueless here) would like to be able to schedule recordings, and watch all free to view satellite in UK (like freesat, but I hear their guide is closed access currently?)

4. Fast boot time is very important to me, would really like box to behave as much like a normal component piece as much as possible. Would it help to use a small SSD (MLC 30GBs are cheap now) for the OS and a larger hdd which could stay in idle mode for PVR functions (All media is on separate server).

5. Is a wifi adaptor say, easy to configure in stipped down mythbuntu? Vital for streaming (can suggest good ones if you like!)

6. Any audio decoding issues on hd formats such as dts-hd, dolby tru hd etc? Wanted to pass through to decoder though.

Thanks for your patience and suggestions.

---

### Post by the goat boy on 2008-11-26
I have mythbuntu running on my PC

the wireless on it was totally abysmal. I spent weeks getting it to run, but it was still shocking

in the end i bought these:

[http://www.devolo.co.uk/uk_EN/index.html?gclid=CMPKyei4kpcCFQWVMAodMnyR_g]("http://www.devolo.co.uk/uk_EN/index.html?gclid=CMPKyei4kpcCFQWVMAodMnyR_g")

from my limited knowledge wireless on linux is just rubbish. Please don't shout at me for that! I tried my best to get it to work. It was easier to fork out the cash to get the home plugs that suffer constant loss of connection etc...

as for the EPG, mythbuntu can get some of the freesat epg just by selecting "use EIT information" from the card set up menu

I get the channel information for most of the freesat channels with that, just not Channel 5 at the moment. It takes a while to fiull the EPG, but it works. 

for my EPG i use the mythweb function of mythbuntu. So i can select recordings through my laptop via a web portal running on the mythbuntu box.

if you want to watch one channel and feed another channel to another reoom, i think you will need two sat cards for that. unless they are on the dame multiplex ( i think)

---

### Post by Extricate on 2008-11-26
Thanks for your reply goat boy.

Interesting about wireless on Linux, I have had driver issues and fiddled with ndis wrappers etc but not really tested throughput when connected.

I do actually have dual LNB coax, so the channels are split (and there are cards with two inputs on) but even if I had one I wonder if I could have myth primary output via hdmi, then force satellite output to vga where I could switch the output to RF coax and supply the signal to other rooms? This is what has been done with the Sky+ box in the past and I wish to duplicate this functionality (or I may have to end up getting that humax hd pvr!) it seems a pity to have so many boxes under that TV when really 1 should do the job with a decent A/V receiver!

Glad to hear epg is not a complex issue, and hopefully more freesat epg information will be released/discovered in the future as well.

---

### Post by fatmonk on 2008-11-26
I actually foudn wireless under Linux a vast improvement over Windows.

For me it seemed faster and far quicker to connect.

My only reservation there is the new Network Manager app and keyring that it insists on using which means I currently need to enter a password to connect to the wifi whenever the box is booted (I'm trying to solve that one though, and I do believe it will be doable).

Alternatively, connect the myth backend via a plug in network connetion as suggested by goat boy (one on the myth box and one on your wireless router).

For multiple outputs you would be better off building a stand alone Myth front end to connet to your other TV. It IS possible to run two front ends on a combined 'front-end back-end' box, but then you would have top run cables from the main combined box to the other TV. Why not just build a front-end only box and have the video streamed from the backend to the front end wirelessly (thats what Myth's architecture was designed for - one or more backends and as many front ends as you like).

So long as you don't go for an odd wireles card (I had problems with a wireless-n card) you shouldn't have any problem getting a good wireless connection under linux. I'm using a Broadcom based card and it's fine.

-FM

---

### Post by the goat boy on 2008-11-26
i tried two methods

one was a netgear usb wireless dongle and the other was a belkin pci card

nothing but trouble using the both of them.

neither would run under the 64 bit OS

i got it to work on the 32 bit os, but kept losing connection all the time, and the network manager kept inventing a new password for my wpa all the time. i had to keep re inputting it every 5 mins or so.

this is my biggest gripe with linux. but for me its forgivable, as long as i dont have to use windoze!

since i switched to an Ethernet based connection, its been nothing but joy.

---

