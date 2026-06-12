---
title: "AverTV card, how to get analog tv working?"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by Schendje on 2008-03-11
So I've been working for Ubuntu for about a week now, it's really great. Most things went really smooth but now I'm running into an annoying problem.

I have an AverMedia AverTV Hybrid+FM PCI card in my computer to watch and record a little bit of TV with. However, I can't seem to get it working.

I've found tons of things about this DVB-t thing, which is digital television, right? However, I'm trying to watch simple analog TV with the card. I've also plugged in my old Nintendo 64 (through the RCA input, the red/white/yellow cables) and TVtime displays that just fine.

I have tried installing the original Windows program and drivers through Wine, which didn't work (not that I expected it to, but I figured I could try). I also have Kaffeine, MPlayer, VLC, XawTV and Xine Movie Player, but none of them can help me with analog tv. I tried MythTV just now, but I'm having all kinds of trouble with it.

So, how do you view analog TV on Ubuntu?

Any help at all would be nice! Am I doing something wrong, did I misunderstand anything, or am I just plain out of luck? Thanks in advance.  :)

---

### Post by xc3RnbFO8P on 2008-03-11
Is this how you installed it:

>  sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
> 
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

> cd v4l-dvb

> make all

> sudo make install

I use Tvtime to view analog.

---

### Post by Schendje on 2008-03-11
Thanks, I did what you said but none of the programs is showing anything yet... Not even TVtime. I hooked up my N64 again and now it's not even showing that.

Last time I got anything was when Kaffeine finally recognized the card and started the DVB function. I scanned for channels and everything, but it said there weren't any. :???:

---

### Post by xc3RnbFO8P on 2008-03-11
What is your card:

> AverMedia Cardbus Hybrid TV FM E506R 
AVerMedia AverTV Hybrid FM PCI A16D 
AVerMedia AverTV Hybrid FM PCI A16AR

---

### Post by Schendje on 2008-03-11
I believe it's the A16AR version. It's definitely not the first one. The only reason why I think it's not the A16D is because of pictures... It doesn't specify anywhere on the box or in the manual.

---

### Post by xc3RnbFO8P on 2008-03-11
Check if you can see it here:

[http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#AVerMedia]("http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#AVerMedia")

---

### Post by Schendje on 2008-03-11
Yeah, I checked that page before. It says "Yes" under "Supports".

Also, I'm quite sure it's the A16AR, because of the "Philips SAA7135HL (A/V decoder)" on that page. I ran some sort of command yesterday to test what card I had, and that popped up.

//Edit: oh wait, the A16D also has that. Never mind. :P

//Edit 2: [this page]("http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_Hybrid%2BFM_PCI") says:

> If you have an A16AR then "sudo lspci -vv" should reveal:

02:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
Subsystem: Avermedia Technologies Inc Unknown device 2c00
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 32
Interrupt: pin A routed to IRQ 20
Region 0: Memory at fddff000 (32-bit, non-prefetchable) [size=2K]
Capabilities: [40] Power Management version 2
Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-


When I run that command it says exactly that.

//Another edit: *sigh*

> Note: these two examples are less then ideal:
we need output from lspci that shows the card being properly detected ... what is currently shown is what would be output by the command when the card is NOT automagically recognized!

This isn't getting anywhere. :(

---

### Post by xc3RnbFO8P on 2008-03-11
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/848681.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/848681.html)

 > Hi Doc, I'm new to Whirlpool and have just sent you a whim ...as I said Avermedia A828 linux driver 0.07(0.04 also I think) will do the trick on Ubuntu....

Yep, it does wonderfully, i'm so happy. I thought I would detail the procedure here (i'm a newbie so if any of this is really obvious then feel free to ignore it, or wrong please correct me).

I followed a source that specifically details how to install the AVermedia AVerTV Hybrid+FM Volar (A828) which works for A301. (With some assistance from google.

Source Info:
[www.avermedia.com/cgi-bi...DIA-Linux-A828-0](www.avermedia.com/cgi-bi...DIA-Linux-A828-0). <-- for the older version but it still works ok
[www.avermedia.com/EN/def...&CATNO1=D2&CNT=1](www.avermedia.com/EN/def...&CATNO1=D2&CNT=1) <-- download driver 0.07

When trying this driver you must have:
1) Source code for the kernel installed
2) The ¨build¨ option for the kernel installed.
3) A symbollic link for the source
Feel free to try the install first it will soon tell you if it can´t proceed.

First perform the following:
download the driver ([www.avermedia.com/EN/def...&CATNO1=D2&CNT=1](www.avermedia.com/EN/def...&CATNO1=D2&CNT=1))
uname -r (note the name)
sudo apt-get install build-essential
sudo apt-get install kernel-source-2.6 (if not 2.6 substitute the correct file, alternative method for the source here: [www.ubuntu-unleashed.com...r-thinkpads.html](www.ubuntu-unleashed.com...r-thinkpads.html))

Now installing the kernel source does not install the symbollic link required for the installation of the AVermedia driver 0.07.

So verify that the source code has been installed to /usr/src and is uncompressed (If not use tar -xf linux-source-2.6.22.tar.bz2).

Then
ln -s /usr/src/linux-source-2.6.22 /lib/modules/`uname -r`/source (creates the symbollic link from the source code.)

Then
unzip AVERMEDIA-Linux-A828-0.04-beta.sh.* zip
sudo ./sh AVERMEDIA-Linux-A828-0.04-beta.sh

If you still want to be sure if the driver is loaded, do the following
at the command line:

lsmod | grep a828

Now for some reason, this module does not seem to load on boot, so I have to insert if prior to use using:
modprobe a828

Also, double check any closed source drivers install (ie. Nvidia) as mine did not work properly after this and had to be re-installed.

Good luck, to all I hope this helps
DrE

Edit: none standard characters, hmm how did they get there ?

---

### Post by Schendje on 2008-03-12
> **Ringi said:**
> [http://forums.whirlpool.net.au/forum-replies-archive.cfm/848681.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/848681.html)

Thanks again for the info Ringi. :)

I ran into this page before and I tried it but I got stuck. I tried it again now and after a lot of trouble the A828 driver seems to be installed. When I type:

```
lsmod | grep a828
```

I get:

```
a828                  586032  0 
dvb_core               80668  1 a828
videodev               34432  2 a828,saa7134
usbcore               138632  7 a828,snd_usb_audio,snd_usb_lib,uhci_hcd,ehci_hcd,ohci_hcd

```

However... I still doesn't seem to do anything. None of the programs shows something. :(

---

### Post by Schendje on 2008-03-13
Does anyone else have an idea?

I guess I'll just sell the card or something, too bad it doesn't work. :(

Thanks to Ringi for all the effort though! :)

---

### Post by ralph1e on 2008-03-29
Hi.
I use openSUSE as my main OS but I found this thread via Google and I wanted to share with you with my knowledge about this topic. Latest possible to download drivers are 0.07beta now but there is internal version of these drivers called 0.15beta. I have got them from official AverMedia support and thanks to them I can watch analog TV now on openSUSE 10.3. Here is changelog ```
0. Table of Contents

	1. Scope
		1.1 Supported distributions
	2. Requirement
	3. Feedback & Support
	4. Change Log
	

1. Scope

This document provides guidelines on using AVerTV USB Hybrid+FM driver
installer. The main purpose of the installer is to help user install
driver for the running kernel. If you reboot to another kernel or upgrade
your kernel, the installer should be executed again to install
driver for the new kernel.

The following products are supported by the installer:

	1. AVerTV Hybrid+FM Volar (A828)


1.1 Supported Distributions

This version of driver installer supports kernel 2.6.17~2.6.23.
Most distributions with these kernel versions are supported.
If you kernel falls outside this range, the installer will still
try to install the most suitable version.

The following distributions, with their stock kernel, are officially 
tested and supported:

		1. Open SuSE Linux 10.3
		2. Mandriva Linux 2008
		3. Fedora Core Release 6
		4. Fedora Core Release 7
		5. Ubuntu 7.10
		6. OpenSuSE 10.3


2. Requirement

If you customize your own kernel, make sure to enable support for DVB, Video
For Linux, and USB in the kernel configuration. General users can safely skip
this section.


3. Feedback & Support

Suggestions and bug reports are very welcome. If you have any question
not answered by this document or have any suggestions regarding our product
or driver, please contact AVerMedia support desk at the following website:

http://www.avermedia.com/cgi-bin/support_faq_form-new.asp

It would help if you can provide /tmp/A828-install.log, which is generated by
the installer. It contains muched detail information regarding your system and
how installer operates. 	


4. Change Log

0.14-beta => 0.15-beta
	1. Fix installer bug which causes compatibility issue on some kernels.
	2. Show kernel messages after ALSA audio is successfully initialized.

0.13-beta => 0.14-beta
	1. Support ALSA audio
	2. Fix FM lock bug
	3. Fix driver remove bug

0.12-beta => 0.13-beta
	1. Fix change channel bug
	2. Fix video streaming bug
	3. Fix some memory leaks
	4. Improved driver stability 
	
0.11-beta => 0.12-beta
	1. Add documentation on how to use included tools.

0.10-beta => 0.11-beta
	1. Fix some installer bug on tool installation.

0.09-beta => 0.10-beta
	1. More user-friendly driver installer
	2. More stable video streaming

0.08-beta => 0.09-beta
	1. Improved compatibility with tvtime

0.07-beta => 0.08-beta
	1. Fix the bug in VIDIOC_ENUMSTD ioctl
	2. Test analog TV using mplayer in Kernel 2.6.22

0.06-beta => 0.07-beta
	1. Support Kernel 2.6.21

0.05-beta => 0.06-beta
	1. Support VIDIOC_ENUMSTD

0.04-beta => 0.05-beta
	1. Support new Distributions
	2. Support x64 architecture
	3. New kernel version compatible
	4. Unsupport pre-build distribution's native kernel

0.03-beta => 0.04-beta
	1. Added support Fedora Core 6
	2. Automatically detect system (distribution) and improve system
	   compatibilities during installation		   
	3. Improve compatibility to tvtime player
``` 
(yes, they mentioned "Open SuSE Linux 10.3" and "OpenSuSE 10.3" as supported systems, probably by mistake)

I can upload these drivers for 32 and/or 64bit systems or you could just ask official AverMedia support for them. Just wanted to point out that AverMedia is quite friendly to Linux users and they are still working on these drivers (they will release them "when ready", that's why you won't get these drivers from official site now).

Ah, and last thing about sound. I had to install "A828-Tools" (included with driver), compile them (using "make" as says "readme") and run (as root, you will probably use sudo for that) "audio" file. Now I can run my favourite TvTime application and watch analog TV with sound.

I don't know how to make remote controller working so if you know something about it I would be more than happy to hear it :)

Hope this help you a bit. Have fun!

EDIT: Uploaded 32bit and 64 bit drivers.

[color=blue]PS. Official AVerMedia site has now newer drivers available for download than 0.15beta so I encourage you to download those drivers from now on. Here is a direct link to site with drivers : [http://www.avermedia.com/AVerTV/Product/ProductDetail.aspx?Id=31&tab=APDriver](http://www.avermedia.com/AVerTV/Product/ProductDetail.aspx?Id=31&tab=APDriver)[/color]

---

