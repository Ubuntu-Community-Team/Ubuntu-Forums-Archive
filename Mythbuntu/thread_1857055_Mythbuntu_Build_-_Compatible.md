---
title: "Mythbuntu Build - Compatible?"
date: 2011-10-09
forum: Mythbuntu
---

### Post by Tagged on 2011-10-09
Hey all!

This is my 2nd attempt to use mythbuntu. My first build I got working enough to figure out that my TV Capture card was not going to be able to let me go further.

Please look over this build and recommend any changes to give me the best shot of getting onto Ubuntu full time!  Thanks all for your help!


Approximate Purchase Date: Ordering Monday
Budget Range: $400-$500
System Usage from Most to Least Important: TV & Movies (digital copies mostly). Would be nice if BF3 could run on here 
Parts Not Required: Keyboard, mouse. Also have 3 7200 hard drives I will transfer in: (320GB, 1Tb, 1.5Tb)
Preferred Website(s) for Parts: newegg.com
Country of Origin: USA
Parts Preferences: SFF, AMD LLano
Overclocking: Not important
SLI or Crossfire: possible later
Monitor Resolution: 1920x1080 via 48" LCD
Additional Comments:HTPC, would like to be quite. Will run Windows7. Would also like it to run Ubuntu to try to set up a frontend/backend myth tv if possible.   Not sure if this is enough power?  

ASRock A75M FM1 AMD A75 (Hudson D3) SATA 6Gb/s USB 3.0 HDMI Micro ATX AMD Motherboard with UEFI BIOS
Item #: [N82E16813157260](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157260) $74.99

Hauppauge WinTV HVR-1250 Hybrid TV Tuner /Video Recorder 1196 PCI-Express x1 Interface
Item #: [N82E16815116028](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116028) $49.99

Antec EarthWatts Green EA-380D Green 380W Continuous power ATX12V v2.3 / EPS12V 80 PLUS BRONZE Certified Active PFC Power ...
Item #: [N82E16817371033](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371033) $44.99

G.SKILL Ripjaws X Series 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory Model F3-12800CL9D-8GBXL
Item #: [N82E16820231428](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231428) $51.99

AMD A8-3850 Llano 2.9GHz Socket FM1 100W Quad-Core Desktop APU AD3850WNGXBOX
Item #: [N82E16819103942](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103942) $139.99

nMEDIAPC Black Aluminum / Acrylic / Steel HTPC 5000B Micro ATX Media Center / HTPC Case
Item #: [N82E16811204035](http://www.newegg.com/Product/Product.aspx?Item=N82E16811204035) $69.99

Total Price: $431.94

Biggest questions: Enough power? Would putting 5900rpm drives save a ton of heat / keep power much lower? This is an always on machine. Myth work on here?

---

### Post by ozite on 2011-10-09
That's more than enough power for MythTV frontend/backend.  For comparison, I use a dual core E7200 with 2 GB ram with a Hauppauge PVR-250, pcHDTV 5500, and Firewire tuner. Memory usage never goes above 2 GB for my uses. It easily handles recording 2 HD streams while playing back another HD program, with commercial flagging in the background.  I don't use VDPAU with an old fanless 8400GS.

I'm not sure about the heat difference with 5900 RPM drives. I have a mix of 5400, 5900, and 7200 rpm drives for 5 total drives in a modded Antec Overture II htpc case.  You might be able to save some heat with a different CPU choice (3800?).

---

### Post by nickrout on 2011-10-09
I don't see mention of a graphics card. If this is to be a frontend then there is only one wise recommendation - nvidia card capable of vdpau.

---

### Post by Tagged on 2011-10-10
The AMD processor comes with a 3850 built in. Pretty nice little CPU/GPU combo

---

### Post by nickrout on 2011-10-10
err... amd video?

Good luck with that!

---

### Post by David Grigor on 2011-10-10
Just go with a AMD Cpu + Nvidia card.   The built in GPU of the newer AMD CPUs is not an NVIDIA based so you won't get any real benefit from it.  If you do plan to use the machine to rip your digital copies a quad may be better. For just record/playback a lower end dual core if fine.

---

### Post by Tagged on 2011-10-10
Sorry, its not a 3850 card, that is the part number  :)

The integrated card is a ATI Radeon HD 6550D. Saw a couple reports that said this card could run WOW in ultra mode, and played BF3 beta. Will try BF3 without adding a discrete card, gaming is secondary and will actually not happen too much.

---

### Post by ian dobson on 2011-10-11
Hi,

Go with a NVidia graphic card if you can, the AMD/ATI linux drivers aren't the best under linux. Also hardware acceleration for videos under linux doesn't work/isn't supported by MythTV.

Regards
Ian Dobson

---

### Post by David Grigor on 2011-10-13
Like Ian said,  I was referring to ATI with Mythtv isn't any real benefit.  For Windows stuff may be fine but expect video in myth to require more cpu since there will be no acceleration.  I have used onboard video with ATI in the past and getting sound through hdmi wasn't a problem, it was the accleration that is lacking.  NVIDIA based is what you want for Mythtv use so getting a regular AM3 cpu + Nvidia gpu is the way to go. No need to pay for something you can't really use if mythtv is one of your primary goals with the new machine.

---

