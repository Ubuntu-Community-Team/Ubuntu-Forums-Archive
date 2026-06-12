---
title: "Nvidia ION - New Kick *** frontend"
date: 2009-01-18
forum: Mythbuntu
---

### Post by BassKozz on 2009-01-18
Check it out: [http://www.engadget.com/2009/01/12/nvidia-ion-platform-gets-demonstrated-at-ces/](http://www.engadget.com/2009/01/12/nvidia-ion-platform-gets-demonstrated-at-ces/)
[http://hothardware.com/Articles/NVIDIAs-Ion-Small-FormFactor-PC-Platform-/](http://hothardware.com/Articles/NVIDIAs-Ion-Small-FormFactor-PC-Platform-/)
[http://www.pcper.com/article.php?aid=659](http://www.pcper.com/article.php?aid=659)

This puppy will have no problem running full HD h.264 1080p streams, with [VDPAU]("http://en.wikipedia.org/wiki/VDPAU") enabled. 
BTW (at the risk of getting backlash for even asking), when will .22 be released so we can take advantage of VDPAU (out of trunk)?
Will it be ready for Mythbuntu 9.04?

---

### Post by BassKozz on 2009-01-19
Guess it's not as exciting as I thought :P
> **BassKozz said:**
> BTW (at the risk of getting backlash for even asking), when will .22 be released so we can take advantage of VDPAU (out of trunk)?
Will it be ready for Mythbuntu 9.04?
:BUMP:

---

### Post by theophile on 2009-01-19
Yeah, it's really not that exciting. Plenty of cards have no problem playing back 1080p content. I've got a bargain basement GeForce 5xxx series that can play back 1080p content without a problem.

---

### Post by superm1 on 2009-01-19
> **BassKozz said:**
> Guess it's not as exciting as I thought :P

:BUMP:
The schedule for 0.22 is all dependent upon how upstream is looking.  If you have the skills, go help upstream get it out sooner :)

We'll have all the rest of the pieces ready in the distro for preparing to have 0.22 in place (ubiquity, mcc, packaging etc), but just waiting for the green light on upstream.

---

### Post by BassKozz on 2009-01-19
> **theophile said:**
> Yeah, it's really not that exciting. Plenty of cards have no problem playing back 1080p content. I've got a bargain basement GeForce 5xxx series that can play back 1080p content without a problem.

Really, you sure it's not the CPU your using that is processing that content?

> **superm1 said:**
> The schedule for 0.22 is all dependent upon how upstream is looking.  If you have the skills, go help upstream get it out sooner :)
This is the type of answer I was expecting to get from that question :P

I am not looking for a date, but more of a guesstimate (2mths, 6mths, 1yr ???) from the community, maybe a poll of sorts.
Will it be ready for Mythbuntu 9.04 (take your best guess) yes/no?

---

### Post by theophile on 2009-01-19
> **BassKozz said:**
> Really, you sure it's not the CPU your using that is processing that content?
It's both. The CPU is a P4 2.4 ghz, nothing special.

---

### Post by BassKozz on 2009-01-19
But isn't it still kinda a BIG deal because of its small form-factor?

I was planning on building a MythTV system using [Dell Studio Hybrid]("http://www.dell.com/hybrid")(s) (C2D 1.8ghz) as my frontend(s) but I decided against it, because people have been complaining of jerky h.264 1080p video using these units.

Also with VDPAU this new ION system will be able to off-load a majority of the work to the GPU.

---

### Post by danimaldaisy on 2009-02-04
the 5xxx series of cards SUCK! well for what i am using it for anyway. ( i am not flaming 5xxx users, but simply saying that i do NOT recommend first time users to go out and buy one, i re3ccomend all new users to go for the 7 series cards....and when VDPAU is supported get a 8 series or higher card.)i gave my dad my old 5700 for his mythTV build as he is using it for SD cable:popcorn::popcorn:

CANT playback 1080p content!!!!! 1080i recorded TV is possible unless you get a really high quality recording and then you have PROBLEMS!!!!

UNTIL VDPAU is fully supported "out of the box" in mythtv might i suggest a 7 series nvidia card and use xmcv.

now here is where EVERYONE will run into problems.

try ripping a blue ray into an MP4 format with NO QUALITY LOSS!!!!

just to get the movie playing in the front end you NEED Mplayer or the video will have massive stutter!!!!

i have a perfectly working system SO I THOUGHT!!! i have a asus p5n-em motherboard using the on board grforce 7100.....the card has REACHED it's limits....i cannot playback star gate blue ray rip without the audio going out of sync....i have a e2180 overclocked from 2.0ghz to 2.66ghz and 1066FSB....i had to overclock the sucker to ~2.9ghz in order to correct this issue....but step into liquid still has problems...so as far as i see my video card has reached it's limits and now depends on the CPU to kick in in order to push ahead.

the GPU is clocked at 600mhz and the ram shares its memory with the on board video and its running at 1066mhz....no way to overclock the on board video card.

i am going to temporarily swap in my q6600 from my main PC and see if my problem is solved....if not i am going to need VDPAU as well as a 9500gt fanless card from MSI in order to get going on these 2 really high bit rate movies.

really with mythtv .22 was here with full VDPAU support, full HD PVR support....i CAN'T WAIT! i checked and VDPAU will not be supported for my on board video card. DARN! maybe i should look and see if their is a way to overclock the onboard video by at least 100 MHZ....i do have a killer NB heat sink laying up next to a arctic freezer pro 7 blowing air across it and they are both cold to the touch...so i have room....but i bet overclocking the video card is out of the question....

keep in mind that i dont have a problem with my 30 other blue ray rips....

I HAVE TO RIP THEM.....mythtv and ubuntu have no blueray support!!!!!

---

### Post by danimaldaisy on 2009-02-04
Dell studio hybrid.....

that's because of the onboard graphics...YOU NEED NVIDIA!!

Intel®  Integrated Graphics Media Accelerator X3100-->no go for mythtv

---

### Post by BassKozz on 2009-02-04
> **danimaldaisy said:**
> Dell studio hybrid.....

that's because of the onboard graphics...YOU NEED NVIDIA!!

Intel®  Integrated Graphics Media Accelerator X3100-->no go for mythtv

I realize that, that's why I can't wait for OEM's to start pushing out the ION platform.

---

### Post by nicoloks on 2009-02-04
> **theophile said:**
> Yeah, it's really not that exciting. Plenty of cards have no problem playing back 1080p content. I've got a bargain basement GeForce 5xxx series that can play back 1080p content without a problem.

Smooth 1080p playback with no audio sync issuees  on a system running a P4 2.4Ghz CPU and a GeForce 5 series? What's your secret? 

I have a AMD X2 3800+ (dual core 2Ghz overclocked to 2.25Ghz) using an onboard GeForce 6150 and I can't get anywhere near watchable 1080p playback (video stutter and audio sync issues). I've also just built a system for a friend using an AMD 5600+ (dual core 2.9Ghz) and it just barely plays 1080p using the onboard GeForce 8200 vga. If you can get smooth 1080p playback with no video stutter or audio sync issues on lesser hardware I'd love to know how you did it!

---

### Post by newlinux on 2009-02-04
make sure you guys are comparing apples to apples... Is everyone here talking about 1080p h.264 or are some talking mpeg-2. 1080p mpeg2 with a 2.4 ghz and XvMC enabled on a Geforce 5 seems possible (I had a P4 2.6 with an MX440 that did 720p content without XvMC). I'd love to know how that P4 2.4 is doing 1080p h.264 without VDPAU.

@nicoloks - is your friend using VDPAU with the 8200

---

### Post by nicoloks on 2009-02-04
> **newlinux said:**
> @nicoloks - is your friend using VDPAU with the 8200

Obviously not. I had naively thought that I automagically had VDPAU support by simply using the Nvidia 180.22 drivers (I am a Windows user after all). However, after following [this guide]("http://zacgarrett.com/software/installing-mplayer-vdpau/index.html") I saw my CPU usage drop from approx 90% (+/- 10%), to around 10% (+/- 5%). This was on a high quality VC-1 rip of The Matrix in 1080p with DTS sound. Quite frankly if I hadn't seen it with my own eyes I would not have believed it!

---

