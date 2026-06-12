---
title: "New MythTV Shopping list plea for confirmation"
date: 2010-07-18
forum: Mythbuntu
---

### Post by bglaze1 on 2010-07-18
I was just compiling my shopping list for my new Myth system.  I am finally going to be able to upgrade my old system.

I was thinking of getting the following:

ASUS M4A785-M Motherboard 
AMD Athlon II X4 635 Quad Core Processor 
Centon 4GB DDR2 PC6400 Memory Upgrade 
Seagate Barracuda 7200.12 Hard Drive 
XFX Radeon HD 4670 Video Card 
Lite-On IHAS124-04 Internal DVD Writer 
Ultra X-Blaster Black ATX Mid-Tower Case 
Ultra LS500 Lifetime Series 500W Power Supply
HD HomeRun tuner card 

I went to compare with what was listed in the Functional Hardware thread, and I found several Asus M3A78 motherboards (some of which were working with HD HomeRuns), but unfortunately not any Asus M4A785's listed in the functional hardware.  Also, I didn't see any 4670's listed in that thread either.  Is that card a good quality video card?

This made me start to doubt my shopping list, so I am coming here for some confirmation, will this system I listed above work with Mythbuntu?

I am just hoping to get a system that will allow me to record two show simultaneously or playback in HD one show, while recording something else.  I don't need it to be super top of the line, but I do want something that can do the job easily.  And I would prefer to spend the money on something that will be mostly working out of the box.    

Please let me know if this works, or worse, if it is not going to work without major tweaking. 
Thanks for your help.

---

### Post by bglaze1 on 2010-07-18
Oh, I forgot to mention, I had been looking at the Asus M3N78-EM motherboard, which was listed several times on the functional hardware thread.  It uses the NVidia onboard chipset compared to the ATI onboard chipset used by the M3A78 motherboard.  The M3N78 seems to have been discontinued.  If I were able to find one, would I be able to substitute this motherboard (the Asus M3N78-EM) in for the Asus M4A785-M listed originally and have everything in that system still function correctly?  

Does the onboard graphics chipset even matter, if I am using the 4670 video card?

Thanks again.

---

### Post by LowSky on 2010-07-18
Um... you dont need the onboard chipset if you are going to use a graphics card. So nearly any AM3 AMD board will do.
Also you should get a Nvidia graphics card, and not an ATI based card so you can use VDPAU for better video encoding and to take stress off the CPU. Preferablly a Geforce 9600GT or better. Yes a AMD motherboard can use Nvidia graphics cards. I'm doing it in two of my computers right now.

The HD HomeRun will work on any system, as its a network based tuner, and not PCI. You can plug it into your router if you like, it doenst have to be connected to the PC directly.

If you want to use an internal PCIe tuner, the HVR-2250 does work pretty well if you follow my tutorial.

Also have you heard of Multirec, it means you can potentially record two or more shows if they use the same frequency channel. My dual tuiner can potentially record/watch 4+ shows at the same time, as long as the signals are from the same source... you got to love digital!

---

### Post by newlinux on 2010-07-19
With the exception of the GPUs, it will work fine. Way more powerful than my machines which can do what you want. Go with nvidia. A g210 or better can be had for less than $50 these days (just bought one myself to replace an aging and failing 7100). Going nvidia will prevent a lot of potential headaches with an HTPC. The onboard GPU  in the Asus M3N78-EM is vdpau capable (thus, you wouldn't actually need to buy a separate video card). If you are watching only recorded digital content, vdpau won't even be close to necessary with your CPU, but nvidia in general works better in Linux.

---

### Post by laffinet on 2010-07-19
I would scale back the CPU (quad core is overkill for a media PC, dual core is more than sufficient) and get a nvidia card (GT210 upwards). 
Fully HD capable with very low load on the CPU.

---

### Post by LowSky on 2010-07-20
> **laffinet said:**
> I would scale back the CPU (quad core is overkill for a media PC, dual core is more than sufficient) and get a nvidia card (GT210 upwards). 
Fully HD capable with very low load on the CPU.

Quadcore might seem overkill, but when an AMD Athlon II dual core is only $25-30 cheaper, the extra cores can be handy if you are going to use the PC for other duties outside of the normal HTPC workload.

---

