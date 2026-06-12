---
title: "Nvidia 6100"
date: 2005-10-31
forum: Multimedia &amp; Video
---

### Post by oldmarti on 2005-10-31
Any ideas howto make my NVidia 6100 video card run with ubuntu? 
NV driver don't work NVIDIA too. Only vesa driver ;-(

---

### Post by Teroedni on 2005-10-31
hmm interesting(i have wanted to try out 6100;)
Can your post the name on the motherboard and the rest of your computer specs
Can you post the xorg.conf file 
and can you post the xorg.log file you get when trying nvidia and nv please

for xorg
sudo gedit /etc/X11/xorg.conf
for xlog
sudo gedit /var/log/xorg.0.log

---

### Post by oldmarti on 2005-10-31
The motherboard is K8NF4G-SATA2 from asrock. Chip set is nVidia GeForce 6100 northbridge and nForce 410 MCP southbridge. Now I switch back to NV driver and after that to NVIDIA, to collect the logs and the error messages and post it in next message.

---

### Post by oldmarti on 2005-10-31
Here is logs from nv and nvidia

---

### Post by Teroedni on 2005-10-31
the log file fro nvidia doesnt report errors
(II) Primary Device is: PCI 00:05:0
(--) Chipset NVIDIA GPU found

what happends when your using nvidia
where do it stops?

as for nv driver
It can find your device
i think you can specifi it to use 6200 driver  with turbocahce
worth a try:)

---

### Post by Teroedni on 2005-10-31
Something i didnet think about
The 6100 integrated chipset is very new 

searched and found this sorry:(
[http://www.nvnews.net/vbulletin/showthread.php?t=57791](http://www.nvnews.net/vbulletin/showthread.php?t=57791)

you have to wait for 8xxx driver
Thats bad by Nvidia](*,) 

but try the 6200 driver with turbocache with nv, it may work
Else you have to revert to Vesa
But it should be possible to get better resolution and refresh rates with vesa too

---

### Post by oldmarti on 2005-11-01
Thanks! I'll wait for 1.0.8 driver from nvidia ;-(
but if I want to try the 6200 driver with turbocache with nv what I must to do?
My section in xorg.conf is:

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nv"
        BusID           "PCI:0:5:0"
EndSection

 where I must place 6200 and turbocache?

---

### Post by Teroedni on 2005-11-01
Here you go

But it probably wont work:(
Try setting defaultdepth at 16 also to see if that fixes anything.

Section "Device"
Identifier "GeForce 6200 TurboCache(TM)"
Driver "nv"
BusID "PCI:0:5:0"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"GeForce 6200 TurboCache(TM)"
	Monitor		"Generic Monitor"
	DefaultDepth	24

---

### Post by oldmarti on 2005-11-01
Thanks!
 I try everything, with 24 depth and with 16 depth. No difference - VGA don't work:) . 
The message is "no screen found".
Maybe I must wait the boys from nvidia and continue using vesa driver:)

---

### Post by Teroedni on 2005-11-01
well you can get vesa to work good also
Yust tell me if you need help

About the last line
Please remove it.I understand that you are mad at Nvidia, but dont stigmate one group because of Nvidia please.

---

### Post by lucdec on 2005-12-09
Hallo,
I have the same motherbord.
Is there already a solution ?

I am a totally newbe with linux.
I will install ubuntu 5.10 but it doesn't work
neither the install cd and the live cd.
It went wrong by the x server. 
I think it is my video card

It's the chipset Nvidia 6100.
Is this driver already supported in 5.10 ?

The installation abort every time and it says : can't
configure correctly the x server, correct it and
try again ?

How can i do that ?


A second question : I want make ubuntu working but also
XP
working on the same pc ?
Can that work ?

Lucdec
Sorry for my bad English

---

### Post by Teroedni on 2005-12-09
Yup the nvidia issue is fixed know
Can you reinstall Ubuntu,and we take it from there:)

As for dual boot i dont know
sorry:(  BUt i guess someone else here on the forum can give you tips regarding that:)

---

### Post by lucdec on 2005-12-10
Hallo, thank you.

I try again with the live cd.

When it went wrong, and the x server stopped,

i changed the device nvidia in vesa.

(sudo nano /etc/X11/Xorg.conf   
then after chinging into vesa : startX)

Now it works, but the sound doesn' work and I can't reach the 
internet.

This is my pc ::(Asrock K8NF4G-SATA2) 

Chipset - Northbridge: nVidia GeForce 6100 
- Southbridge: nVidia nForce 410 MCP 


Audio - Realtek ALC850 7.1channel AC'97 audio codec 

LAN - Realtek PHY RTL8201CL 
- Speed: 10/100 Ethernet 
- Supports Wake-On-LAN 

OS - Microsoft Windows 2000/XP/XP 64-bit compliant

---

### Post by weinstev on 2006-04-04
I'm not here offering advice, I'm here looking for it.

I've got an Asus A8N VM mobo (nVidia 410/6100 chipsets), 1GB of RAM, with a SATA 
drive on which is installed WinXP, and a 20GB IDE drive on which I'm trying to install
5.10 (Breezy Badger).  I launched the installer with the boot options

boot: linux noapic nolapic acpi=off

The installer gets to the point where it ejects the CD and tells me to reboot, which I do.

When grub starts up, I make sure that the line beginning with 'kernel... ' contains
noapic nolapic acpi=off

tell grub to boot, and then the installer continues unloading packages from the hard drive.

At some point, I am prompted for a list of screen resolutions to try.  I believe that 1024X?,
800x600, and 680x400 are the only items selected.  So, I hit the 'continue' option, and I
get a black screen of death - which the best as I can tell is a kernel panic of some kind,
complete with register dumps and stack trace.  

If I reboot and select the grub option that basically says "start up the installed kernel", the
installer pops up and tells me that there's a problem that I need to fix.  When I click 'ok', I
get the black screen of death.  

I tried selecting the "safe mode" option from the grub menu - which boots without starting up the x server -
and having a look at my
xorg.conf file.  However, it is exactly zero bytes in length.  I see references to modifying
the Driver definition to be "vesa", but I would also need to define the monitor and display
sections.  Since I don't have a sample xorg.conf from which to work, I was trying to sort it
out by just reading the xorg.conf man page.  I tried to startx and xinit, but these didn't
work, needless to say.

I'm wondering what my next step should be.  My ethernet driver is working, e.g. I can ping
[www.google.com](www.google.com), which means that I have the ability to apt-get necessary packages.

I can think of a few different possibilities:

1) the install has completed far enough that all I need to do at this point is come up with
a valid xorg.conf file (using "vesa" as the driver in the correct section whose name eludes
me at present) and then I should be able to startx.  Again, I'd need a valid sample xorg.conf
to work from if I have any hope of getting this to work.

2) even if I do 1, it seems like the installer is going to try and go back through the same
process and possibly undo what I've done with xorg.conf.  Therefor, I need to do a non
graphical install where I can line by line select how to configure the video (and every other
damn thing).  By the way, is there some way to do a more specialized install?  I believe that
for the Live CD, there is some sort of live-expert mode.  Is there something similar for the
installer?

3) run the server installer which may not try to set up the video driver (or maybe it will?)
and go through the process of figuring out how to do the full workstation install manually
later on.

I would really appreciate any help that anybody can offer.  I've spent a fair amount of time
installing (and reinstalling) and I would like to start getting a little something for my efforts!

---

### Post by Teroedni on 2006-04-05
Hey could you try the Dapper cd instead. Dapper have better support for newer hardware and therefore may work better for you.

Dapper s still **_[COLOR=Red]alpha status[/COLOR]_**, but for the most cases it is a better product,and may be neccesary for your computer to work.

[http://www.ubuntu.com/testing/flight6](http://www.ubuntu.com/testing/flight6) info about the latest dapper flight 6 cd:)


[http://cdimage.ubuntu.com/releases/dapper/flight-6/](http://cdimage.ubuntu.com/releases/dapper/flight-6/)   <---download Dapper

---

### Post by weinstev on 2006-04-05
Ok, well maybe I will simply give the Dapper Drake release a try instead.  I tried the
"expert" install option,  but had the same failings.  However, I did meet with a little 
more success.  I selected recovery mode in the grub menu, and tried to dpkg-reconfigure xserver-xorg.  This failed because dpkg hadn't been properly installed, and I had to run
some other command to get it updated.  Then, I was able to dpkg-reconfigure xserver-xorg.
Next, I changed the Driver "nv" line in xorg.conf to Driver "vesa" and then typed startx.  
Surprisingly, gnome started right up, I was able to browse using Firefox, everything seemed
pretty good.  

I then tried rebooting and selecting the "normal" boot option from the grub menu.  After I
logged in, the installer took over and then crashed with kernel panic output as before.  This,
time, the screen background was blue, an ominous sign...

Anyway, it seems like if there was some non-graphical way to do the installation, I would
be in good shape.  As it is, I appear to be stuck in an endless loop until I can figure out why
the Ubuntu installer continues to try to run when I log in, and how I can "convince" the
installer to leave me the f*** alone.  Prior to downloading the Dapper CD, I may try and
do the server install, and try and figure out what packages are missing if that works out
ok.

I'm sharing my experiences in case others go through the same thing.

Thanks for the suggestion regarding D. Drake Flight 6.  I may have to go down that route.

Vic

---

### Post by TrancëJay on 2006-04-17
[color=red]And Kubuntu users?[/color]

---

### Post by Tombius on 2006-06-04
Hi, i am new around these parts:confused: , Just today i gave a try to Ubuntu 5.10, seems like new hardware like Nforce 6100 just doesn't seems to work](*,) , what about users with the 6.06 version, any better luck? :-k [-( it seems like it is even worse, so my advice is, lets just say thanks and goodbye to 5.10 :-| and break our heads with the newest version, in any case, we will end up using it sooner or later. Dont you think?

---

### Post by Teroedni on 2006-06-04
Yea try the latest Dapper(Ubuntu 6.06) it is much better:)

---

### Post by mikeh on 2006-06-14
Some information:

I have the Asrock K8NF4G-sata2 motherboard.
The vesa drivers in 5.10 work for a while, but are unstable. Do not use!
The latest nvidia binary drivers (from Dec'05?) work fine.

Dapper has both the open 'nv' and binary 'nvidia' drivers support the 6100.
So all is well. I havn't tested the new vesa driver.

---

