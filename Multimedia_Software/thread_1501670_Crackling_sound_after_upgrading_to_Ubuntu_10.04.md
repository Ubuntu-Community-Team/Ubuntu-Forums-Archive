---
title: "Crackling sound after upgrading to Ubuntu 10.04"
date: 2010-06-04
forum: Multimedia Software
---

### Post by guyjohnston on 2010-06-04
Hi, I recently upgraded to Ubuntu 10.04 from 9.10 and there's now a strange high-pitched crackling distortion sound whenever I play any kind of sound with any program, which seems to stop and start at random. My sound card is an SiS SI7012, and the sound was working perfectly before I upgraded.

I'm not sure whether this is a problem with Pulseaudio or ALSA or what. I tried removing all of the Pulseaudio packages, but that didn't help, and I also tried doing 'remove completely' on all of the Pulseaudio and ALSA packages and then reinstalling, but that didn't work either.

Does anyone have any idea what might be causing this? Thanks.

---

### Post by amitchell on 2010-06-07
I have an almost identical problem. I wouldn’t describe it as high pitched but more like a static interference. My gut reaction is this is a driver problem; from the sound preferences window and hardware tab I can see the card is SB Live! EMU10K1X.  Any suggestion would be greatly appreciated. 


I know there are better ways to identify the hardware if you provide instruction I will reply with more detailed information.

---

### Post by lidex on 2010-06-07
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
head -1 /proc/asound/card0/codec97#0/ac97#0-0 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by oyvinst on 2010-06-08
I have bad audio crackling problems in Ubuntu 10.04 that are triggered by Radeon KMS. Do you have an ATI video card ? And if so, does booting kernel with option "radeon.modeset=0" resolve the audio crackling issues ?

---

### Post by guyjohnston on 2010-06-08
> **amitchell said:**
> I have an almost identical problem. I wouldn’t describe it as high pitched but more like a static interference. My gut reaction is this is a driver problem; from the sound preferences window and hardware tab I can see the card is SB Live! EMU10K1X.  Any suggestion would be greatly appreciated. 


I know there are better ways to identify the hardware if you provide instruction I will reply with more detailed information.
Yeah it sounds similar to static interference for me too. I also think it's a driver problem. I found out the  driver used for my sound card is the snd_intel8x0 module, and I've seen in the forums that quite a few people seem to have the same or similar problems with that driver since upgrading to Ubuntu 10.04. I haven't found a way to fix the problem though.

---

### Post by guyjohnston on 2010-06-08
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
head -1 /proc/asound/card0/codec97#0/ac97#0-0 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

This is the output of uname -a:
```
Linux glaptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
```

aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

cat /proc/asound/version:
```
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).
```

head -n 1 /proc/asound/card*/codec#*:
```
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
```

head -1 /proc/asound/card0/codec97#0/ac97#0-0:
```
0-0/0: Analog Devices AD1981B
```

My computer is a Dell Inspiron 1000 laptop.

---

### Post by guyjohnston on 2010-06-08
> **oyvinst said:**
> I have bad audio crackling problems in Ubuntu 10.04 that are triggered by Radeon KMS. Do you have an ATI video card ? And if so, does booting kernel with option "radeon.modeset=0" resolve the audio crackling issues ?

My graphics card is made by SiS, so I don't think that's the cause of the problem for me.

---

### Post by smusevic on 2010-08-31
Somehow similar problem here. The computer in question is at my work, so have no idea what's the hardware, no model indicated on the case. To be exact: the music does play BUT there is absolutely no low frequencies, the highs are severely amplified, causing a very high frequency distortion, sounding somehow like a crackling sound.

uname -a
```

Linux sash-desktop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

```

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

cat /proc/asound/version
```

Advanced Linux Sound Architecture Driver Version 1.0.21.

```
head -n 1 /proc/asound/card*/codec#* 
```

Codec: Realtek ALC883

```

head -1 /proc/asound/card0/codec97#0/ac97#0-0
```

head: cannot open `/proc/asound/card0/codec97#0/ac97#0-0' for 
reading: No such file or directory

```


Thanks in advance!
Sas

---

### Post by lidex on 2010-08-31
> **smusevic said:**
> Somehow similar problem here. The computer in question is at my work, so have no idea what's the hardware, no model indicated on the case. To be exact: the music does play BUT there is absolutely no low frequencies, the highs are severely amplified, causing a very high frequency distortion, sounding somehow like a crackling sound.

uname -a
```

Linux sash-desktop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

```

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

cat /proc/asound/version
```

Advanced Linux Sound Architecture Driver Version 1.0.21.

```
head -n 1 /proc/asound/card*/codec#* 
```

Codec: Realtek ALC883

```

Thanks in advance!
Sas

Could you provide this info as well:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

Reference this page:
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html#issues](http://www.sabi.co.uk/Notes/linuxSoundALSA.html#issues)

---

### Post by smusevic on 2010-09-02
Hello lidex, thanks for interest in the problem.

First of all, a little update on the problem. The crackling sound and absence of low frequencies only appears to happen via Flash Plugin in Chrome. In all other cases, the sound is NOT CRACKLING, but low frequencies are still missing. High frequencies appear to be boosted, however it is hard to say it's not just an absence of low frequencies that does the impression. I've listened to same mp3 file on VLC on the computer in question AND on my MacBook, the difference is vast. 

Here are the outputs:

sudo dmidecode -t bios
```

# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Award Software International, Inc.
	Version: APD F2
	Release Date: 10/19/2006
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
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

Handle 0x001A, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		n|US|iso8859-1
		n|US|iso8859-1
		r|CA|iso8859-1
	Currently Installed Language: n|US|iso8859-1

```

sudo dmidecode -t baseboard
```

# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: 965GM-S2
	Version:  
	Serial Number:  

```

Comment on the last output: nothing appears after "Serial Number:". Just in case you think I forget to paste it.

Thank you again!

Sas

---

### Post by smusevic on 2010-09-02
btw: a very similar thing can happen if a stereo signal is mixed down to mono (eg: reverse left signal and mix it with right - that would cancel out most of lower frequencies)

---

### Post by lidex on 2010-09-02
How do you feel about a bios update?

---

### Post by smusevic on 2010-09-04
> **lidex said:**
> How do you feel about a bios update?
I feel good about bios update :)

However, a friend suggested it might be some faulty wiring inside the box, so I'll check that first (I'm off work next week, so I'll open the computer on 13.Sept).
However, doing a bios update seems a good thing regardless of my problems, right? I mean, are things generally better after bios update or it doesn't really matter in most cases?

Thanks a million,
  Sas

---

### Post by smusevic on 2010-09-13
> **lidex said:**
> How do you feel about a bios update?

OK, I'm ready to try the BIOS update. Is something like [this]("http://www.hardwaresecrets.com/article/33") you had in mind?

Thanks,
 Sas

---

### Post by lidex on 2010-09-14
Yeah, kinda. You'll need to  get to the website of your PC/MOBO manufacturer and get the correct version.

---

### Post by smusevic on 2010-09-14
> **lidex said:**
> Yeah, kinda. You'll need to  get to the website of your PC/MOBO manufacturer and get the correct version.

Right. The following occured:
#sudo dmidecode
```

...
Base Board Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: 965GM-S2
	Version:  
	Serial Number:
...

```
Googled and came up with the following site: [965GM-S2 BIOS]("http://www.gigabyte.com/products/product-page.aspx?pid=2617#bios")
Created FreeDOS bootable disk, booted from it and attempted to update BIOS with executable provided by mentioned site, cryptic error, not worth mentioning.
Could not use the Q-FLASH utility to update BIOS, cause it only reads BIOS images from floppy disks (!!!!). In fact the only problem was the whole research facility (my workplace) couldn't come up with a single floppy disk. 

needless to say, I'm open to suggestions!

Thanks,
  Sas

---

### Post by Linuxforall on 2010-09-14
> **smusevic said:**
> Right. The following occured:
#sudo dmidecode
```

...
Base Board Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: 965GM-S2
	Version:  
	Serial Number:
...

```
Googled and came up with the following site: [965GM-S2 BIOS]("http://www.gigabyte.com/products/product-page.aspx?pid=2617#bios")
Created FreeDOS bootable disk, booted from it and attempted to update BIOS with executable provided by mentioned site, cryptic error, not worth mentioning.
Could not use the Q-FLASH utility to update BIOS, cause it only reads BIOS images from floppy disks (!!!!). In fact the only problem was the whole research facility (my workplace) couldn't come up with a single floppy disk. 

needless to say, I'm open to suggestions!

Thanks,
  Sas

Use ISOBURNER to create a bootable CD disk, get boot file from bootdisk.com Add the bios file and flash file via ISOBURNER and flash your BIOS.

---

### Post by McBert on 2011-03-20
Hi,

i had a similar problem on a MacBook Pro 1.1 after upgrading to Ubuntu 10.04. The left speaker sometimes crackles while playing any sound. I fixed this problem by disabling IEC958 audio interface:

   amixer sset 'IEC958' mute
   amixer sset 'IEC958 Default PCM' mute

Hope this helps you and other.

---

