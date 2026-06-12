---
title: "Hardware Compatible Video Cards"
date: 2005-11-21
forum: Multimedia &amp; Video
---

### Post by Teroedni on 2005-11-21
I need to gather information on Graphics card for use on this wiki [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

I ask therefore user her to post their experience with graphicscard they own.
Include the
1.The type of card:Agp,pci,pci-express or Isa  
2.brand 
3.model number
4.the status of the card:Working ,problems, working to some degree etc
5.And if you have to due some tweaking to get your card working please create a thead for it and link it here:)
6.If you card have problems please include a link to the post where you have asked for help. This will help you get help faster;)


Thanks for all contributions:)
Regards Teroedni

---

### Post by frodon on 2005-11-21
Hi teroedni,

I use a nvidia FX5200 PCI card with the ubuntu nvidia drivers and never had any issues with this hardware. It just works fine !

---

### Post by Pablo_Escobar on 2005-11-21
1. AGP
2. Gigabyte
3. GV-R955128D (128 MB, 128-bit, TV-OUT, DVI)
4. Works out of the box, Repo fglrx drivers work flawlessly
5. No tweaking yet :D

---

### Post by xmastree on 2005-11-21
I've had successes so far with:
TNT Geforce-4 AGP (no surprises there)
Voodoo Banshee AGP
Intel 810 (built in to mobo)

All worked fine out of the box. No tweaking required although I did install the Nvidia drivers.

---

### Post by teaker1s on 2005-11-21
sparkle(nvidia geforce4 mx 128mb) works flawlessly with opengl and nvidia driver so far

---

### Post by oskude on 2005-11-21
an AGP "noname" ATI Radeon 9250 SE 
(dont have the package anymore, but i look if the brand is written on board, next time i open my pc)```
lspci -v
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01) (prog-if 00 [VGA])
        Subsystem: PC Partner Limited: Unknown device 0260
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
        Memory at c0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at b800 [size=256]
        Memory at cfef0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at cfec0000 [disabled] [size=128K]
        Capabilities: [58] AGP version 2.0
        Capabilities: [50] Power Management version 2
```works out of the box with autoconfigured "ati" driver
"radeon" and "fglrx" drivers both work too

---

### Post by Teroedni on 2005-11-22
Xmastree 
thanks i will add them:) 

Thanks for the contrib:)


And Teaker 
Could you tell me if its ann Agp or Pci card?
Thanks :)

I really appreciate this
Thanks to frodon, Pablo_Escobar, xmastree, teaker1s, oskude:)

And if others have card not listed here Please include them:KS

---

### Post by xmastree on 2005-11-22
[QUOTE=Teroedni]Xmastree 
Could you give some more information about your Voodoo Banshee card
Both 2d and 3d works?
What driver are you using?[/quote]Erm, not sure about 3D. :rolleyes:  It's in a server. Waste of a half decent card actually, but it's all I could find lying around. As for the driver, I'll take a look next time I'm in the office.

Edit: is this what yoiu need? From xorg.conf:
```
Section "Device"
        Identifier      "3Dfx Interactive, Inc. Voodoo 3"
        Driver          "tdfx"
        BusID           "PCI:0:15:0"
        Option          "UseFBDev"              "false"
EndSection
```
> And the TNT Geforce 4
What type of geforce 4?128MB MX440 (is that what you meant?)

---

### Post by qrazi on 2005-12-03
1.AGP
2.3Dfx
3.Voodoo5 5500 64MB
4.2D works without any problems. Didnt have to mess around with config files to get the right resolution. 3D hardware accelleration not at all tough. still have to figure if thats possible or not. 
5.as of now, not yet.


1.AGP
2.Diamond SPeedstar 540 III (i think it was)
3.S3 Savage4 16MB
4.2D works without any problems. 3D hardware accelleration trough DRI drivers work. Gets me ~450fps in GLX gears, and i can run Cube at reasonable speeds.
5.Used the How-to for Savage cards.

---

### Post by alastairj on 2005-12-03
0. OS/computer: Ubuntu Live CD v. 5.10 on Sony Vaio PCG-U1
1. AGP
2. ATI 
3. Radeon Mobility M6 LY
4. with x.org driver radeon: X works OK, but on switching to virtual terminal (ctrl-alt-F1) the screen becomes brighter and brighter until all characters are invisible. This also happens if I reboot or shutdown from an X terminal.

- Alastair Jenkins

---

### Post by oskude on 2005-12-04
[QUOTE=alastairj]4. with x.org driver radeon: X works OK, but on switching to virtual terminal (ctrl-alt-F1) the screen becomes brighter and brighter until all characters are invisible. This also happens if I reboot or shutdown from an X terminal.[/QUOTE]i have had this kind of problems too, and experimenting with the virtual terminal (and/or xorg) resolution and color depth this dissappeared... maybe they both have to be the same color (bit) depth...

---

### Post by petri on 2005-12-04
1. AGP
2. Hercules
3. Radeon 8500DV AIW
4. Not working. When I installed fglrx-drivers = hard freeze
5. Nobody helps me :( 

Teroedni, how's your card doing?

---

### Post by Teroedni on 2005-12-20
I need more cards here:rolleyes: 

bump

---

### Post by AthlonMDK on 2005-12-23
Hercules ATI 9800SE AIW AGP 128MB
2D - Works Flawless
3D - With fglrx works flawless 
AIW - Not working -> /dev/video0 not found

All on xorg 6.8 (breezer)
resolution : 1600x1200

---

### Post by Teroedni on 2006-01-05
Thank You Athlon Mdk
It has been added:D 


People i need more cards please post them so the doc get better:)

I also very much would like to hear about cards that not are working
If you have a problematic video card  please post it here with a link to you thread:)

---

### Post by shof2k on 2006-01-06
0. Ubuntu 5.10 (breezy) installed from CD
1. Built in to motherboard 
2. Intel
3. 845GM/GL/G series
4. Install works but defaults to 640x480 resolution.  Need to edit Xorg.conf to use 1024x960.
5. The supplied i810 drivers works ok, but for additional performance you need the modules from freedesktop.org.  (Note that the december 2005 versions are not giving hardware acceleration yet :( )

---

