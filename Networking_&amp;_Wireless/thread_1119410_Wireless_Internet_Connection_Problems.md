---
title: "Wireless Internet Connection Problems"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by hatecrewdeathroll on 2009-04-07
I'm new to Ubuntu. I dual boot Vista and now Ubuntu. While my wireless internet connection works fine with Vista, I can't seem to get it to work with Ubuntu. The help section says to go to system>admin>network, but i don't have this button. Any ideas?

---

### Post by RedSingularity on 2009-04-07
Type in terminal "lspci" and post the output.

---

### Post by hatecrewdeathroll on 2009-04-07
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by RedSingularity on 2009-04-08
Type BCM into the synaptic package manager.  There are drivers in there you can try.  If they dont work remove them.

Its the b43-fwcutter

---

### Post by hatecrewdeathroll on 2009-04-08
i searched BCM and all i got was "libklibc"

---

### Post by superprash2003 on 2009-04-08
try this [http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html)

---

### Post by hatecrewdeathroll on 2009-04-08
didn't recognize my STA driver, only something from my graphics card

---

### Post by RedSingularity on 2009-04-08
Download NdisWrapper located [HERE](http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=voxel&filename=ndiswrapper-1.54.tar.gz&a=66127087).  Put it on your desktop and i will tell you how to install it.

---

### Post by hatecrewdeathroll on 2009-04-08
ok it's on my desktop

---

### Post by RedSingularity on 2009-04-08
Ok good, did you extract it to the desktop or is it still in the .tar file?

---

### Post by RedSingularity on 2009-04-08
Oh and also download the GUI tool for ndiswrapper located [HERE]("http://dlz.download.chip.eu/exec/r2r.pl?m=dlz;u=http%3A%2F%2Fdl05.chip.eu%2Fdownload%2F0c17b25db92275fe165b51062de925eb%2F49dd257a%2F157167%2Fndiswrapper-utils-1.5-ndisgtk_i386.zip;ct=1;thc=1;b=157167;c=3593663;tit=Beitrag+157167+EN;url=http%3A%2F%2Fdownload.chip.eu%2Fen%2Fdownload_getfile_en_3593679.html;sep=%7C;tid=50;tp=9;tc=005010;tn=Linux;tpn=download+eu;content_type=egc;cs=1")

There is no need to extract anything from here because it is a .deb file and it will install itself.

---

### Post by hatecrewdeathroll on 2009-04-08
i haven't extracted it yet, as i don't know where i would extract it to

---

### Post by hatecrewdeathroll on 2009-04-08
i think that last link is broken

---

### Post by RedSingularity on 2009-04-08
Ok then extract it to your desktop.

---

### Post by hatecrewdeathroll on 2009-04-08
done.

btw thanks for being so patient with me

---

### Post by RedSingularity on 2009-04-08
No problem buddy, i just hope we can fix this.  

Ok now go to the terminal and enter the following commands......

cd ~/Desktop/ndiswrapper-1.54------PRESS ENTER

make---------PRESS ENTER

sudo make install---------PRESS ENTER

---

### Post by RedSingularity on 2009-04-08
Then download [THIS]("http://mirrors.kernel.org/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.4-1_i386.deb")

You can install this easily by just clicking it.

---

### Post by hatecrewdeathroll on 2009-04-08
ok i dl'd the .deb file but on the

cd ~/Desktop/ndiswrapper-1.54  it says there is no such file or directory

---

### Post by RedSingularity on 2009-04-08
Oh are you connected via an ethernet cable now?

---

### Post by hatecrewdeathroll on 2009-04-08
no i have wireless and am using vista

---

### Post by RedSingularity on 2009-04-08
Install [THIS.](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb)

and [THIS](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.52-1ubuntu1_all.deb)

---

### Post by hatecrewdeathroll on 2009-04-08
Aight' I have those dl'd

---

### Post by RedSingularity on 2009-04-08
Ok try installing them.  Some will complain that dependencies are not met but if that happens just skip to the next one.  Soon all will be installed.  You should have 3 .deb's correct??

---

### Post by hatecrewdeathroll on 2009-04-08
yes i have 3 .deb files and an extracted folder entitled ndiswrapper-1.54

how do i install them?

---

### Post by RedSingularity on 2009-04-08
Forget the extracted folder.  We will use the .deb files.  Just click them to install.  And like i said, if they give you dependency errors just try the next one and eventually you will have all 3 installed.

---

### Post by hatecrewdeathroll on 2009-04-08
Windows doesn't know how to open .deb files

---

### Post by RedSingularity on 2009-04-08
Ohhhhh no move them and open them on your linux machine....lol.

---

### Post by hatecrewdeathroll on 2009-04-08
lol lemme try that *hits restart button yet again*

---

### Post by hatecrewdeathroll on 2009-04-08
Alright all 3 are installed

---

### Post by RedSingularity on 2009-04-08
Great, now in a terminal type "sudo ndisgtk" without the quotes.  Should bring up a user interface.

---

### Post by hatecrewdeathroll on 2009-04-08
A menu pops up that says add/remove drivers and configure network. i have no installed windows drivers it says

---

### Post by RedSingularity on 2009-04-08
Perfect thats what we want.  Now can you locate the drivers for your wireless card?  If you have a CD for your card then you can just insert that.

Your looking for  Broadcom Corporation BCM4328

---

### Post by hatecrewdeathroll on 2009-04-08
lemme see if they're available online somewhere

---

### Post by hatecrewdeathroll on 2009-04-08
it's gonna take like 10 min to dl this driver

---

### Post by RedSingularity on 2009-04-08
Looks like you can get it [HERE]("ftp://ftp.dell.com/network/R151517.EXE")

EDIT:  Oh you found one??

---

### Post by hatecrewdeathroll on 2009-04-08
The one im downloading is R151519 the link you had was R151517 im not really sure what the difference is

---

### Post by RedSingularity on 2009-04-08
Ah we can try both then.

---

### Post by hatecrewdeathroll on 2009-04-08
alright finished downloading one of them, lemme do the other one and find some caffeine

---

### Post by hatecrewdeathroll on 2009-04-08
it says the driver is invalid >.<

---

### Post by RedSingularity on 2009-04-08
Is that all it says?

---

### Post by hatecrewdeathroll on 2009-04-08
yea

---

### Post by RedSingularity on 2009-04-08
Ok did you check in System>Administration>Hardware Drivers?  If you did and there is nothing there that has to do with your Wireless card i have one more item you can download.

---

### Post by RedSingularity on 2009-04-09
[THIS](http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-4ubuntu1_i386.deb) many help you out.  Install it and then restart your system.  If you still dont have internet working then go back to the Hardware Drivers and look in there again.

---

### Post by hatecrewdeathroll on 2009-04-09
the only driver there is "wl"

---

### Post by RedSingularity on 2009-04-09
Try the file i have up above.  That has firmware in it that is essential to the working of your driver.  If that doesnt work you can submit a bug report.  A professional gets back to you in 24 hours giving you steps to fix it (if possible) and if not they include a fix for it in the next ubuntu/Kernel release.

If you are interested (if all else fails) go [HERE](https://bugs.launchpad.net/bugs/+filebug) for bug reports.

---

### Post by hatecrewdeathroll on 2009-04-09
Thanks again for the help

---

### Post by RedSingularity on 2009-04-09
Happy to help......let me know what happens with that last package.

---

### Post by hatecrewdeathroll on 2009-04-09
failed installation...

---

### Post by RedSingularity on 2009-04-09
It doesnt say why at all?  Such as dependencies.......or something like that?

EDIT:  Are you trying to install the package alone not with Ndiswrapper?  It is a .deb and therefore you only need to click it while in Ubuntu for it to install itself.  Dont try it with ndswrapper....

---

### Post by mundackal on 2009-04-09
hai 
i too have the same problem. since i dont have an internet connection and my wifi isnt working, where can download the packges.i am new to linux, so the packages when i try to install it is asking for internet.so can i download it and install?
is download available here .

thanx

---

### Post by RedSingularity on 2009-04-09
Yeah you can download it.  Look [HERE](http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-4ubuntu1_i386.deb).  Put it on a flash drive or something and install it on your ubuntu computer.  Try it out.

---

### Post by hatecrewdeathroll on 2009-04-09
It said the installation was complete but download failed, service or whatever not known

---

### Post by RedSingularity on 2009-04-09
Oh it need to retrieve files from the internet.  You cant plug in a temporary ethernet cable to get the downloads?

---

