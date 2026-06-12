---
title: "No sound at all: Sound Card cs-4236"
date: 2009-02-23
forum: Multimedia Software
---

### Post by vajinder dutt on 2009-02-23
Hi, I'm Vajinder Dutt
I have recently installed ubuntu intrepid ibex. Everything is going well except sound. My sound card is crystal semiconductor, cs4236. I hear drum sound only at logon screen. Volume Control present with red mark when clicked shows " The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured".

#aplay -l output 
aplay: device_list:215: no soundcards found...

#lspci output 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0f.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:0f.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
00:10.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

lspnp -v output
01:01.00 CSC0000 Crystal PnP audio system CODEC
    state = active
	dma 1
	dma 3
	irq 5
	io 0x534-0x537
	io 0x388-0x38b
	io 0x220-0x22f

01:01.01 CSC0001 Crystal PnP audio system joystick
    state = disabled

01:01.02 CSC0010 Crystal PnP audio system control registers
    state = active
	io 0x120-0x127

01:01.03 CSC0003 Crystal PnP audio system MPU-401 compatible
    state = active
	io 0x330-0x331

when i go to System/Preference/sound, I found no device listed in device box. and all options are set to autodetect.

I'm really very frustrated. Please write me the solution
Thanking you

---

### Post by Sera88 on 2009-04-18
Sorry I don't have the solution for this but I'll tell my problems with this sound chip. I have an IBM Thinkpad 600 running at 233MHz with 130MB of RAM and the CS-4237B chip. My OS is Ubuntu 8.04 with kernel 2.6.24-16-generic i586.

My problem is that the "registers" entry is disabled so I don't know what my *cport* variable is when setting up the cs-4236 module:

[i]00:06 CSC0010 Crystal PnP audio system control registers
state = disabled[/i]

I've tried to enable it with the command **sudo setpnp 06 on**, but the program just informs me that

*lspnp: /proc/bus/pnp not available*

I try to create the directory with **sudo mkdir /proc/bus/pnp** but it says the folder can't be created because "the file or folder doesn't exist". The /proc/bus directory is there though. Weird.
I don't think I have any more options to go with. I have a folder **pnp** under **/sys/bus** so **setpnp** should look it from there.

EDIT: I got sound working now. I set the boot options (edited */boot/grub/menu.lst*) to **acpi=off apm=on and pnpbios=on**, then **sudo update-grub**, then **sudo modprobe snd_cs4236 port=0x530 cport=0x538 isapnp=0 dma1=1 dma2=0 irq=5** and **sudo modprobe snd_pcm_oss**. The command doesn't load all the way because it gets jammed but I just closed xterm.

Then, I did **asoundconf set-default-card CS4237B**, and then **aplay -l** which confirmed that the sound card is in use. It worked but it requires some work, as you can see.

---

### Post by b@sh_n3rd on 2009-05-11
Hi, even I have the CS4236B sound card and I found the easiest and fastest fix. It applies to other soundcards too, Just replace the CS4236 driver with whatever driver your card uses :D. Check it here, [http://ubuntuforums.org/showthread.php?t=1140821](http://ubuntuforums.org/showthread.php?t=1140821). 3rd Post.

---

