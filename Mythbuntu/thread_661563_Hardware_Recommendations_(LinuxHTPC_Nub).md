---
title: "Hardware Recommendations (Linux/HTPC Nub)"
date: 2008-01-08
forum: Mythbuntu
---

### Post by psybert on 2008-01-08
Hello. First post here. I've been doing some research for the past week or so about setting up an HTPC. My wife is constantly bugging me to be able to record her shows, I'm not a huge TV watcher, but I do enjoy some shows here and there. I have "free" cable that is included in my home owners association that consists of 80 analog channels. There is also over the air digital available for all of the basic channels, which i've yet to tap into because my TV doesn't have a digital tuner. I have a 48" wide screen RPTV with a digital (DVI) input. 

I've chosen Mythbuntu as my preferred OS after looking through several others like LinuxMCE, Mythdora, and Knoppmyth. I've read this tutorial [http://www.linuxis.us/linux/media/howto/linux-htpc/index.html](http://www.linuxis.us/linux/media/howto/linux-htpc/index.html) I've been researching various parts and hardware on linuxtv.org, mythtv.org

I'm a linux nub, I've just installed ubuntu on an old PC i had laying around just to get a feel for the linux OS, but that's about it. I have quite a few PC's laying around that I can pick and pull from. I actually bought a case off of eBay yesterday that I initially liked, but I might wind up changing in favor of one of the ASUS barebone systems. I have a mATX, p4 2.8 DELL with a gig of memory that i plan on filling the new case, along with an ATI X1650 something. I've read a lot about how ATI isn't really supported on linux, so i'm leary of that. I also have a decent sound card laying around as well.  Also to note the Dell board has 2 PCI slots, 1 PCIe x1, and 1 x16. The ASUS system i'm looking at has 2 PCI slots. 

I pretty much have a few areas of questions in which i need some help with: 

Video: I was reviewing a couple barebone systems from ASUS that include onboard video: Nvida GeForce 6150 for AMD platforms, and Intel GMA 950 for Intel platforms. Will i have compatibility/performance issues if i choose either? What about using a standalone ATI X1650? 

TV Tuners: I'm pretty sure i want two analog tuners so i can watch and record and the same time... right? On that note, I would definitely want to do the same with the digital channels as well. So i need a total of four tuners, 2 digital, 2 analog, right? What's the best way to fill up 2 PCI slots to get all of that? I'm originally from hauppauge, NY, so I feel i have a connection to that brand, although I was reading up on the Kworld tuners and the PcHDTV as well. I like the Hauppauge PVR-1800, but the analog isn't supported, right? Does the KWorld 115/110 support two digital signals or is it one analog and one digital? 

Remote Controls:
What's the deal with these guys. I read that the Microsoft ones are the best, and when you set up other remotes, you have to emulate the microsoft ones. If one comes with one of the tuners I pick, will I be able to get full functionality out of it? I kind of liked the one that was included with the PVR-1800 kit. Will i have any problem getting one of those MS mini keyboards to work in addition ([http://www.amazon.com/exec/obidos/tg/detail/-/B000AOAAN8/ref=ord_cart_shr?%5Fencoding=UTF8&v=glance](http://www.amazon.com/exec/obidos/tg/detail/-/B000AOAAN8/ref=ord_cart_shr?%5Fencoding=UTF8&v=glance) $30) ?

Anyway, I know it's a barrage of questions, I just need a little assistance so i can get started! Any recommendations would be amazingly helpful. Thanks everyone!

---

### Post by ozybushwalker on 2008-01-08
G'day. I'm new to MythTV and Mythbuntu too.

I'm only interested in Digital TV (DVB-T) because the analogue service in my area (Eastern Australia) is closing down in a few years and everything thats on analogue is also on digital anyway.

I have used a Leadtek WinFast DTV1000T which has a single digital tuner and once I worked out how to configure MythTV for it the card has worked very well. The Leadtek WinFast DTV2000H is a hybrid unit with a digital and analogue tuner on the same card. I have a DTV2000H but don't yet have any experience with it.

If you explore the links on [http://www.linuxtv.org/wiki/index.php/Main_Page]("http://www.linuxtv.org/wiki/index.php/Main_Page") you will see a bunch of digital tuners supported in Linux, some of which include analogue tuners. Some of the (DVB-T) digital tuner cards include two digital tuners. If you can't get the combination you want to fit into 2 PCI slots it would be worth investigating USB tuners.

Don't skimp on the research into the Linux support position. It will help immensely to set reasonable expectations. You will find things you might not expect, such as tuner cards that are supported but the accompanying  infra red remote is not supported.

---

### Post by murchball on 2008-01-08
For analog, the Hauppauge 150, 250, 350 and 500 are supported out of the box and for digital, the HDHomeRun is the way to go. The HDHomeRun has two tuners and so does the Hauppauge pvr500, so You can actually get 4 tuners on 2 devices. One thing to note, you don't need two tuners to watch and record at the same time, only to watch and record two *different* things at the same time. Also, the HDHomeRun is a simple networked device; it doesn't take up any PCI slots.

---

### Post by psybert on 2008-01-08
Regarding the HDHomeRun, I didn't really think it would be a good choice because I would have to buy an additional NIC and PCI slot to be able to support it. Plus I really didn't want to have another component outside the PC to worry about. 

Is there any supported Dual Digital Tuners, or combo Analog/Digital tuners?

---

### Post by aaltieri on 2008-01-08
The HDHomeRun unit sits on your network as a regular device.  It doesn't need to be tied directly to your computer.  The benefit of this is that if you are using it for OTA, you can put the tuner closer to the antenna in a part of the house with better reception.  I have a friend who did this (it's in his attic) and it works like a charm.

So if you have a switch (I wouldn't try a hub with HD transmission) you should be fine.  You shouldn't need a second card in your server.

anthony

---

### Post by murchball on 2008-01-08
Why would you need an additional NIC? Does the computer you're using not have one? The Homerun is one of those 'set it and forget' devices, except that there is really nothing to set. Plug it in to your antenna, tell MythTV that it's there and do a channel scan. It's really straightforward.

---

### Post by psybert on 2008-01-08
Well in that case it's a pretty nice setup. Is it slower to change and retrieve channels versus PCI tuners?

---

### Post by newlinux on 2008-01-08
The kworld ATSC 110s and 115s are single tuners. They can do analog and digital, but not both at the same time. So you can record one analog or one digital signal at a time with these. I think your only option if you want 2 analog and 2 digital tuners that can all be tuning at the same time and you have only 2 PCI slots available is the hdhomerun because I don't think there are any PCI dual tuning digital QAM/ATSC cards. A PVR-500 and hdhomerun seem like the way to go if you are constrained by PCI slots. 

I haven't heard of anyone saying the speed to retrieve channels is slower. I imagine it wouldn't be very noticeable with decent network performance. I watch hidef over the network from remote backends and I don't notice much a speed difference between that and watching hidef from a tuner on a local backend. This would seem to approximate the hdhomerun experience.

As far as remotes go, you have way more choices than MCE, and they don't have to emulate MCE remotes. In fact, you can use pretty much any remote with a working receiver. The advantage to using a known or more popular remote is that you don't have to create the config files (lircrc and lircd.conf) from scratch. So with remotes that come with tuners, the key isn't getting a remote that will work, because in the worst case you can use irrecord to build the lircd.conf file. The key is getting the receiver to work, or buying/building a receiver that will work. For most, it's just easier to buy a well supported remote and receiver.

The keyboard you mentioned should work AFAIK, but you might have to do a little extra work to get all the multimedia keys to work. But I don't know for sure.

---

### Post by psybert on 2008-01-08
> **newlinux said:**
> 
As far as remotes go, you have way more choices than MCE, and they don't have to emulate MCE remotes. In fact, you can use pretty much any remote with a working receiver. The advantage to using a known or more popular remote is that you don't have to create the config files (lircrc and lircd.conf) from scratch. So with remotes that come with tuners, the key isn't getting a remote that will work, because in the worst case you can use irrecord to build the lircd.conf file. The key is getting the receiver to work, or buying/building a receiver that will work. For most, it's just easier to buy a well supported remote and receiver.




Is there a "well supported" list of remotes and receivers out there? 

**EDIT** [http://www.lirc.org/html/table.html](http://www.lirc.org/html/table.html) Is this a good one to start from?

---

