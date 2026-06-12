---
title: "Karmic Koala doesn't 'find' ATI video card."
date: 2010-02-07
forum: Multimedia Software
---

### Post by semperlinux on 2010-02-07
Hi Forum,

I'm trying to get the screen graphics working correctly on a newly purchased ACER Aspire 7740G laptop. It has a 17.3" 16:9 screen with an ATI Radeon Mobility HD5470 512MB graphics card.

The command LSPCI in Terminal gives.....

"02:00.0 VGA compatible controller: ATI Technologies Inc Device 68e0"

I've also uploaded /var/ log/ xorg.0.log.

In System/Preferences/Display the pink coloured monitor screen has 'UNKNOWN' displayed on it with only 3 resolutions available.

I installed the ATI Catalyst Control centre but when it initialises, it produces an error saying that there is no driver installed  - I thought the XORG log shows that the driver is installed.

The command ATICONFIG in Terminal reports.........

"aticonfig: No supported adapters detected" !


Be grateful for any hints how I can sort this

Many thanks
Semperlinux

---

### Post by markbuntu on 2010-02-07
There is no driver out yet to support the Mobility 5470, it is too new. You will need a driver from here

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

but even the latest one there does not list the 5470 as supported so you will have to wait and hopefully next month's driver release 10.2 will have support for it.

This happens with the latest greatest stuff.

---

### Post by semperlinux on 2010-02-07
Thanks for the reply Markbuntu.

You're right enough in what you say but I downloaded and installed 10.1 anyway.

Terminal wouldn't let me run ATICONFIG as it still said there was no adapter present. I then tried System/Administration/Hardware drivers and up popped the newly installed 10.1.
The system said there was another driver already in use but I was given the choice of using the proprietary one so I selected the new one.

The display immediately changed to what I reckoned was working. I went and checked System/Preferences /Display and there was the correct resolution (1600 X 900) with choices available.
The driver is actually working correctly  - what puzzles me though is how the System can still tell me there is "no adapter present" and I still have not been able to run ATICONFIG !!

Bit of a mystery.

---

### Post by markbuntu on 2010-02-07
There is most likely preliminary support in the driver but it is not fully implemented yet. This is fairly common for very new gpus. You can go to the phoronix forums and ask about progress, some of the ati devs hang out there. It is a good place to keep up on what is going on.

---

### Post by semperlinux on 2010-02-08
Thanks for the info Markubuntu.

I'll have a look at phoronix and will likely give the 10.2 version a try when it comes out.

However, I don't quite see how the correct driver loaded correctly will solve the 'no adapter present' problem.
As I understand it, the OS must identify the hardware FIRST then the boot process can correctly associate the driver and then load it in to memory.

I see that as an Ubuntu problem not ATI.

Thanks for your input

---

### Post by sleepitoff on 2010-02-12
For the record, you've got the correct resolution working now, right? I'm getting a new Asus laptop in a few days that has the ATI 5470 gpu as well. While I know the linux community generally looks down on ATI for their driver support, I went for a laptop with this ati card anyway. I can wait for better support for a while if I can at least get it running in the highest resolution.

---

### Post by thisone on 2010-02-12
I might add that I've also bought a laptop with the HD 5470 card. I experienced exactly what semperlinux described in the original post. But unfortunately no drivers appeared in Ubuntu's Hardware Drivers tool, so I'm not even able to change resolution.

I'll be watching this thread, so please reply if you get anywhere.

---

### Post by semperlinux on 2010-02-12
Thanks for the replies.

What to do is download the '4000' series driver from AMD and bung that in - you'll get most of the functionality with that driver.
Plenty of different resolutions although the 1600 x 900 gives a very acceptable display - and its nice and fast.

I contacted AMD but it must have been a real no-brainer on that day as they advised me to contact Acer !!!
I replied asking for a bit better technical support rather than just shunting me off to Acer - hopefully I'll get a more sensible answer in a day or two.

If anything interesting turns up, I'll post it here.

Hope you enjoy your new laptops - so far, I'm delighted with the Acer.
6 hours after taking it out the shop, I'd backed up the Windows system, re-sized the partitions and had a lovely dual-booting machine (Win7 & Karmic koala) - both systems running perfectly (except for the graphics card in Linux !! Oh well !

---

### Post by sleepitoff on 2010-02-12
Thanks for the tip, semperlinux, I'll be sure to give the 4000 driver a try when my laptop comes. 

Also, this appears to be the only thread regarding ATI's 5470 graphics engine for the time being, and the only search result for googling "linux ati 5470" or variants of that that comes up with any info, so I'll keep this thread on watch, too.

---

### Post by Melcar on 2010-02-12
Karmic won't detect it because it's too new; the driver that Karmic provides doesn't support the chip.  The latest AMD driver (10.1) supposedly supports the chip (it should at least give you proper modesetting support).  The 10.2 driver should have official support though (hopefully).

---

### Post by hyde0429 on 2010-02-12
After researching issues with ATI Graphics drivers, I have noticed that the new version of Ubuntu (Lucid Lynx) will have added support at the kernel level for a slew of older chipsets that AMD has discontinued support for. The Newest chipsets will likely have a driver by then as well. Yay!

For most ATI graphics users, biting the bullet and installing the catalyst drivers is the best option. However, this makes VNC to that desktop go wonky when you enable desktop effects. Par for the course with proprietary drivers. Just disable desktop effects when you want to remote to it and you'll be good. 

I have a Mobility Radeon HD chipset as well (laptop is about 10 months old), and although Linux Mint 8 picks it up and gets the display setting right, I use the 10.1 Catalyst drivers as well since they include snippets of code that the Open Source community has to reverse-engineer to do. Too bad AMD doesn't partner with Canonical to ensure better support. Not profitable I guess. When will they get that convenience = profit?

---

### Post by hyde0429 on 2010-02-12
>  The driver is actually working correctly  - what puzzles me though is how the System can still tell me there is "no adapter present" and I still have not been able to run ATICONFIG !!

Bit of a mystery.


This is because the ATI Catalyst drivers max out the resolution and lock out the user from modifying the display resolution by default upon installation. When the ATI Catalyst drivers install, you will have two new shortcuts in your menu, ATI Catalyst Control Center, and one that is an Admin mode of the same thing. 

GNOME Display preferences only allow you to modify settings of the X server itself. Since your driver is a patch to the kernel, the admin panel for that driver is also going to be proprietary. This means that in order to play with your settings, you will need to access the ATI Catalyst Control Center in Admin Mode by clicking the shortcut.

---

### Post by Melcar on 2010-02-12
You can use xrandr to change resolutions.  Just run it from a terminal as a regular user.

---

### Post by sleepitoff on 2010-02-17
Any tips on getting the 10.1 driver for the 4000 series to install? I've tried a few times, but just ends in countless errors and I'm limited to 800 x 600 resolution on the time being, which becomes a bit mind numbing after some time. 

Hopefully ATI gets the new catalyst out sometime soon, I don't want to boot into Windows 7 if I don't have to.

---

### Post by markbuntu on 2010-02-17
I just made a how to for installing/fixing the ati drivers for ati cards. This procedure has been tested by a lot of people on a lot of Ubuntus.


[http://ubuntuforums.org/showthread.php?t=1409467](http://ubuntuforums.org/showthread.php?t=1409467)

---

### Post by Yellow Pasque on 2010-02-17
> **semperlinux said:**
> However, I don't quite see how the correct driver loaded correctly will solve the 'no adapter present' problem.

It's just a misleading error message. It really means "the driver could not find a known ATI product" and you should be more worried if lspci doesn't show your card.

This command might help lspci to give a proper name to your card
```
sudo update-pciids
```

---

### Post by sleepitoff on 2010-02-17
Everything works okay with the 4000 series driver, with the exception that you can't use desktop effects and there's a watermark stuck on the bottom right hand corner displaying "AMD Unsupported hardware" 

Now, I understand that this isn't the right driver for the 5470 and things like desktop effects won't work and I'm happy enough to just be the correct resolution, but how can I get rid of that watermark until the new driver gets released?

---

### Post by monraaf on 2010-02-17
What makes you think ATI is going to release a special driver for your card? I've never heard of that. They just add support for new cards to Linux Catalyst. Latest release is 10.2, and it's very buggy so I've heard :lolflag:

---

### Post by sleepitoff on 2010-02-17
Thanks for the info, that'll be sure to get the watermark off my screen.

---

### Post by GraceDivine on 2010-02-17
Try this: (taken from my post on Phoronix)

Just download the original 9.12 linux driver and instead of the --buildpkg switch, use --extract fglrx. 

In the newly extracted fglrx folder, find the two files _control_ and _signature_ and then copy them to /etc/ati. Reboot and the watermark should not be there.

---

### Post by sleepitoff on 2010-02-19
Bummer, that trick didn't work. 

Maybe with 10.2 you need a different trick to get rid of the watermark.

---

### Post by Kurotowa on 2010-02-21
> **thisone said:**
> I might add that I've also bought a laptop with the HD 5470 card. I experienced exactly what semperlinux described in the original post. But unfortunately no drivers appeared in Ubuntu's Hardware Drivers tool, so I'm not even able to change resolution.

I just bought a new laptop with a 5470, too (asus k52jr), and at first no proprietary drivers were showing up in the Ubuntu HW Drivers tools search.

Since the 10.2 driver is not provided by Ubuntu yet, I wanted to install it manually anyway.
I did this but the driver was not installed, though modprobe fglrx worked OK, maybe because aticonfig did not find any device. I could have come up with a xorg.conf for it, but I was unsure whether something else would be needed or not.

I don't know if it's related to the failed 10.2 install, but now the 10.1 driver was showing up in the search, so I installed it, but again after a reboot Ubuntu told me the driver failed to load. Indeed when inserting fglrx manually with modprobe I got "unable to allocate memory" related to the kernel module /lib/modules/2.6.31-19-generic/updates/dkms/fglrx.ko.

So now I had a server configured with a buggy driver, instead of an uninstalled working driver ;-)

The next logical step actually worked: I just re-ran the 10.2 install to overwrite the 10.1 modules, and to my greatest relief, I now had a working server with a correct resolution.:)
I had a few worrying glitches when the screen came back on after blanking, but now it goes off and on correctly, so I will just cross fingers it does not happen again...

Two things are left, though:

[LIST]
[*]remove the watermark (I'll try what I read in this thread)
[*]plug in the extra LCD panel at its full resolution (this is critical for the intended use of this machine...)
[/LIST]
To be continued...

---

### Post by Kurotowa on 2010-02-21
Update:

[LIST]
[*]The external monitor "works" somehow, though setting it up in the catalyst app crashed my session a few times.
[LIST]
[*]Plugged with the SVGA cable I could not go above 1280x768 without rebooting, and after a reboot setting 1920x1200 crashed my sessions until I found a screen & desktop combination that asked me to reboot (again), and it finally worked.
[*]At some point I wondered why I could launch the catalyst app as admin without typing my password and launched it with sudo from the command line (sudo amdcccle), but I'm not sure it's related to it finally asking me to reboot.
[*]Or maybe I clicked "OK" instead of "Apply"...
[/LIST]
 
[*]Did not tackle the watermark issue, that'll have to wait.
[*]Glitches appeared again, indeed at each logon the display is completely schmucked up, until I launch an application in fullscreen.
[LIST]
[*]Wouldn't be surprised to discover it is related to the fact that I use a netbook-remix setup 'coz it already did fancy things to the display (and crashed a few times) on another laptop of mine.
[*]Simple workaround: launch anything fullscreen, eg. a terminal, then go the System->Preferences->Startup applications, go to Options tab, click "Save applications currently running in my sessions" (or something like that). At subsequent logons, the glitches no longer occur ^_^
[/LIST]
 
[/LIST]
Now I believe I earned my diner!
Cheers,

---

### Post by sleepitoff on 2010-02-22
I bought a k52jr as well (the k52jr-a1). Digging this notebook quite a bit. 

No problem with an external monitor with the correct resolution on my end.. Both VGA and HDMI worked fine.

---

### Post by chill32 on 2010-02-22
Wierd i use an ati card and it works perfectly, uhm I don't know what to say.:confused:

---

### Post by raccoss on 2010-02-28
> **Kurotowa said:**
> 

I don't know if it's related to the failed 10.2 install, but now the 10.1 driver was showing up in the search, so I installed it, but again after a reboot Ubuntu told me the driver failed to load. Indeed when inserting fglrx manually with modprobe I got "unable to allocate memory" related to the kernel module /lib/modules/2.6.31-19-generic/updates/dkms/fglrx.ko..

Sorry, can you help me? I'm a newbie.
I have the same computer you have.
How can I use modprobe?

Thanks

---

### Post by Kurotowa on 2010-03-06
Hi,

You use modprobe when you need to manually load a module (here a hardware driver) into the linux kernel. Of course you need super-user privileges to do that so, if you're trying to load the fglrx module for the ati card, open a terminal and type this:

```
sudo modprobe fglrx
```To unload the same module:

```
sudo rmmod fglrx
```To list already loaded modules:

```
lsmod
```If in doubt, to confirm fglrx is actually loaded...:

```
lsmod | grep fglrx
```...should return something like "fglrx                2279896  46"

You don't actually need those commands to have the driver run as I did, it's just a diagnosis tool. Just install the 10.1 from Ubuntu repositories and then run 10.2 install from ATI website manually to overwrite the 10.1 module.

You might want to read those also:
 * [http://ubuntuforums.org/showthread.php?t=1402076](http://ubuntuforums.org/showthread.php?t=1402076) to have wired ethernet working
 * [http://swiss.ubuntuforums.org/showthread.php?p=8920850](http://swiss.ubuntuforums.org/showthread.php?p=8920850) to remove the watermark, once the ATI driver works

hope this helps,

---

### Post by raccoss on 2010-03-12
> **Kurotowa said:**
> 



You might want to read those also:
 * [http://ubuntuforums.org/showthread.php?t=1402076](http://ubuntuforums.org/showthread.php?t=1402076) to have wired ethernet working
 * [http://swiss.ubuntuforums.org/showthread.php?p=8920850](http://swiss.ubuntuforums.org/showthread.php?p=8920850) to remove the watermark, once the ATI driver works

hope this helps,

Thank you for you explanation but it still doesn't work. I tried installing the 10.1 drivers with the procedure of [markbuntu]("http://ubuntuforums.org/member.php?u=566591"). Everything seems to go ok, but when in the end I try to launch aticonfig it says something like "no device" (or something like that, actually I'm at work).

---

### Post by raccoss on 2010-03-14
To explain myself better, I found the Catalyst 10.1 

ati-driver-installer-10-1-x86.x86_64

It seems that installation went ok, but when I try 

```
aticonfig
```

it says

```
aticonfig: No supported adapters detected

```

---

### Post by Yellow Pasque on 2010-03-14
Before you start:
```
sudo update-pciids
```
Then try it again using Catalyst 10-2
Also you might want to:
```
sudo aticonfig --initial -f
```

---

### Post by sgb77 on 2010-03-24
Hello all,
I need your advice, I am looking to buy a new asus laptop and I do not want to use Window$ anywhere near my computer. So the question is, should I purchase the asus I am looking for which has the ATI Mobility Radeon HD 5470 in it, or should I look at a notebook with an nvidia card, since it seems to be more linux friendly, I am using one right now in my machine and I love it.

Here are my basic requirements, I need the display not to be too buggy, as far as flickering, trhowing errors for no apparent reason and the like. 
I need to be able to connect my external monitor and use it as an extension of my laptop display.
Would be nice to be able to use compiz, but not requiered.

Please let me know if the ATI/ubuntu combination would accomodate my minimum requirements or if I should just look for a laptop with an Nvidia GPU.

Thanks for any helpful advice in advance..

---

