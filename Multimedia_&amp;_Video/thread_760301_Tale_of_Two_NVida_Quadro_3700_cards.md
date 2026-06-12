---
title: "Tale of Two NVida Quadro 3700 cards"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by narraal on 2008-04-20
Hi all,

I am trying to install 2 Nvidia Quadro 3700 cards in my computer (eventually with SLI). These cards are replacing a Quadro 1700 card.

uname -a returns

LINUX computername 2.6.22.14-generic #1 SMP Sun OCT 14 21:45:15 GMT 2007 x86_64 GUN/Linux


The computer was running really nicely with the 1700. Once I installed the cards, when booting Ubuntu, I just get a blank screen forever. Since I was running the nv driver, I figured I should get the latest NVidia driver. So the steps I then took were

downloaded NVIDIA-Linux-x86_64-169.12-pkg2.run from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
booted in the recover mode
init 3
installed the driver
startx

All this worked ok, and the NVidia control panel could see the two cards. Then I rebooted.

I again got the blank screen forever.

Rebooted into save mode.
init 3
startx

and it failed with some error - sorry cannot remember.

Booted in to recovery mode
installed the driver

Found a new driver

[http://www.nvidia.com/object/linux_display_amd64_171.06.html](http://www.nvidia.com/object/linux_display_amd64_171.06.html)

 (why [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) does not find this is beyond me)

sh NVIDIA-Linux-x86_64-171.06-pkg2.run

startx

and all it good.

/proc/drivers/nvidia

seems to show everything I expect.

Reboot in normal mode - argh   blank screen forever again :-(
reboot in recovery mode
init 3
startx

and I get

(WW) NVIDIA: No matching Device sectoim for instance (BusIS PCI:1:0:0) found
(II) Module already built in
Error: API mismatch: this NVIDIA drive component has version 171.06, but the NVIDIA kernel module's version does not match.
Please make sure that the kernel module all all NVIDIA driver components have the same version.
(EE) NVIDIA(0) Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0)      that there is a supported NVIDIA GPU in this system, amd
(EE) NVIDIA(0)      that the NVIDIA device files have been created properly.
(EE) NVIDIA(0)      Please consult the NVIDIA README for details.
(EE) NVIDIA(0)      *** Aborting ***
(EE) Screen(s) found, bt .......

If I right now do

sh NVIDIA-Linux-x86_64-171.06-pkg2.run
startx

everything works again

Ok, I am totally lost. What am I doing wrong :-(
I guess the more important thing is how to I debug / get logs of what is happening in a normal boot

Thanks in advance,
narraal

---

### Post by narraal on 2008-04-20
Whilst I have X Windows working, I can show some more details of my system rather than having to run a second "Windows" box beside me to post :-(

root@computername:/etc/X11# lspci
00:00.0 Host bridge: Intel Corporation Memory Controller Hub (rev 20)
00:01.0 PCI bridge: Intel Corporation PCI Express Port 1 (rev 20)
00:05.0 PCI bridge: Intel Corporation PCI Express Port 5 (rev 20)
00:09.0 PCI bridge: Intel Corporation PCI Express Port 9 (rev 20)
00:10.0 Host bridge: Intel Corporation FSB Registers (rev 20)
00:10.1 Host bridge: Intel Corporation FSB Registers (rev 20)
00:10.2 Host bridge: Intel Corporation FSB Registers (rev 20)
00:10.3 Host bridge: Intel Corporation FSB Registers (rev 20)
00:10.4 Host bridge: Intel Corporation FSB Registers (rev 20)
00:11.0 Host bridge: Intel Corporation Unknown device 4031 (rev 20)
00:15.0 Host bridge: Intel Corporation FBD Registers (rev 20)
00:15.1 Host bridge: Intel Corporation FBD Registers (rev 20)
00:16.0 Host bridge: Intel Corporation FBD Registers (rev 20)
00:16.1 Host bridge: Intel Corporation FBD Registers (rev 20)
00:1b.0 Audio device: Intel Corporation 631xESB/632xESB High Definition Audio Controller (rev 09)
00:1c.0 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 (rev 09)
00:1d.0 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 (rev 09)
00:1d.1 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 (rev 09)
00:1d.2 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 (rev 09)
00:1d.3 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #4 (rev 09)
00:1d.7 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller (rev 09)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d9)
00:1f.0 ISA bridge: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller (rev 09)
00:1f.1 IDE interface: Intel Corporation 631xESB/632xESB IDE Controller (rev 09)
00:1f.2 SATA controller: Intel Corporation 631xESB/632xESB SATA AHCI Controller (rev 09)
00:1f.3 SMBus: Intel Corporation 631xESB/632xESB/3100 Chipset SMBus Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 061a (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 061a (rev a2)
03:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Upstream Port (rev 01)
03:00.3 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express to PCI-X Bridge (rev 01)
04:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E1 (rev 01)
04:01.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E2 (rev 01)
05:00.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1068E PCI-Express Fusion-MPT SAS (rev 08)
06:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 21)
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
09:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
root@STRONTIUM:/etc/X11# lspci -t
-[0000:00]-+-00.0
           +-01.0-[0000:01]----00.0
           +-05.0-[0000:02]----00.0
           +-09.0-[0000:03-07]--+-00.0-[0000:04-06]--+-00.0-[0000:05]----00.0
           |                    |                    \-01.0-[0000:06]----00.0
           |                    \-00.3-[0000:07]--
           +-10.0
           +-10.1
           +-10.2
           +-10.3
           +-10.4
           +-11.0
           +-15.0
           +-15.1
           +-16.0
           +-16.1
           +-1b.0
           +-1c.0-[0000:08]----00.0
           +-1d.0
           +-1d.1
           +-1d.2
           +-1d.3
           +-1d.7
           +-1e.0-[0000:09]----0a.0
           +-1f.0
           +-1f.1
           +-1f.2
           \-1f.3
root@STRONTIUM:/etc/X11#


Also, Monitor and Display - System settings:

is showing my graphic cards running "VESA driver (generic), So maybe I am not running the NVidia drivers at all. 

Yep, Confused.

---

### Post by narraal on 2008-04-20
One more thing: in

Monitor and Display - System settings

when I try to configure the graphics card, under NVidia, I don't have any driver for the 3700: only lots of GeForce cards.

---

### Post by tempo500 on 2008-04-20
hey,

unfortunaly i cant help you..no linux guru.  i want to buy the quadro 3700 because my 3500 broke. could you be so kind and let me know if you could get the card to work? its listed as supported by nvidia. maybee you should give it a try with a single card/without sli...phil

---

### Post by narraal on 2008-04-20
Ok, the puzzle deepens. I now only have one 3700 card in the computer. Trying to use the Kubuntu Install CD, as soon as I choose Run/Install Kubunto, I get the first kernel alive message, then after that nothing. The problem seems to be that "Kubunto 7.10" will not work with a 3700? Once I put the 1700 card back in the computer, Run/Install is fine.

Additional information seems to suggest I should be posting on NVidia's website. See

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

and

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Anyone?

---

### Post by narraal on 2008-04-21
Nor does Kububtu 8 Release Candidate. I just tried OpenSUSE 10.3 and at least I can start installing.

---

### Post by tempo500 on 2008-04-21
puh... that does not sound good. i bought the 3700 card yesterday and will get it in 2 days. all official sources say that its supported! i hope you find a solution! besides the geforce 8800gt has the same g92 gpu. has anyone problems with this card? phil

---

### Post by tempo500 on 2008-04-21
hey look at [http://ubuntuforums.org/showthread.php?p=4187870&highlight=8800+gts&page=2]("http://ubuntuforums.org/showthread.php?p=4187870&highlight=8800+gts&page=2")


looks like your problem...

---

### Post by bijeeshvs on 2008-04-21
hello buddy i got the same problem but with a single card (nvidia) al was going the same like you mentioned. but i was able to correct my problem wit the installation of a software called "Envy" it takes care of your driver installation it automatically downlods the appropriate driver and installs it and also configures it no worries . i had a 17" monitor after the installation i had to set the refresh rate in the screen and cards (the default one in gnome0) now its no problem at all, here is the link to the software definetly its worth a try

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by tempo500 on 2008-04-22
so... any luck?

---

### Post by bijeeshvs on 2008-04-22
hi guys i am pretty unsure about my suggestion did any help to you people, so please let me know did it worked or not. If it worked don't deny the satisfaction it will give to us

---

### Post by narraal on 2008-04-22
Sorry guys, after I installed the NVidia driver, tried un-installing it, using apt-get etc etc, I ended up with a mess. So I thought I was safe because I had Acronis'd the partition before all of this. Alas no, after restoring the partition back to by NVidia 1700 state, now grub spits the dummy. Oh well, I need the practise in install Linux again. So as soon as I get a running system again, I'll test envy.

Computers 7 Humans 2 .....

---

### Post by tempo500 on 2008-04-25
hi, after having serious shipping problems, cancelling the quadro 3700, i found out that my power supply was the eval one. so sorry,(happy me) i dont have to play with a brand new card. phil

---

