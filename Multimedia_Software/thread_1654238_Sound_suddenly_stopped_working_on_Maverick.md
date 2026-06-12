---
title: "Sound suddenly stopped working on Maverick"
date: 2010-12-28
forum: Multimedia Software
---

### Post by sharat87 on 2010-12-28
I recently installed ubuntu 10.10 (Maverick) on my new laptop. Sound was working just fine until today morning, when all of a sudden no sound would come out of my system. It is not a hardware problem as sound is working fine on windows, so I suspect I must've messed up something myself.

I am a newbie when it comes to multimedia stuff on ubuntu, so, any help is appreciated.

If you need any information, tell me how to gather it (the command I have to run), and I will get it to you.

Thanks.

---

### Post by VonSpyder on 2010-12-28
what kind of sound card do you have?

I actually have had this happen, and as best as I can figure is that it was the result of a corrupted download of maverick. I downloaded another iso of it and did a clean install; it fixed the problem.

---

### Post by sharat87 on 2010-12-29
Thanks for the response VonSpyder. Today morning, as magically as it disappeared, it started to work again. This is beyond me, I did restart a couple of times yesterday and that didn't do anything!

Anyway, I think my lap has an Intel sound card, and I don't think it has to do with a corrupted disk. I suspect it would have been fixed if I had reinstalled with the same disk again :)

---

### Post by lidex on 2010-12-29
Did this occur after a suspend/hibernate? If it happens again try restarting alsa thusly:
```
sudo alsa force-reload
```

---

### Post by sharat87 on 2011-01-02
Thanks for the response lidex. I have the problem again now. I was troubleshooting why my sound recording was not working and discovered a few things. In the Sound Preferences -> Output tab, if I setthe connector to "Analog Output", sound output works just fine with the speakers, but does not work with headphones/earphones. If I set it to "Analog Headphones", sound output works neither with speakers nor with headphones. Strange because I used to use speakers and earphones interchangeably until yesterday. I don't know what to make of it.

Coming to sound input, it works just fine if I use the microphone that comes with my headphones, but not with the built in laptop's microphone. I first thought it was a fault with the laptop's mic, but that mic works fine on windows.

I am ready to provide any information you need. I really need this working as soon as possible. Any help you can do, is greatly appreciated.

**Edit**: I do suspend/hibernate occasionally, but I have restarted 3-4 times today already. But yes, it might have started after a suspend/hibernate. But still, sound works fine with the speakers, not with headphones.

Thank you.

---

### Post by lidex on 2011-01-02
So you need to get headphones working, correct?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by sharat87 on 2011-01-02
Hey lidex, here is the link I got [http://www.alsa-project.org/db/?f=be3c8250562b45cb0dff77413c72256d9cb429e0]("http://www.alsa-project.org/db/?f=be3c8250562b45cb0dff77413c72256d9cb429e0")

---

### Post by lidex on 2011-01-02
This should be working and from what I understand, was working for you until recently. Let's try a different approach. You should reset your pulseaudio configuration. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

*Ignore any not found errors.

---

### Post by sharat87 on 2011-01-02
Yes, it was working for me until very recently. So, I deleted .pulse and .pulse-cookie in my home folder, however there are no ~/.asound* or /etc/asound.conf.

I restarted my system after that, but there is no difference. I still get sound only from my speakers, connect my earphones, and there is no sound at all. (I checked the earphones with my phone, they work just fine).

---

### Post by sharat87 on 2011-01-02
Oh wait. Shutdown. Came to my office. Powered it up again. Boom, sound works in my earphones. This is turning really unreliable.

Do you have any thoughts why or how this might happen?

---

### Post by lidex on 2011-01-03
Magic? Ghosts? ;)
Seriously, I have no idea.
Try playing around with gnome-alsamixer and sound preferences, especially the connector drop down on the output tab.

To see if there are pulse errors do the following in a terminal:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```
Also, can you post these for me please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

An edit to alsa-base.conf may be necessary however I haven't found anything on this codec, so this may or
may not work. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-eq 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by sharat87 on 2011-01-06
Here's what you asked for

```

Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  sharat    F.... pulseaudio
/dev/snd/pcmC0D0p:   sharat    F...m pulseaudio

```

```

# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Dell Inc.
	Version: A06
	Release Date: 09/15/2010
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 4.6

Handle 0x0018, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

```

```

# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: Dell Inc.
	Product Name: 0MGC3T
	Version: A00
	Serial Number: /DQBD7BS/CN7016609GG0A3/
	Asset Tag:  
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Not Specified
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0014, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Disabled
	Description: "Intel GM45 Graphics"

Handle 0x0015, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Disabled
	Description: NETWORK_NAME_STRING

```

I'm being a bit paranoid right now, as it is currently working. I am not even shutting my system down everyday as I used to do. But, I will try doing what you said this weekend :)

---

### Post by Sunships on 2011-01-19
Hello,

Were you ever able to resolve this issue? I'm having a similar problem. My thread is here: [http://ubuntuforums.org/showthread.php?t=1659018](http://ubuntuforums.org/showthread.php?t=1659018)

---

### Post by Sunships on 2011-01-19
(double post deleted)

---

### Post by Sunships on 2011-01-19
Hello,

Were you ever able to resolve this issue? I'm having a similar problem. My thread is here: [http://ubuntuforums.org/showthread.php?t=1659018](http://ubuntuforums.org/showthread.php?t=1659018)

---

### Post by Sunships on 2011-01-19
Hello,

Were you ever able to resolve this issue? I'm having a similar problem. My thread is here: [http://ubuntuforums.org/showthread.php?t=1659018](http://ubuntuforums.org/showthread.php?t=1659018)

---

### Post by buknoii on 2011-06-06
i also experienced this when i hibernated my laptop (hp pavilion dm1) i tried some scripts and rebooted for quite some times..then when I shutdown my laptop.. ALAS! it went back.. i dont know if the scripts work or it just needs a shutdown but right now everything is back to normal.

---

