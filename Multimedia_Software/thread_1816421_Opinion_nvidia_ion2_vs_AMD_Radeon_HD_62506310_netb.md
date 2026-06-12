---
title: "Opinion nvidia ion2 vs AMD Radeon HD 6250/6310 netbook"
date: 2011-08-01
forum: Multimedia Software
---

### Post by tjones00 on 2011-08-01
Hello, I need to buy a couple of new netbooks to use as portable htpc this week and I'm torn between the two graphics options.

I already own an intel atom nettop with ion2 so I'm aware of how that performs.

These new AMD systems seem really nice and I was wondering if anybody has an opinion about them vs a nvidia ion2 system.

Either platform will cost ~275 USD per unit. Both will display 1080p. 

The reasons I'm leaning towards AMD fusion:

[http://www.notebookcheck.net/AMD-Radeon-HD-6250.40958.0.html](http://www.notebookcheck.net/AMD-Radeon-HD-6250.40958.0.html)

1) fusion cpu/gpu technology that was developed for the latest generation of gaming consoles eg. xbox360 slim that solved their overheating issues. 
2) it should be more energy efficient than an intel/ion system these will be netbooks not nettops

I'm thinking a basic 6310 model. eg.Asus EEE PC 1215B

[http://www.google.com/search?q=Asus+EEE+PC+1215B&hl=en&client=ubuntu&hs=5Ol&channel=fs&prmd=ivns&source=univ&tbm=shop&tbo=u&sa=X&ei=v2Y3TsXyK8bl0QHzuKHCAw&ved=0CFEQrQQ](http://www.google.com/search?q=Asus+EEE+PC+1215B&hl=en&client=ubuntu&hs=5Ol&channel=fs&prmd=ivns&source=univ&tbm=shop&tbo=u&sa=X&ei=v2Y3TsXyK8bl0QHzuKHCAw&ved=0CFEQrQQ)

Can anybody enlighten me further as to which of these graphics platforms would be better for my situation. HTPC running a basic xbmc interface that is portable for travel.

---

### Post by tjones00 on 2011-08-02
Hmmm if nobody has an opinion (I trust the a/v tech heads in this forum) on the graphics lets explore other areas.

AMD radeon has no dedicated memory, ion2 has 512mb. I could upgrade the system memory for cheap.

Apparently the AMD APU benchmarks better than an atom n550 on everything except the javascript test here.
[http://techreport.com/articles.x/19981/2](http://techreport.com/articles.x/19981/2)

It looks like I'll be ordering the AMD netbooks today unless somebody has a compelling reason I should pick an atom n550/ion2 netbook instead.

---

### Post by tjones00 on 2011-08-03
Well if anybody is interested I decided upon the AMD netbooks. The final point was the fact they use ddr3 1333mhz ram and can be upgraded to 4gb. I bought a couple of 2x2GB samsung kits as well. I went with a AMD C-50 Radeon HD 6250 for ~$270

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820147083&SortField=0&SummaryType=0&PageSize=10&SelectedRating=-1&VideoOnlyMark=False&IsFeedbackTab=true#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=N82E16820147083&SortField=0&SummaryType=0&PageSize=10&SelectedRating=-1&VideoOnlyMark=False&IsFeedbackTab=true#scrollFullInfo)

I'm pleased that samsung as actually entered the consumer ram marketplace since some of the major ram brands are just rebranded samsung memory anyway.

---

### Post by Björn on 2011-08-07
Hi, i'm curious how things worked out. How is 1080 playback?

Björn

---

### Post by tjones00 on 2011-08-08
They should be arriving today. I'll do some win7 tests (since win7 is included) and then linux. I'm not sure if the memory will arrive today as well. I'd really like to test it with the 4gb installed.

Edit: update w/o bumping thread.

The 40nm samsung ram arrived. It's dead sexy. Still waiting on the freaking netbooks though.

Oh some more consumer feedback. 

I also got to test a couple of these mini keyboards.

[http://www.amazon.com/ProMini-Wireless-Keyboard-TouchPad-Pointer/dp/B003VAVC26/ref=sr_1_3?ie=UTF8&qid=1312912082&sr=8-3](http://www.amazon.com/ProMini-Wireless-Keyboard-TouchPad-Pointer/dp/B003VAVC26/ref=sr_1_3?ie=UTF8&qid=1312912082&sr=8-3)

They work in linux but the signal is absolute garbage(inconsistent at 8ft). I'm sending them back and never buying a rf keyboard again from now on it's bluetooth or nothing.

---

### Post by tjones00 on 2011-08-17
Well for anybody who is interested. I received the netbooks yesterday after some shipping mishaps to my new address.

First impressions:
-10/100 nic but that's expected
-nice chiclet keyboard feels proper for touch typing unlike most netbooks
-some pretty cool features like a hdmi out fn key so you don't have to mess with displays in the os
-asus micro os incase you don't feel like booting a full os for a web browser etc.
-power saving/performance switch

Ram upgrade was a snap only required removing 1 screw. The samsung 40nm ram I used installed without a hitch.

As of now I've only been able to test vlc/flash/xbmc in win7(64b) as shipped with the netbook.

The displays I have access to are:
1080p samsung 55 inch led lcd 120Hz
1080p samsung 51 inch plasma 600Hz
1080p samsung 40 inch led lcd 120Hz

My ion2 platform for comparison is a lenovo q150. Most of my experience so far is on the 55 inch 120Hz.

Only tweaks I did to the os before testing was to set performance mode disabling aero, solid black desktop etc msconfig - no gui boot, set processors, set ram. Basic windows performance stuff. 

I might eliminate the page file to cut down on system i/o processing since that helped with the ion2 nettop.



-Lastest adobe flash player in win7 can play @ 1080p w/o any buffering/stuttering. This is something that the ion2 struggles with. I did notice some frame skipping but that could be due to the player/display refresh rate or the media itself.

-XBMC player in win7 with hardware acceleration on can play 1080p mkv media @ 1080p no problem.

-VLC player in win7 is having some issues @ 1080p. However I bet I can get it figured out with some tweaking.



But as to windows with xbmc player and flash it seems to work fine right out of the box at 1080p. For flash @ 1080p it seems to do a better job than the ion2. I did not test the playback with the default 1gb of ram. Ram is so cheap today that I don't see anybody purchasing one of these and not upgrading the ram.



Final note. These asus amd fusion netbooks are dead silent unlike the fan on my ion2 gpu and they barely warm up even after ~2hrs of heavy media use.



If anybody wants to hear something more specific or the results from some misc free benchmark let me know.

I think they're a good deal for $270 + $40 (ram upgrade) vs what else is out there. I'll update as to linux compatibility in a couple weeks. I will most likely install a minimal commandline system with xbmc.

---

### Post by tjones00 on 2011-08-21
Tried out a 44gb 1080p m2ts "stress test" file last night in xbmc @ 1080p there were about 100 frame skips after around 1hr of play. 

AMD has a fusion utility from there ccc downloads website for windows systems to add what I'd call enhanced power management profiles that also monitor services etc. I'll be messing with that this week. Remember this is windows with almost every application believing it needs to run as a service. So that's a nice little bonus from AMD.

Other tidbits of interest according to ccc the vclock on these netbooks is ~266mhz the allocated ram is 384mb. I might use the amd overclock utility and see if i can bump up the frequency and the allocated ram (if that is possible) to 512mb.

vs ion2

[http://en.wikipedia.org/wiki/Nvidia_Ion](http://en.wikipedia.org/wiki/Nvidia_Ion)
"The 12" version features all 16 cores of the GT218 chip and is clocked at 475 MHz, with a power consumption of 12 watts."
and of course 512mb discrete memory.

When playing 1080p mkv the system is hovering at about 1.26gb of 4gb(3.8whatever) memory.

I'm finding it hard to distinguish the cpu vs gpu usage with these fusion APU's but during mkv playback the "cpu" is hovering around 50%. I know this should be lower with hw acceleration enabled (10-12%) so I think this might be gpu usage on the apu. If it was pure cpu it would be higher ~90-100.

Update: 
Flashed the bios from 0310 to 0401 apu usage dropped to 20-30% on my test file. Used the AMD fusion utility to load their default DVD/Media profile. Flawless playback now with the display hz set to the file in xbmc (of course an initial frame drop upon loading)   **Audio rate ~6000Kb/s Video rate ~25Mb/s ~24fps** 1080p 42GB m2ts file local (2hr movie).

So I didn't need to overclock. Also note there is no option to set the video memory in the bios.

---

### Post by BicyclerBoy on 2011-08-21
Great post..
There be some fun getting linux working as well.

The ION2 weaknesses are being attached to an atom & that it has to use a PCIe x1 connection.
The fusion CPU is more capable & the GPU is intimately connected. This should make a great solution.

The weakness of the fusion APU is shader performance.
VA de-interlacing & hqscaling are not possible on fusion but are on ION2.

Your source material is 1080p24 so there is no de-interlacing or scaling necessary.
But with (all ?) digital broadcast TV (SD & HD) & DVD source, VA-DI & scaling is mandatory. I don't have any bluray..

AMD must be thinking the expected use will be 24p..The cheap nVidia GT520 has the same problem.

I guess you were outputting native 24p output to your displays & letting them generate intra-frames ?
Maybe the GPU drivers will start to do this in the shaders like pull-down etc.

---

### Post by tjones00 on 2011-08-23
I have used non 1080p media as well and haven't noticed any issues with interlacing/scaling. My media library is a complete hodgepodge of formats. My primary goal has been to test real 1080p media (bandwidth/processing) before worrying about anything else.

With the latest catalyst installed in the video settings the only options are automatic de-interlacing and pulldown detection. So it looks like the drivers are trying to help

Any suggestions for a true test of the scaling/interlacing? Besides me running random files and listing observations.

No PVR or blueray here. Stopped using subscription TV services years  ago since I noticed I barely used them. I tried one of those cheapass digital usb tv tuners  once......emphasis on tried and once.

Edit: The systems I have are AMD C50 Radeon HD 6250 just incase anybody was interested. HP has some E350 Radeon HD 6310 models for sale ~375

---

### Post by BicyclerBoy on 2011-08-24
With a varied mix of media types I guess you're better of with CPU capability & not relying only on the GPU.
I don't know any easy way to check the scaling except side-by side comparison with a reference or looking for artefacts esp. around motion.

These test tracks are very good for checking what type of interlacing is used, they are available in 50 & 60Hz.
And that's also good for demonstrating euro judder etc from frame pull-down.
[http://www.avsforum.com/avs-vb/showthread.php?t=1157287](http://www.avsforum.com/avs-vb/showthread.php?t=1157287)

---

### Post by bcschmerker on 2011-08-24
This is good information for those looking into a new laptop.  Advance Micro Devices® developed a new Socket FM1 for its latest desktop MPU's, which combine a capable Athlon II primary CPU (up to four cores) with a Radeon HD 6000a-series GPU on a common die; I'd consider this new E-series MPU for a new LinUX box that I have on the drawing board, were it not for the Athlon II's known problems with real-time preemption on Kernels 2.6.31-rt and earlier.  As of 23 August 2011, I still haven't information on a comparable MPU with both a Hyper-Threaded multiple-ALU CPU and an X4000-series GPU on a common die from Intel® for Socket 1155 or any newer LPGA specification.

Should Intel® have such an MPU in production in one to two years, I'd probably build a custom real-time preemptable kernel for Ubuntu® 12.04-LTS to run its internal GPU as a media accelerator, and use a separate GPU (either an nVIDIA® GeForce® GTS 550/560 or an AMD® Radeon® HD 6800-series or 7800-series, whichever has friendlier-to-LinUX drivers available for Kernel 3.0.n-realtime) for driving dual displays.

---

### Post by BicyclerBoy on 2011-08-24
The current E series are not targeted at laptops, they need CPU for business apps.

I think the fusion E series fills in the void caused by no one making CULV c2d,i3, i5 with a low power GPU & this is because Intel has not licensed the processor bus. Another reason is the cost of intel CPUs, & price seems to be king.
So we get stuck with atoms & botched on GPU chipsets like ION2.

The AMD bulldozer CPU core *may* change all this because it purports to be powerful & efficient (i.e. like intel iCPUs)

---

### Post by tjones00 on 2011-08-24
I've noticed Clevo is now producing C and E series AMD fusion laptops. Mind you not as many varieties as their intel products but it's a start. Interestingly they are producing 15.6 inch models with these APUs not 11-14.

[http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=329](http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=329)

**FYI Clevo produces the most powerful laptops in the world. They are rebranded/packaged as Alienware, VoodooPC, Sager, etc. Clevo first SLI laptop, first quad core, first just about anything etc.

With the 15.6 inch format on sale everywhere and being pushed hard (that Clevo AMD C50 with a 15.6 display doesn't make sense to me) I think manufactures are trying to liquidate their stock of display/chassis to move onto smaller form factors. Display is always a power hog, the smaller the display, the less power consumed.

My other observation as of late is it seems nvidia is being pushed to the enthusiast discrete graphics market. With intel developing it's own MPU (purposely shutting out Nvidia as bb pointed out) and AMD incorporating it's ATI tech into the APUs. 

With both processor companies going forward with a MPU strategy. The real question is do you think intel graphics will catch up to ATI before AMD cpus catch up to Intel?

---

### Post by tjones00 on 2011-08-24
> **BicyclerBoy said:**
> With a varied mix of media types I guess you're better of with CPU capability & not relying only on the GPU.
I don't know any easy way to check the scaling except side-by side comparison with a reference or looking for artefacts esp. around motion.

These test tracks are very good for checking what type of interlacing is used, they are available in 50 & 60Hz.
And that's also good for demonstrating euro judder etc from frame pull-down.
[http://www.avsforum.com/avs-vb/showthread.php?t=1157287](http://www.avsforum.com/avs-vb/showthread.php?t=1157287)


Sweet thanks man I'll definitely try these out soon. If it has some sort of report I'll post it here.

---

### Post by BicyclerBoy on 2011-08-27
All of this is just speculation:
I bet AMD hope their new Llano CPU etc helps to catch up to Intel..AMD GPU can easily hold their own..& someone has to keep Intel honest.
I think the intel iCPUs & AMD fusion are just the start of a long development path.

VIA (the only other x86 licence holder) seems to have given up, they recently sold of their S3 graphics business to focus on mobile/low-power.
I am surprised nVidia does not buy VIA or the licence but maybe nVidia is broke.

For the first time windows is soon to be compiled for another platform than x86. So maybe the fight over market share in going to the mobile/tablet/low-power computing market. (OS & h/w)
NVidia is in the market already with CPU & GPU.

Mobile & tablets & netbooks are about content consumption, HD video decode & basic openGL for games maybe.
Intel want just-good-enough graphics : HD decode & encode  bitstream processor & adequate openGL for apps & simple games.
They know serious gamers will always want discrete graphics openGL.

The good Intel graphics to date were/was bought from PowerVR (GMA500 Poulsbo)
Guess that the HD2000 3000 are similar, can't find any discussion.

---

### Post by lakerssuperman on 2011-08-28
I have the 1215b.  The major problems with video playback under Linux are two.  First, VA-API, which is the video acceleration API is totally broken in 11.04.  So playback of hi def content does not work.  Trying to use XBMC with VA-API simply crashes the program.  Second, Flash has no ability to use VA-API on Linux even if it was in a working state so you lose out on hidef content acceleration on Youtube and other streaming websites.

ION may be inferior to Fusion, but it has the benefit of VDPAU, which is working in 11.04 and, though it is nowhere near as good as DXVA in Windows, Flash can use VDPAU to accelerate video.

---

