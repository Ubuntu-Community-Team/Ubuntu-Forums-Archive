---
title: "Newbie trying to enjoy Ubuntu"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by Mahngiel on 2009-11-06
So, I'm tired of (insert other painful OS of your choosing) and wanted something fresh.  I found Ubuntu, and am trying to enjoy it.  Installation went great, UNTIL I realized I had no wireless.  It won't recognize I have a wireless card. I have spent hours pouring through this forum and trying to find something that would work.  But I'm tired of failing and restarting to bring windows back up just so i can have the internet and troubleshoot this.  Please help. ):P

Following HOWTO guidelines:

**1)	Machine**
HP Pavillion ZD7000
**2)	Wireless Card info**
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 
[14e4:4320]
**3)	Interface**
wlan0     IEEE 802.11bg  ESSID:""   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=0 dBm    
          Retry  long limit:7   RTS thr: off   Fragment thr: off 
          Power Management: off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
**4)	Modules**
b43                   122136  0  
mac80211              181236  1 b43 
cfg80211               93052  2 b43,mac80211 
led_class               4096  1 b43 
ssb                    35300  1 b43
**5)	Network Scan**
[    8.793020] b43-phy0: Broadcom 4306 WLAN found (core revision 5) 
  *-network:1 
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 3 
       bus info: pci@0000:02:03.0 
       version: 03 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=32 
       resources: irq:21 memory:d2004000-d2005fff 
**6)	Network Configuration**
wlan0     Failed to read scan data : Network is down
**7)	Version info and Architecture**
Ubuntu 9.10 
2.6.31-14-generic i686

---

### Post by t0mppa on 2009-11-06
Ok, so you have the b43 driver installed, have you installed the firmware for it? It doesn't get automatically installed, because it's a proprietary piece of code.

If you have not, BCM4306 revision 3 uses version 4.150.10.5 of the firmware, which you can install by hooking up to Internet through a wired connection and installing the b43-fwcutter package (can use Synaptic or apt-get) and answering yes to the question of whether to fetch and install the firmware.

Or if you cannot establish a wired connection, you can download the files on another computer (the wgets are simple download commands, so just point your browser to said address and save the file), copy them over and install it manually with these [instructions]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new").

If you already have installed the firmware and it's still not working, can you open up a terminal and post the results of **dmesg | grep b43** to see if that gives us any clues as to what's wrong?

---

### Post by Mahngiel on 2009-11-06
i know that i need to learn a lot about this new OS, but it would be easiest to learn while looking at it. that being said:

i used windows to download the b43-fwcutter and the driver i needed; however, i still am not sure what I'm doing.  here's what i'm being told to do, followed by why I'm a newb:

**Step 1**:
Use version 012 of b43-fwcutter. 
Download, extract the b43-fwcutter tarball and build it

```
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2
tar xjf b43-fwcutter-012.tar.bz2
cd b43-fwcutter-012
make
cd ..
```

**Step 2**:
Use version 4.150.10.5 of Broadcom's proprietary driver. 
Download and extract the firmware from this driver tarball:

```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```

If i use the 'wget' command, where do the files go once downloaded? 

If i used windows to download them, how do i get the files there from my thumb drive?

And is all of that above what i'm supposed to use in the command lines?

---

### Post by Tony Ricena on 2009-11-06
The Firmware should be on the Disc.  You honestly don't need a internet connection to get it to work.  Everyone seems to be having this problem.  Will have to make a sticky for all the Broadcom users out there

[I]The Broadcam firmware/driver is on your ubuntu 9.10 cd! I had the same problem with my laptop, but looked on the internet and found the solution. 

Goto your Software sources and check the Installable from cd/dvd, put your CD/DVD in

Goto the Synaptic Package Manager, and search for bcmwl-kernel-source.. check and install.. restart computer and boom it works[/I]

---

### Post by Mahngiel on 2009-11-06
thanks. i'll try this now. hopefully i can report back from Ubuntu, and not windows

---

### Post by Mahngiel on 2009-11-06
weirdness...

i was initially running Ubuntu installed inside of windows, but since i wouldn't have a physical disk (used virtually mounting before) i had to make a disc. 

so i partitioned Ubuntu beside Windows and the first install went bad @ 99%.  So i only booted from the disk as the trial. i was ecstatic when Ubuntu loaded and i seen the proprietary drivers up on top, so i exited and went to re-install.

But anyways, now I cannot get the driver to pop up, and i searched the Synaptic Package Manager, but i don't have "bcmwl-kernel-source" only "bcmwl-modbuilder" or something, but it IS installed.

now what?  thanks to all who can help

went[here]("http://packages.ubuntu.com/karmic/i386/bcmwl-kernel-source/download") and downloaded the bcmmwl-kernel-source. going to try to unpack it. *crosses fingers*

---

### Post by Mahngiel on 2009-11-06
failure. that new pkg is for BCM4311+, i am using 4306

---

### Post by Mahngiel on 2009-11-07
> **t0mppa said:**
> 
If you already have installed the firmware and it's still not working, can you open up a terminal and post the results of **dmesg | grep b43** to see if that gives us any clues as to what's wrong?

[I][    1.849271] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.637279] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   15.960607] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   16.065835] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   16.073782] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   16.073792] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   16.073808] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.[/I]


And i get this: [I]E: b43-fwcutter: subprocess installed post-installation script returned error exit status 1
[/I] trying to install the fwcutter

---

### Post by t0mppa on 2009-11-07
> **Mahngiel said:**
> failure. that new pkg is for BCM4311+, i am using 4306

Yeah, *bcmwl-kernel-source* package installs the Broadcom STA which supports BCM4311, BCM4312, BCM4321 and BCM4322, not the older chips. Thus it is of no use for you.

> **Mahngiel said:**
> i know that i need to learn a lot about this new OS, but it would be easiest to learn while looking at it. that being said:

i used windows to download the b43-fwcutter and the driver i needed; however, i still am not sure what I'm doing.  here's what i'm being told to do, followed by why I'm a newb:

**Step 1**:
Use version 012 of b43-fwcutter. 
Download, extract the b43-fwcutter tarball and build it

```
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2
tar xjf b43-fwcutter-012.tar.bz2
cd b43-fwcutter-012
make
cd ..
```

**Step 2**:
Use version 4.150.10.5 of Broadcom's proprietary driver. 
Download and extract the firmware from this driver tarball:

```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```

If i use the 'wget' command, where do the files go once downloaded? 

If i used windows to download them, how do i get the files there from my thumb drive?

And is all of that above what i'm supposed to use in the command lines?

Wget downloads the file to the directory where you're currently in. If you connect the thumb drive, i.e., plug it in, Ubuntu should recognize and automatically mount it. That means it will be shown as an external drive on the places list on the file browser (Nautilus) and you'll see a shortcut on the desktop for it, which you can double click to open Nautilus in it. Just copy the files either to your home (will be shown as <user_name> in the places list) directory or make a new subdirectory for them, if you want to organize things.

Yes, all those are commands to be run on the terminal. The terminal opens up automatically in your home directory and will have a prompt like: *<user_name>@<computer_name>:<directory_you're_in>$* the ~ sign refers to your home directory, i.e., */home/<user_name>/*. And if you copied the downloaded files to a subdirectory, say b43fw, then you can change the directory with **cd b43fw** (**cd ..** will get you up one level in the hierarchy, i.e., from ~/b43fw to ~) and the prompt should change to **<user_name>@<computer_name>:~/b43fw$**. It's pretty simple and informative once you get used to it.

As for the commands themselves, *tar* is used for manipulating tarballs, which are the common archive files you'll come across on Linux/Unix based systems, kind of like Zip files on Windows. The .bz2 extension means those two are compressed with Bzip2 and thus you need the *j* option for the tar command to uncompress them. The *x* option is for extracting the files from the tar archive and the *f* specifies the file and thus needs to be followed with a space and the file name. You can run **tar --help** or **man tar** to get an explanation of all possible options.

Make is a program that compiles source code to an executable program. Basically it will show a lot of output and the only thing you need to worry about is if it ends in an error. If not, everything compiled cleanly.

Finally, sudo is a way to get super user priviledges for running single commands that require them. In the Linux world, your normal user doesn't have them, so you can never do anything too harmful accidentally and also it's a very good security feature, since even if you happened to get a malicious program on your system and execute it, it can't do anything nasty without the super user rights. Bottom line is: **never** run sudo in front of a command, unless you know what the command does (*man <command>* is a good way to find out).

---

### Post by Mahngiel on 2009-11-07
is this why i cannot access certain directories nor extract something to /lib/firmware?

btw:  i went [here]("http://www.omattos.com/node/6") and found a tar without the hassel of needing fwcutter. so all i need to do is to send it to the /lib/firmware foler... which is how again?

sorry for being so noob, just been at this for about 20 hours now.

---

### Post by t0mppa on 2009-11-07
Yes, you need root (the super user account name on Linux, i.e., same as Administrator on Windows) access to do things like that. It's not built-in into Nautilus, so you're better off using terminal and sudo when you have to modify system files/directories.

EDIT: You can copy the files to the */lib/firmware* with **sudo cp <file_name> /lib/firmware** after extracting them from the tar archive. Note that in terminal pressing tab after typing the first few letters of a file or directory name will auto complete the name, if there are no other options left, so that's a handy way to avoid typos.

---

### Post by Mahngiel on 2009-11-07
hey man, i totally appreciate your help. i'm up and running! woo-frickin-hoo! now i can focus on figuring out what else is going on and have the ability to access the forums while looking at the OS. awesome man, thanks alot.

---

