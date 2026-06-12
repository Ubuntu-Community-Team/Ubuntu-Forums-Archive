---
title: "BSOD (sort of) after installing 14.04.1"
date: 2014-08-20
forum: Mythbuntu
---

### Post by paul164 on 2014-08-20
I had a perfectly functional 12.04 installation but I wanted to change my partitioning scheme and a few other things so I conned myself into a fresh install of 14.04.1.  I installed from the live USB key and all went well until I did the updating and added the nVidia driver that was at the top of the list and "tested".  I haven't seen an X screen since. I can still get to a console screen but have been unable to unload the nVidia driver and get back to the native driver. The mobo is a Zotac 8200CE that has an onboard nVidia GEForce 8200 video chip.  

I decided that it was simpler to just do a fresh install so I reinstalled over the existing 14.04.1 but did not check the box for the proprietary driver.  I don't think the "reinstall" is the same thing as a fresh install on a bare partition because I still had the BSOD (no X) after the install.  

I am going to repartition with gparted and try it again. I need to know which driver will work well for the nVidia 8200, as the native nouveau driver is not adequate for full HiDef...stuters...and the recommended driver (331 I think) DOES NOT WORK on the 8200.

---

### Post by bcschmerker on 2014-08-21
Actually, what you're describing is a "black screen of death" (KSOD), most likely a no-login-screen problem; a "blue screen of death" (BSOD), actually black with white text in LinUX, would be indicative of a Kernel panic or oops.  I ran into a consistent no-login-screen situation attempting to run any nVIDIA® Driver package, even the legacy version, on an eMachines®/Acer® EL1210-09 (Advanced Micro Devices® Athlon 64® LE-1620, nVIDIA® nForce® 780 with integrated 64-bit GPU) retrofitted with a Shuttle® PC6300001 power supply and any of three half-height video adapters built on the nVIDIA® GT218 GPU.  At least my system runs semi-stably with X.org Nouveau with the GT218.

I haven't received any Reply to my Thread "[Best nVIDIA entry-level GPU for X.org Nouveau in 14.04-LTS?](http://ubuntuforums.org/showthread.php?t=2218164)," as of 20 August 2014, concerning a go-no go to test other nVIDIA® GPU's such as the GF119 (used on GeForce® GT&#8482; 520 and 610 consumer and NVS&#8482; 315 professional VDA's) on the EL1210.

---

### Post by khPWXxF on 2014-08-22
[FONT=&quot]I found nVidia instability with 14.04 on both my Mythtv setup (8300 onboard) and my desktop system with an 8400 card.

311 drivers are the issue - downgrading in safe mode restored stability:
sudo apt-get install nvidia-304

hth
Phil

[/FONT]

---

### Post by paul164 on 2014-08-22
@[**[COLOR=#000000]khPWXxF[/COLOR]**]("http://ubuntuforums.org/member.php?u=1844453"):  Thanks...just what I was looking for.  I was about to do a fresh install...again...but I will try that first.  

@[**[COLOR=#000000]bcschmerker[/COLOR]**]("http://ubuntuforums.org/member.php?u=609186"): Black, of course.  I was still able to log in from the console (Alt-Ctl F3) for what that was worth.  I will try the downgrade as suggested above.

---

