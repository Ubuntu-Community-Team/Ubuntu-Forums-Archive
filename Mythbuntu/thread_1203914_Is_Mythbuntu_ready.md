---
title: "Is Mythbuntu ready?"
date: 2009-07-04
forum: Mythbuntu
---

### Post by deamon_knight on 2009-07-04
I had been planning to try Mythbuntu when I was ready to build a new MediCenter. Unfortunately, My XP MCE System died on me. So I rebuilt what I could without doing as much research and upgrading as I would have liked. Luckily I got it back up and running without too much trouble, but I'd really like to move Away from MCE and into Mythbuntu. I'd like some advice on how easy this journey might be.

The Hardware:
Mainboard: Gigabyte MA78GM-US2H 
[http://www.gigabyte.us/Products/Motherboard](http://www.gigabyte.us/Products/Motherboard) Products_Overview.aspx?ProductID=2997

CPU: AMD X2 7850
2GB RAM DDR2

Tuners: Two Haup PVR-150 .

How easy will it be to get Mythbuntu working properly on this setup? I'd also like to move from my existing Capture cards to a Haup HVR-2250 and 1250 and add a Blue-Ray drive, but I'm having trouble trying to verify that this hardware is supported. 

What is the advantage of HDMI for this, over say VGA or DVI? Will that be easy to set up?

As this is my only PVR, Downtime is an issue. I've gotten too used to fast forwarding past commercials!

I think I can connect a USB external HDD and install Mythbuntu to that device without affecting my current MCE install for testing purposes. Is this correct?

Thanks

---

### Post by epi 1:10,000 on 2009-07-05
Your processor will definatly handle SD and will handle HD as long as you use low power deinterlacers.  You will need an nvidia 8500 (or better) and VDPAU patches to offload video decoding to a GPU.  Im not sure if the 780G integrated GPU plays nice w/ linux but you can search the forums to see if anyoune else got it working.  The HVR-1250 is suported in the most recent kernels and the HVR-2250 requires you to install the divers via kernellabs mercurial repositories (see Lowsky's tutorial [http://ubuntuforums.org/showthread.php?t=942403](http://ubuntuforums.org/showthread.php?t=942403) ).  As far as I know Blu-ray isn't supported in linux but it is reported some have ripped the disks to their hard drive and played it from a file.   As far as installing MythBuntu on an external dive I have no idea how to do that.

---

### Post by deamon_knight on 2009-07-05
Thanks EPI. The board I have has An integrated ATI HD3200, but I see alot of people saying Nvidia is the way to go, so thats one mark against the move. Looks like there is little support for the 2250 so an Ideal situation with just two cards also isn't going to work. 

The Best upgrade option for me looks like a single 1250 and replace one PVR-150 with an HVR-1600 so I would have one Dedicated High def tuner for OTA, and three for cable, 2 analog and 1 digital for clearQAM.

I'm considering this and wanted to Try Mythbuntu, but it looks like the Wubi install does not work with ATI or NVIDA cards due to a Bug? Can someone confirm this for me, and if there is a work around?

For me, Wubi installs within windows. But after the first reboot it launches the install at step 9of15 to select my driver. The "Next" butttom remains grayed out no matter what option I choose and I cannot continue.

---

### Post by LowSky on 2009-07-06
Dont use Wubi to run Mythbuntu, its a bad idea. Use the normal installation method, you can repatition your Windows hard dirve to fit the Myth install, just make sure to do a defrag in windows before attempting. Wubi is a great way to try Ubuntu but a horrrible way to use it. Thats my opinion and I sticking to it.

The little support for the 2250 is a shame, and for me using windows 7 at the moment makes more sense, sorry guys. If you need a good linux supported tv tuner look here
[http://www.pchdtv.com/](http://www.pchdtv.com/)

---

### Post by epi 1:10,000 on 2009-07-06
> **LowSky said:**
> 
The little support for the 2250 is a shame, and for me using windows 7 at the moment makes more sense, sorry guys. If you need a good linux supported tv tuner look here
[http://www.pchdtv.com/](http://www.pchdtv.com/)

Have you tried the HVR-2250 in Windows 7 and if so how does it do?

---

### Post by deamon_knight on 2009-07-07
Thanks Lowsky, thats kinda what I thought, but I just wanted to try mythbuntu without taking down my whole system. Since its easy to scrounge up a basic PC, or just try Ubuntu from a Live CD, but I don't have a spare set of TVs and Capture cards lying around. Obviously the Live CD for Mythbuntu isn't a solution either.

With all the plate-spinning that is reportedly involved to get MythTv working I guess I'm not yet ready for it.

Also, cool link, I'm just not sure what they are advertising. Software HD decoding? Isn't ATSC & DVB just am Mpeg-2 stream, no "decoding" (as opposed to NTSC) needed? Poor linux support aside, Hauppauge breaks it down from the consumer standpoint: "Can I watch one Channel and Record another?".

---

