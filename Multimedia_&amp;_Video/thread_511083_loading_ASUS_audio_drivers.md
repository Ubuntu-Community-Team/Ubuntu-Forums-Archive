---
title: "loading ASUS audio drivers"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by swet on 2007-07-27
Hi

I have run a search for this but found nothing, apologies if I'm going over old ground.

I am new to ubuntu and linux and I've been trying to find details on how to load new device drivers. So far I have found no helpful info. I have an ASUS P5VDC mobo and the onboard sound wont work with ubuntu 7.04. I have an ASUS disc which has a directory named 'linux drivers' but I don't have a clue how to install the files.

Can anybody offer simple instructions for a newby??

Regards

Ed

---

### Post by deadgobby on 2007-07-27
If there is Linux drivers for it, it may have a install or read me file. Or has a file with xxx.rpm . Please take a screen shot  and post it please. 
Gobbby

---

### Post by swet on 2007-07-27
Hi gobby

I unpacked the audio zip file and this is the content....

[ATTACH]39167[/ATTACH]

regards

Ed

---

### Post by deadgobby on 2007-07-27
Open open the INSTALL file and read the text. You all so can try double click on install-sh and it may install it. It is a scrip and I do not know if it is for a debain base linux system. It could be for slax or rpm. It will kill if unknown  system and will not install. I do not see a tar ball, debian, or RPM file. Thus the install read me text first.

Gobby

---

### Post by swet on 2007-07-27
Hi gobby

thanks for the interest. I tried running all the obvious executables when I first loaded the disc but the shell for each disappeared so quickly I didnt see any messages.....bottom line is that nothing happened and hence my post on here....basically I've no Linux experience and don't know how to install generic device drivers or even what they look like. 

to answer your question(sorry to waffle) I looked in all the text files with likely looking names and they all contained update history or scripts, neither of which was very helpful to a greeny like me.

regards

Ed

---

### Post by kostkon on 2007-07-27
First of all, did you try to run the *install-sh* script from a terminal? That way, you will see any messages that maybe the script will print out and you'll not have the problem of the terminal window disappearing.

Furthermore, seeing your screen shot it looks to me that you have the option to compile the driver. Thus, open a terminal and go to the folder where these files are, and do:

```
./configure && make && make install
``` 

These commands will compile the driver (I assume) and will install it. I take no responsibility of what will happen if you do this, and by that I mean that first you have to read the README files to see what these files do and check if you need to actually compile the driver or will be better by using the install script.

I hope someone has already tried this or maybe knows how to solve the sound problem for your mobo. There is a possibility that there is already a driver for your sound chipset inside the kernel and the only thing you have to do is activate it.  Have you searched the [Ubuntu wiki]("http://wiki.ubuntu.com/") about this? It s important to know what sound chipset is used on your mobo.

A quick search from me showed that your mobo uses the VT8251 southbridge so your sound is supposed to work out of the box with the snd-via82xx driver. But this is a speculation from me I don't know if this is for sure.

Could you provide us the output of the *lspci* command here?

---

### Post by swet on 2007-07-27
Hi Kostkon

herewith the output:

ed@ed-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
02:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
ed@ed-desktop:~$ 

I looked in all the ASUS driver directories and it looks like its all C source for compilation, together with makefiles for compiling.

Just to confuse matters, sometimes there is sound but its masked with a 10khz sort of overtone. Other times there is no sound at all.

Ed

---

