---
title: "ATI-PCI (!) card - how to get TV-out and appropriate driver?"
date: 2008-06-03
forum: Multimedia Software
---

### Post by Thanh-BKK on 2008-06-03
Hello :)

Hooray, i managed to install Hardy Heron on my last computer and it really works, unbelievable.

But not the way it *should* work. 

To explain: That computer's sole purpose is to record video from my satellite receiver thru a TV capture card. The computer is running without keyboard and mouse and the TV is it's SOLE display.

Now, as it is an old Compaq, it does have onboard video, of course WITHOUT TV-out. And only PCI-slots for expansion.

Therefor i use an ATI-PCI graphics card, mobility M-5 chipset, 128 MB. This has two monitor connectors and one composite video out for TV. 

When i installed Ubuntu, i had one monitor and the TV connected and on. Install went fine, altough happened on the monitor only. Now, as the system is installed, it STILL works only on the monitor - the TV goes blank the moment the login screen comes up.

The "Hardware Drivers" manager can NOT find any restricted driver for this card, it seems PCI models are not really supported? However i installed the "fglrx" via synaptic and i have to say, it works. I can enable all desktop effects and compiz etc.

However still no TV-out, the only thing i actually NEED.

Now, when i cold boot the machine, all the way thru Grub, it works fine (picture on both TV and monitor). The moment the login screen comes up (X starts) the TV gets no signal anymore. The card hence works fine (also was fine with the previously installed Windows, where the "TV only" worked flawlessly) so it must be some setting somewhere in Ubuntu.

And now i need a manual how to do that :)

Ubuntu version is 8.04 Hardy Heron.

Many thanks in advance :)

Best regards......

Thanh

---

### Post by prshah on 2008-06-03
> **Thanh-BKK said:**
> 
However still no TV-out, the only thing i actually NEED.


Look for a utility called ["atitvout"]("http://www.google.co.in/search?q=atitvout")

and my old thread [[SOLVED] Use only TV instead of monitor]("http://ubuntuforums.org/showthread.php?t=709155"), which is solved, but only for SiS, not for ATI.

---

### Post by Thanh-BKK on 2008-06-03
Hello :)

Thank you for reply. I should have mentioned it - i DID try the "atitvout", problem is - it does nothing at all. 

I will try the solution in your thread, tomorrow morning when i'm at home again and in front of that box. 

However, a question - what version of Ubuntu were you running when you had that issue? As it was posted in February. Was that Gutsy (or older)? Because i'm on Hardy, which has a different xorg version, i believe the setup is entirely different from Gutsy (but don't know that for sure), i need a bulletproof method for Hardy 8.04.

I will let you know if i had any success :)

Best regards.....

Thanh

---

### Post by prshah on 2008-06-03
> **Thanh-BKK said:**
> 
However, a question - what version of Ubuntu were you running when you had that issue? As it was posted in February. Was that Gutsy (or older)? Because i'm on Hardy, which has a different xorg version, i believe the 


Yes, at that time, I was on Gutsy; I wiped out that and installed Hardy; in hardy too, the solution was the same. 

Note that though hardy comes in with a "stripped" xorg.conf, it does _still_ read and obey settings in it.

To summarize: My HTPC (gradiose title) is running MythBuntu Hardy with a SiS 6326 8Mb AGP, connected only to TV.

The part about "PAL800x600" etc is, AFAIK, only applicable to SiS. So try it, but don't be surprised if it doesn't work. Of course, if you're running NTSC, then please change accordingly.

I will post the xorg.conf from that machine here for your reference, later.

---

### Post by Thanh-BKK on 2008-06-05
Hello :)

I am a step further, but again stiopped dead in track now. I followed your suggestions as well as the ones on that other site, added those modes and now, EVERY time i boot, it starts up (only TV connected!) complaining that graphic card and screen can not be correctly detected, and therefor it's running in low graphics mode.

BUT that low-res image comes up on the TV, so that's a step forward.

However from here, i don't know further. 

When the "low graphics" thing comes up, it allows me to configure, so i chose the "fglrx" driver and the resolution and all however these settings are just bluntly ignored. I can't enable any desktop effects which tells me that my selected driver isn't active.

I tried getting the appropriate driver via Envy, it installed a bunch of stuff (amongs which is an ATI Catalyst Control Center (which i know from Windows), THAT complains that no driver is installed or in use. 

My problem is that this graphics card is a PCI model - NOT AGP or PCI-Express! And it looks like there is no driver to support these. 

According to "Device Manager" the graphics card is a "ATI Radeon Mobility M5 LV" but on ATI's site all cards are "X....." so i don't know which driver to try manually. 

I think i have only three choices here - go back to Windows (no!), throw away that computer and get one with an AGP slot (no money!) or try to find some sort of adaptor that can connect a regular monitor connection to a TV composite. I think those exist.... but not sure. 

Oh, i have a fourth choice - keep it like it is now, but the 800x600 picture doesn't fill the TV screen completely and it flickers HORRIBLY - unusable. There is PERFECT picture during boot, i.e. while the progress bar is showing - nice resolution, no flicker..... why can't the rest of Ubuntu use the same graphics settings as Grub??? 

Best regards......

Thanh

---

### Post by prshah on 2008-06-06
> **Thanh-BKK said:**
> Hello :)

modes and now, EVERY time i boot, it starts up (only TV connected!) BUT that low-res image comes up on the TV, so that's a step forward.

My problem is that this graphics card is a PCI model - NOT AGP or PCI-Express! And it looks like there is no driver to support these. 

Oh, i have a fourth choice - keep it like it is now, but the 800x600 picture doesn't fill the TV screen completely and it flickers HORRIBLY - 

OK that's a first step!

PCI/PCI-E/AGP - makes no difference to the driver. (Except performance). Your card is good enough; I'm using a SiS 6386 which is _terrible_, performance wise. Just to put your mind at ease, I have also used a Cirus Logic PCI w/ 2Mb, which worked OK, but since I had the 8Mb SiS lying around... (An interesting aside: The 8Mb SiS was giving unpredictable problems in Windows; tried with 3 sets of drivers; but it's running great in MythBuntu!)

I had the problem of 800x600 _overrunning_ the screen; I think you can fix both the sizing and the flickering problem by adjusting your refresh rate settings (I did). How? Look under System-Preferences-Screen resolution. WARNING! There are warnings that you can permanently damage your tv/monitor by using incorrect refresh rates; I have not had this problem in over 10 years of using computers, but your mileage may vary.

---

### Post by Thanh-BKK on 2008-06-06
Hi :)

Thank you for reply. Unfortunately i am stuck solid where i am now - i tried like a million configurations (manually via editing xorg.conf) and always ended up without GUI..... or the automatic reconfiguration ("Ubuntu is running in low graphic mode...." do i kind of gave up, i ticked that box "always run in low graphics mode" and now at least it boots and shuts down properly with TV-only.

I can NOT change the resolution to anything higher than 800x600 (there's two modes only - 640x480 and 800x600) and i can also NOT change the refresh rate - it's set at 61 (!) Hz. 

Also i can NOT enable any form of desktop effect (not that i would need them on that box). 

The driver in use is "mesa", when i try with (by editing xorg.conf) "ati" or "fglrx" i get no GUI respective the aut-reconfig thingy again. When i try the "sudo dpkg-reconfigure xserver-xorg" i also get no GUI, it's then in fact stuck after "running boot scripts" and won't go any further. Lucky i know the "nano" thingy by now :)

The reason why i think that PCI-cards are *not really* supported is because there is no "restricted driver" available - as i have three Ubuntu-boxes now, one with PCI-Express Nvidia and another with AGP-ATI, both have the "restricted driver" showing up and installed after it showed up. However this one doesn't give me such driver from a start, and also Envy doesn't detect any. 

Weird thing is - "Device manager" tells me it's a "Mobility M5 LV" which, according to some sources on the web, doesn't even exist???

Maybe i have to try to find an Nvidia-PCI card.... or just keep it the way it is. If i get the TV-capture card to work, it's all i need - didn't get there yet :)

With best regards.....

Thanh

---

