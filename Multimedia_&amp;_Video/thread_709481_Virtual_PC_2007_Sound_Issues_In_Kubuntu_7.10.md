---
title: "Virtual PC 2007 Sound Issues In Kubuntu 7.10"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by fantazmic2 on 2008-02-27
To all,

I am having sound issues with a Virtual PC 2007 Kubuntu 7.10 install.  The following is a list of symptoms (Based on current configuration*):

**With Sound System Enabled (Sound System - System Settings):**

-(No System Sound or CD playback) "Error-artsmessage cpu overload, aborting" when Audio Device is set to "Autodetect" or "Advanced Lunux Sound Architecture"

-(No System Sound or CD playback) No error messages when Audio Device is set to "Open Sound System", "No Audio Input/Output", "Enlightened Sound Daemon", "Network Audio System" or "Threaded Open Sound System"

**With Sound System Disabled:**

-(No System Sound) Scratchy/Skipping CD Audio

***Current Configuration based on troubleshooting from the "Comprehensive Sound Problem Solutions Guide"**

Modified:  "/etc/modules" with "snd-sb16" at last line
Created:  "/etc/modprobe.d/snd-sb16" with "options snd-sb16 isapnp=0"
Verified: alsamixer settings are correct based on "Comprehensive Sound Problem Solutions Guide"

**Things I have tried:**

-Troubleshooting using the "Comprehensive Sound Problem Solutions Guide" 

-Configured: "/etc/modprobe.d/snd-sb16" with "options snd-sb16 index=0 id="SB-16" port=0x220 mpu_port=0x330 irq=5 dma8=1 dma16=5 isapnp=0"

-Looking/Reading Audio issue threads

-Google search for error messages and solutions

**Interesting Information:**

I am not having an issue with Ubuntu running the same configuration (running in Virtual PC 2007) which corrected the same issues.

I am only having Scratchy Sound (System and CD) with GOS which is based on Unbuntu (From what I have read) running the same configuration (running in Virtual PC 2007)

Each system seems to have it's own sb16 hardware issues.

**Any assistance or suggestions that might fix the sound issue in Kubuntu (or GOS) would be greatly appreciated.  I am new to all three systems (Ubuntu, Kubuntu and GOS) and would like to be able run them in Virtual PC 2007 since I would like to start using them on a daily basis**

Thank you,

Fantazmic2

Just an FYI:  I did run into Network and Mouse issues which I was able to resolve using the information found on this forum...thanks to the person posting those solutions.

---

### Post by rog66 on 2008-02-28
Hi - not an answer to your problem but I have exactly the same issue. Sound works fine in Ubuntu but not at all in Kubuntu.

---

### Post by arthurdent22 on 2008-02-29
I am using Ubuntu 7.10 with Virtual PC 2007. The sound is terrible, scratchy, it has echoes and warbles. The same occurred with Ubuntu 6.10. In most cases the sound is an unintelligible noise. One program plays the sound very fast, about 10 times normal. It looks like the sound driver timing is off. Perhaps there is a better version of sb16 available or an alternative version? Or perhaps some setting can be changed?

---

