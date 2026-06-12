---
title: "Sound files (dev) lost!"
date: 2005-11-20
forum: Multimedia &amp; Video
---

### Post by xip on 2005-11-20
Hi all, first post, not shure this is the right thread(a friend told me to make a second copy if this post in this forum), but i hope it will do

sorry for my bad english, my home language is crapy cus of dyslexia, so a secondary language tends to get messy, pleas bear with me.

I had a fiew hard rebots after some problems with my pc not booting from cd(aperently its broken now) ... anyway.... it dosent mather, but when i finnaly started up ubunti again, the speaker whas gone from "system tray?" (i am an hardcore windows user, and a real noob at linux), evry media application i tryed complained on problems with sound, after some messing around i asked my friend to remotly try to work it out(he knows alot more than me about linux) ... after a while he found out that ALL files/directorys for sound files was gone ... but he did not know how to solve it.

/dev/dsp
/dev/sound
/dev/sound0

is all gone.

i cant work like this, and i Realy REALY need to get things working again, so if anyone with some skills whod explain in a linux-noob-friendly way how i can solve this, i whod be a very happy boy

like i wrote alredy, i suck hard on linux, and evry thing around it, but i think i have a SIS(Silicon Integreated systems) (that i gues is the one since i have an integreated sound card) into my mainboard.

we have tryed search for drivers and SIS key words with synoptic and google, but i dont found what i need.

anyone ho can help me find what i need, and explain how i can install/restore(?) it? i have only used synoptic for installing stuff on linux before.

im very happy for any help anyone can give me
tanx

/Xip

---

### Post by Teroedni on 2005-11-21
can you write in a terminal

sudo lshw

and post the result here?

---

### Post by xip on 2005-11-21
of corse!:)

pingu
    description: Computer
    capabilities: smbios-2.2 dmi-2.2
  *-core
       description: Motherboard
       product: SiS-745
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (11/25/2002)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 1500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          version: 6.8.1
          slot: Socket A
          size: 1300MHz
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse pni syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 768MB
          capacity: 1536MB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 256MB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM
             physical id: 2
             slot: A2
             size: 512MB
     *-pci
          physical id: e0000000
          bus info: pci@00:00.0
          version: 01
          clock: 33MHz
        *-pci
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             clock: 33MHz
             capabilities: pci bus_master
           *-display:0 UNCLAIMED
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: irq=5
           *-display:1 UNCLAIMED
                physical id: 0.1
                bus info: pci@01:00.1
                version: 00
                size: 256MB
                clock: 66MHz
                capabilities: bus_master cap_list
        *-isa UNCLAIMED
             physical id: 2
             bus info: pci@00:02.0
             version: 00
             clock: 33MHz
             capabilities: isa bus_master
        *-serial
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             clock: 33MHz
             configuration: driver=sis96x_smbus
        *-usb:0
             physical id: 2.2
             bus info: pci@00:02.2
             version: 07
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd irq=11
        *-usb:1
             physical id: 2.3
             bus info: pci@00:02.3
             version: 07
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd irq=11
        *-ide
             physical id: 2.5
             bus info: pci@00:02.5
             version: d0
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=SIS_IDE
        *-multimedia
             physical id: 2.7
             bus info: pci@00:02.7
             version: a0
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel irq=10
        *-network
             physical id: d
             bus info: pci@00:0d.0
             version: 10
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=8139too irq=11
  *-network:0
       description: Ethernet controller
       physical id: 1
       logical name: eth0
       serial: 00:50:22:c8:06:8a
       capabilities: mii autonegotiation 100bt-fd 100bt 10bt-fd 10bt ethernet
       configuration: autonegociated=100bt broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=217.210.6.47 link=yes multicast=yes
  *-network:1 DISABLED
       description: controller
       physical id: 2
       logical name: sit0

---

### Post by Teroedni on 2005-11-21
Can you check in Bios that sound is not disabled?

Can you check in Bios that pnp=no?

---

### Post by xip on 2005-11-21
have not seen a settings like that in bios, but i can check.
but even so, shod ther not still be a bunsh of sound dirs in DEV? (that is what my friend tells me)

UPDATE:
oky, i found a sound related option in BIOS, after setting it ON, the "plopp" sound at ubuntu login screen is back, but it gets stuck in a loop and repeatd like 10 times in a row, and then i gues it crashes the sound server, cus after that ther is never ever any more sound anywere.

after i have loged in, the speaker icon in system tray is back!, but ther is no sound in any application, movie or mp3 player, thay all give the same sound error as before.(volume at max and not muted of course)

i also looked for a PNP setting, ther was no boolean setting for this, ther where however an PnP/ (and then somthing else) that upend a sub menu, and ther was alot of settings ther i dont remeber ... but ther was not a no/yeas for PNP.

but atleast i feal a bit closer to a solution :)

PS: i also updated the system print abouve.

---

### Post by xip on 2005-11-27
Im still having problems with this, any one?

tanx in advance :)

---

### Post by Teroedni on 2005-11-27
could you start Alsamixer

In terminal write
```
sudo alsamixer
```

You use m to toggle off and on function.
Tab to shift beetwen sound device
and the direction key to raise and lower sound

Try to change things in thear , and see if you can get sound output;)


could you also give the output of 

```
sudo lspci
```


also try theese in terminal
```
gnome-sound-properties

```

Change on and off the sound here to see if you get some problems
It might be that you have multiple sound problem(i have had this problem

And i got even one more you can check
```
gstreamer-properties
```

is it set to alsa?
If not change to alsa and see if you get something out of it.

---

### Post by xip on 2005-11-27
Hi, and tanx for all you help!, im rely happy for any thing you can trow at me right now, geting very close to desperate :)

the alsamixer gives the same result as the gnome version(im guesing thay are the same software exept for gui)
thay give me graphical view and evrything looks OK in both, like i wrote before, volume is up and nothing is muted.

a friend alredy adviced me to shange to alsa, so i have tryed that alredy, in fakt, i have tryed all of them and the all turns out silent :(

gnome-sound-properties
works both in consol and in gnome, i have alredy tryed this and switshed sound deamon on/off with out result. (nomaly i have to switsh it several times a day anyway sence i use old and new sound softwares...)

gstreamer-properties
this i have alredy done the gnome way, and i tryed all of the different combinations, and it tells me "Failed to construct test pipline for 'ALSA ....' "

i hope this helps, tanx for any help you can give me, i realy need to get things working!:)

the lspci gives me this:
----------------------------------
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 745 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

-----

the "Unknown device 0016" looks very suspect to me, but what do i know?:P

---

### Post by Teroedni on 2005-11-28
here it is Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)

So ubuntu can detect it
What type of motherboard s this 
Brand=asusu?,Msi? or other?
Can you see if you could find the name for your motherboard

I did find a driver on the sis website here [http://www.sis.com./download/download_step1.php](http://www.sis.com./download/download_step1.php)
but it is kernel 2.4.x and only warty use 2.4.x

Could you do a reinstall 0f Ubuntu.
Yes you can probably get it to work without reinstall, but if you could reinstall(eg you are able to backup your data)
it would be much more easier than to try building new alsa  driver or recompile and such.

---

### Post by xip on 2005-11-28
hmmm.... no, well, if i can reinstall anything, i whod LOVE to rip this crap os out of my ma&#263;hine and install some nice and stable winXP (sorry!) hehe, you people might want to kill me right about now, but i have NEVER EVER have so mutch trouble on a workstation in my f**king entire life, and im sooooo tierd of it, shure it runs smother for a longer time, but my old xp-sp2 worked like a charm 24/7, and i hardly ever reboted.... and i sooo miss it... but, no, i cant install it, cus last time i tryed i had to do the install 5x times, each time the machine rebooted with Ubuntu OS from a nother driver(grrr, hate linux), after several retryes my cd broke... typical... so now i cant install xp nor ubuntu ... doh!
so i gues im screwd! :(
I wish i never shanged to linux, but sence im a programmer, i had to give it a try atleast once!;)

well, tanx for all your helpt anyway!

---

### Post by Teroedni on 2005-11-28
Please dont  give up:(

Could you at least give me the motherbrand name and model number ...please!!

I suspect that it may be some configs in bios which need to be fixed;)

Also with the motherboard name i could possible search for problems with this board, and i might be able to find a fix.


You dont need to reinstall it is just easier.But in your case it may be more difficult.
So please dont despair yet

---

### Post by xip on 2005-12-03
Hi there, and tanx for all your suport!:)

as far as i can read(and google), it is a:
Elitegroup K7S6A

hope that helps :)

/Xip

---

### Post by shandar on 2005-12-05
Well, I've been digging around in his computer through a remote connection to see if I could find out what was wrong. What I found was:
1. The soundcard works since it plays the startup sound on the login screen. 
2. The sound loops as if the soundserver/something-else-that-is-messing-up-the-soundcard is crashing. After that any attempt to output sound results in a "Unable to initalize <soundserver>" message or "[SIZE=2][COLOR=#000000][FONT=MS Sans Serif]/dev/dsp: Device or resource busy"[/FONT][/COLOR][/SIZE]. Would be interesting to boot in fail safe mode and skip GDM (which seems to be crashing the sound) then play a mp3 from the TTY with mplayer...
3. The device /dev/dsp is busy for some reason. I've been trying to find out what process is using it but I can't find anything. It's almost like Windows, when an application crashes the filesystem sometimes locks the file it was using...
4. Output sound as root doesn't work...
5. Running "sudo killall gdm" will crash computer bigtime :D

Odd thing is that the sound was working perfectly a week ago but after a reset (the hard way..) it died. Is it possible to reinstall sound drivers / ESD if a file is damaged?

---

### Post by Teroedni on 2005-12-06
double post:(

---

### Post by Teroedni on 2005-12-06
Yea i think so
Have you tried to *completely* remove the alsa package via synaptic
remove everything with alsa.**Reeboot**
Then installing it afterwards to see if the sound device get proper detected and used
You may need to load modules
I am not 100% sure about it

Can you try it
Thanks:)

By the way here is how it should look in bios , but i guess its already done:)

---

### Post by xip on 2005-12-20
after trying to reinstall ALSA, and rebooting, i ended up with ubuntu not starting correktly and could not use my pc for over a weak *nerverse breakdown*
i finnaly made things bootup and i must say that i have loost all intresrests in home-toying and trixing with settings, my pc simply means way to mutch for me, im only happt it works for now so i can write my code and do my work with out crawling on the walls.

however, if you find a simple (none dangerus) solution, dont hessitate to message me :)

tanx
Xip

---

