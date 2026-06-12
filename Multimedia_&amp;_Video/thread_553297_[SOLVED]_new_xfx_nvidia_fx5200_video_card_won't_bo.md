---
title: "[SOLVED] new xfx nvidia fx5200 video card won't boot"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by middlewordie on 2007-09-17
i have just bought an xfx nvidia fx5200 graphics card 128Mb 8xAGP from amazon. i'm trying to get mythtv working on the following box:

sempron 2800
1gb ram
160gb maxtor ide
asrocks k8 upgrade
liteon dvdrw
nova-t dvb card
ubuntu fiesty

i had an ati radeon 7000 but that doesn't support tv out in linux, so although i have mythtv installed, i can't actualy use it. hence buying the the fx5200...

the first time i started the pc i got the nvidia card text on screen, then it flashed up with the boot options screen, then the screen goes blank. i've tried getting into the bios, but it simply brings up a blank screen with a flashing cursor.

any suggestion would be very welcome - i am running out of hair...!

>>>>>>>>>>>>>>>>
[B][U][COLOR="Red"]
SOLUTION: This was a hardware problem probably heating related due to a poorly fitted (by me) heatsink on the CPU.[/COLOR][/U][/B]

---

### Post by w4ett on 2007-09-17
I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by middlewordie on 2007-09-17
i can't actually boot - i just get a blank screen and a cursor - i get a beep when pressing keys but no response.

i've just tried rebooting with the old ati radeon in and now that doesn't work either. this does not look good. :(

---

### Post by w4ett on 2007-09-17
.boot into recovery mode from grub

---

### Post by middlewordie on 2007-09-17
how do i do that? sorry to be an idiot!

at present i can't even boot from the cdrom. teh bios finds the hard drives then just stops

---

### Post by w4ett on 2007-09-17
from the Grub boot menu...find the entry that says recovery and select it....this will get you into Ubuntu (without the GUI) so you can use the command line interface (CLI)...then try my earlier directions,

---

### Post by middlewordie on 2007-09-17
thanks for your help.

i don't even get as far as the grub menu - even with the feisty cd in the dvdrw the computer just stops before it's finished looking up the drives

is it worth resetting the cmos?

---

### Post by w4ett on 2007-09-17
yep...sounds like something is amiss in your bios/cmos.....check your HDD detecttion there

---

### Post by middlewordie on 2007-09-17
tried resetting the cmos and no luck. looks like it might be a dead motherboard moment... :(

---

### Post by w4ett on 2007-09-17
I'd try unplugging your drives (hdd and CDRom) and then trying to get a POST screen.....

---

### Post by xpod on 2007-09-17
> i had an ati radeon 7000 but that doesn't support tv out in linux.


I do hope you get over this hurdle but I also hope you have more luck with your TVout than i have using the new FX5500 i bought.
I went from good TVout in full color with an older MX4000 to black & white Tvout with the new card.

Still.......good luck with this one just now:)

---

### Post by middlewordie on 2007-09-17
ok, hd and dwdrw unplugged 
now i don't get anything at all. just the blank screen and the flashing cursor of death!

---

### Post by w4ett on 2007-09-17
[IMG]http://images.google.com/imgres?imgurl=http://scripturist.org/don%27t%2520panic.jpg&imgrefurl=http://bibimeialonga.blogspot.com/2007/03/dont-take-it-too-serious-lifes-too.html&h=465&w=350&sz=62&tbnid=Sy39jwmCMTyNHM:&tbnh=128&tbnw=96&prev=/images%3Fq%3Ddon%2527t%2Bpanic%26um%3D1&start=2&ei=0_7uRtXFAaLAggTx7sDfBQ&sig2=UzXph93SDWOYBR3g51OCIQ&sa=X&oi=images&ct=image&cd=2[/IMG]

Take a deep breath.........

1.....We need to check your memory...do a visual inspection...make sure they are fully inserted and locked into their slots

2.  If you have 2 memory sticks, remove them and test each one individually....try powering up with each one in the slot closest to the CPU,

3.  Check all power connections

A question.....are you getting any beeps from the pc speaker when you try to boot?

.....now exhale.... :)

---

### Post by middlewordie on 2007-09-17
progress - with only one 512mb stick in i get a short delay before it goes to the cursor of death.

one thing that has sprung to mind whilst surfing google is that my 330w power supply might be insufficient...

---

### Post by w4ett on 2007-09-17
> **middlewordie said:**
> progress - with only one 512mb stick in i get a short delay before it goes to the cursor of death.

one thing that has sprung to mind whilst surfing google is that my 330w power supply might be insufficient...

Yea....about 60% of computer faults (hardware wise) can be attributed to PSU failures/problems.....
not saying you have one, but the troubleshooting of hardware faults is a process of elimination and your powersupply is the first thing I look at when diagnosing a problem on the workbench.  It's possible there is a problem there.

I would substitute a known good power supply or having yours checked with a psu tester.

---

### Post by middlewordie on 2007-09-17
it should be fine - its a brand new seasonic s12 330W - £50 worth!

this is incredibly annoying - every time a buy a new component, another one seems to break. in the last year i've replaced the cpu, motherboard, fan, hard drive, psu and graphis card...the whole pc!

bed time now though - thanks for your help and hopefully it will just magically work in the morning!

---

### Post by w4ett on 2007-09-17
Well.....you should be ok there.Might be time to review some guide to diagnose Post problems.

[http://drizzten.com/blargchives/001425.html](http://drizzten.com/blargchives/001425.html)

---

### Post by middlewordie on 2007-09-19
ok, day 2 of the great why is my pc not booting saga.....


does any one know how to move this thread? i think it should be somewhere else as it does not seems to be a video/multimedia problem.

i have taken the rather bold step of completely disassembling the pc. one thing suggested by my helpful it man at work, was that it may be a heat issue, particularly as the death occurs at the same stage every time. he thought it might be i had dislodged the heatsink (the scythe is quite heavy), whilst moving the case.

on removing the fan there appeared to be a less than complete covering of the cheap white goo supplied with the fan. should i be using something more substantial?

ok, tried with the less is more approach to applying thermal paste and it seems to be working, i now have a post beep and ubuntu started up.

cmos clearing. i've done this and it's raised a few questions in ubuntu booting up because disc write times are 49000 days into the future!

---

### Post by w4ett on 2007-09-19
Now you need to reset the system clock in the Bios......this master clock controls the filesystem timestamp checks upon boot.

---

### Post by middlewordie on 2007-09-19
Thanks for you help - i now have new problem - see [here]("http://ubuntuforums.org/showthread.php?t=554718")

---

### Post by w4ett on 2007-09-19
OK..please mark this thread solved

---

