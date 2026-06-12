---
title: "D945GCLF2 (Dual Core Atom) + PCI Graphics Card"
date: 2008-11-12
forum: Multimedia Software
---

### Post by what4893 on 2008-11-12
Hi,

I recently purchased a dual core Atom mobo, the D945GCLF2 system from Intel. I installed Ubuntu 8.10 and have been loving it. I decided to beef up my graphics capabilities and add a dual headed PCI graphics card. So, I picked up a PCI (not express) PNY 8400GS with 512MB. I slipped the card in and installed the restricted drivers. Upon reboot the system hung at the splash screen, but I was unable to get to a desktop by forcing the the mobo to use the integrated graphics. I figured it couldn't hurt to try a fresh install with the new graphics card. So, I set out to do this instead of trying to install it under the present installation. To my shock and dismay I found that when I tried to boot to install Ubuntu 8.10 again from the i386 disk the boot hung at the same spot as it did before. After about 1min the splash screen dropped out and I was presented with a plethora of Segmentation Faults and sh: File not found errors. I used the same CD before to install the current copy of Ubuntu and it checked out. Any ideas? I'm not sure if the card is so rare being an 8 series PCI card that there is no support for it or what? I know that the Atom boards were only recently supported by Ubuntu so that is the only reason I'm throwing that idea out. I'm no linux guru, but I'm comfortable enough to have gotten my system back up and running by restoring my old Xorg conf file. Any help would be greatly appreciated.

---

### Post by mikespug on 2008-11-17
This sounds similar to a problem I had on an old desktop pc where the onboard intel video conflicted with the add-on pci card and would hang on boot/install...so this may be worth a shot:

1. Remove the add-on graphics card and boot into your ubuntu install as normal.

2. Open terminal and enter the following without quotes:

"sudo gedit /etc/modprobe.d/blacklist"

3. Add the following two entries without quotes to the end of the file:

"blacklist agpgart"
"blacklist intel_agp" 

4. Shutdown the pc and reinstall the add-on graphics card.

5. Connect monitor to add-on card and boot pc.

5. Install restricted drivers if required (if using nvidia or ati you may try using envyng, it's in the repo's)

Good luck.

---

### Post by 2crazy on 2008-11-19
I have exactly the same problem using exactly the same hardware as described above. I also tried a Saphire ATI 9250 with the same results. 

I will give it another shot using the recommended fix. Would be nice if it works. :-)

---

### Post by what4893 on 2008-11-19
Thanks for the recommendation. I've been really busy with school recently and haven't been able to give this a shot. I'm hoping this weekend I can give this a go. I will post my findings. 2crazy, let me know if you have any luck with it if you get to it before me. I'm really hoping to be able to play some 720p video on my Atom box with that 8400GS :), guess we'll find out if it's possible.

---

### Post by 2crazy on 2008-11-21
It works perfectly!

mikespug, thanks for the solution!

---

### Post by what4893 on 2008-11-23
mikespug thank you sooooo much :D

This worked like a charm. Now I can enjoy dual monitors and 720p movies :popcorn:

---

### Post by Betelgeuse on 2008-12-27
> **what4893 said:**
> Thanks for the recommendation. I've been really busy with school recently and haven't been able to give this a shot. I'm hoping this weekend I can give this a go. I will post my findings. 2crazy, let me know if you have any luck with it if you get to it before me. I'm really hoping to be able to play some 720p video on my Atom box with that 8400GS :), guess we'll find out if it's possible.

Today, I've replaced my old mainboard with P4 CPU with D945GCLF2 (Dual Core Atom) mainboard. The PC runs so cool that I sould disable the case fans so I have a silent htpc on my living room. I put 2GB RAM on it and I'm using onboard graphics. I've tested 720P videos and there was no apearent problems. I' enabled lm-sensors and fan pwm to make it more silent. Now, the small fan on the chipset is not running all the time. 
I'm using the mainboard with Kubuntu 8.04 and using XBMC for media center. I'm using this htpc with an old 28" CRT TV. I could not get any video from the s-video port, so I'm using a VGA-TV converter to get video on TV. 
Did you manage to receive any video on s-video port?

---

### Post by what4893 on 2009-01-19
Just as a quick note for D945GCLF2 owners, I was experiencing frequent lock ups whenever I tried to do anything on the machine after boot. I was able to fix it by disabling Hyper Threading in the BIOS. Hope this help someone.

---

### Post by Betelgeuse on 2009-01-19
> **what4893 said:**
> Just as a quick note for D945GCLF2 owners, I was experiencing frequent lock ups whenever I tried to do anything on the machine after boot. I was able to fix it by disabling Hyper Threading in the BIOS. Hope this help someone.

When I first setup my D945GCLF2 mainboard, I was receiving random loackups too. I've disabled fan control from the bios, I set fan to run full speed in the bios menu and the random lockups disappeared. Now I'm using lm-sensors and pwm fancontrol in linux to control the fan. 

Disabling Hyper threading on this cpu makes bad performance.

---

### Post by Nygard on 2009-02-06
> **what4893 said:**
> mikespug thank you sooooo much :D

This worked like a charm. Now I can enjoy dual monitors and 720p movies :popcorn:

Can i know which ubuntu release are u using??? Ah, are you able to play also 1080p videos (probably not :()??? 
Just another question :p... What do you think about your video card???

Thank you ;).

---

### Post by what4893 on 2009-02-06
Hi Nygard,

I'm currently using Mythbuntu 8.10, I originally was plaything around with Ubuntu 8.04. Several things I had issues with when installing either of these version was with the network driver and the ACPI power manager process. When you first install everything seems great, but you will notice in ifconfig that you're dropping millions of packets, the second thing is that the ACPI process will suddenly spike to 100% and make the computer basically un-usable. So, the first thing is to disable that process, and second google for the driver for the network card. I found several sites that had scripts to automate the module install and blacklisting of the old module.

As far as my PCI graphics card, don't bother. It was a fun idea, but terrible in practice. The PCI bus is soooo slow that the computer was unable to keep the 8400GS GPU busy all the time because of the bandwith limitations of PCI. I am currently using the built in graphics with no regrets.

You may be surprised to hear this, but I can actually playback 720p without any trouble, and now I can playback some 1080p movies without any defects or sync issues. Certain films seem to be encoded at slightly higher bitrates and this will skip and lose audio sync very quickly, but others work quite well. The trick to getting this to work is to install the CoreAVC codec for Linux. There is a GoogleCode project hosting the necessary files. I highly recommend buying CoreAVC and using it. My 720p looks/runs much better now, and I can play most 1080p movies. The install for the CoreAVC Linux stuff was a little challenging (involves Wine), but I remember finding several posts on these forums about how to install it. With all of that installed I can actually record standard def TV on a tuner card on the Atom while watching a 1080p movie. Good Luck, and let me know if you need anymore help.

---

### Post by Betelgeuse on 2009-02-06
are you using the s-video output on this mainboard?
I have the same mainboard connected to a CRT TV and I could not get any video from this output. I'm now using a small vga to composite converter box to connect TV to the computer but &#305;'d prefer to use the s-video output. There were some driver issues but still I did not hear any solution.

---

### Post by what4893 on 2009-02-06
I too am using the VGA out, but to go directly into my LCD TV. I can't complain, the quality looks great to me. I haven't actually attempted to setup the S-Video out on the board, I have seen many other posts that users are having trouble getting it working due to driver problems as well.

---

### Post by Betelgeuse on 2009-02-07
> **what4893 said:**
> I too am using the VGA out, but to go directly into my LCD TV. I can't complain, the quality looks great to me. I haven't actually attempted to setup the S-Video out on the board, I have seen many other posts that users are having trouble getting it working due to driver problems as well.

if I had a LCD TV, I'd surely use the vga out diretly to the TV. Connecting a VGA port to LCD TV is way better than using the s-video output. But I have only an old CRT TV so only option for me is using s-video to SCART port on TV. Using a VGA to s-video converter works fine but the picture quality is not so good. 

I think, most of the people are using LCD TV and using the VGA connector to connect to the TV and there was not many old CRT TV left out there for developers to fix the s-video issue.

---

### Post by Nygard on 2009-02-07
> **what4893 said:**
> Hi Nygard,

I'm currently using Mythbuntu 8.10, I originally was plaything around with Ubuntu 8.04. Several things I had issues with when installing either of these version was with the network driver and the ACPI power manager process. When you first install everything seems great, but you will notice in ifconfig that you're dropping millions of packets, the second thing is that the ACPI process will suddenly spike to 100% and make the computer basically un-usable. So, the first thing is to disable that process, and second google for the driver for the network card. I found several sites that had scripts to automate the module install and blacklisting of the old module.

As far as my PCI graphics card, don't bother. It was a fun idea, but terrible in practice. The PCI bus is soooo slow that the computer was unable to keep the 8400GS GPU busy all the time because of the bandwith limitations of PCI. I am currently using the built in graphics with no regrets.

You may be surprised to hear this, but I can actually playback 720p without any trouble, and now I can playback some 1080p movies without any defects or sync issues. Certain films seem to be encoded at slightly higher bitrates and this will skip and lose audio sync very quickly, but others work quite well. The trick to getting this to work is to install the CoreAVC codec for Linux. There is a GoogleCode project hosting the necessary files. I highly recommend buying CoreAVC and using it. My 720p looks/runs much better now, and I can play most 1080p movies. The install for the CoreAVC Linux stuff was a little challenging (involves Wine), but I remember finding several posts on these forums about how to install it. With all of that installed I can actually record standard def TV on a tuner card on the Atom while watching a 1080p movie. Good Luck, and let me know if you need anymore help.

Thank you for all your answers :)! I was planning of buyin' a pci video card cause i've tried to play video files with various os.
I first tried to play videos with an xbmc ubuntu distro, but i had serious vsync problems also with divx!!! I've also tried with winxp and ubuntu 8.10, but I always received the same results... I'm using a configuration like yours, with the atom connected to an LCD TV and, as I said before, I'm unable to watch either Divx or Dvds :(... Anyway, thank you for all! Now I wanna try Mythbuntu and see if I can solve all of those problems... Ah, another question :D: do you have any vsync problem???

---

### Post by smov23 on 2009-08-08
Too get a pci video card to work you can try this.

1 change the MB jumpers to configuration mode.
2 add the pci video card.
3 set bios to load optimal and save
4 change jumpers back to normal

---

### Post by Terry Cunningham on 2010-01-21
Greetings, all.  I was experiencing the same problem as user what4893 with my "Jetway Atom-GM1 Flex ATX Motherboard Atom-GM1-330-LF".  This is a FlexATX motherboard with an Intel Atom 330, Intel 945GC + ICH7 chipset, one PCI-E x1 slot, and two PCI slots.

I've cut out the back of the PCI-E x1 slot and have a Geforce 8400GS PCI-E x16 card installed in the slot.  The motherboard BIOS has the option to either initialize "PCI" or "Onboard" video first, and with it set to "PCI" the 8400GS is used as the primary display adapter and POST information is shown via the 8400GS's output when I power up the computer.

With Windows XP and Windows 7, I can boot with the 8400GS installed, load the operating system and drivers, and use this machine without problems.  Both the onboard video and the 8400GS are shown as video adapters in Device Manager, though, meaning that the onboard video isn't being disabled when I plug in the PCI-E graphics card.  The 8400GS is detected as a PCI-E x1 device.

With Ubuntu and with CentOS, I can't install the operating system with the 8400GS installed.  The machine crashes shortly after I boot from the OS live/install discs.  I imagine this is due to the same issue experienced by what4893, and addressed by user mikespug, and mikespug's suggested fix worked for me and allowed me to install Ubuntu (THANK YOU MIKESPUG!!).

One thing to note, though.  I'm using Ubuntu 9.10, and it appears that you have to perform one more action in order for the driver blacklisting to work.  You have to issue the command (as sudo or root) "update-initramfs -u" after blacklisting agpgart and intel_agp.  After updating the initramfs, you can shutdown and install the graphics card.

So, thanks to all for the assistance!

---

