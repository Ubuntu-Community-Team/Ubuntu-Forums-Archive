---
title: "Why are devices detected even when disabled in BIOS"
date: 2010-12-05
forum: Multimedia Software
---

### Post by XEtedBear on 2010-12-05
I am having problems understanding how sound capable devices are being used on my Ubuntu10.10 64 bit system. I have an ASUS A8V motherboard with on-board multimedia functions provided through the VIA V8237 chip. BIOS gives me the option to disable this functionality and I have set BIOS this way. I want to use an  M-Audio 24/96 card for all sound processing.

However, in applications like Audacity the VIA chip functions are all available and can be set as recording and playback devices. The same is true in ALSA.

Why does 'linux' (I have no idea which part of the OS) ignore the BIOS settings?

Furthermore alsamixer always selects the 'default' devices. Where and how are these set?

<System><Preferences><Sound> hardware tab list 2 'Internal Audio' devices but no M-Audio device. What are these devices? Only 1 of them appears to create any output with the 'Test Speakers' tab. This confuses me completely because the speakers are connected only to the M-Audio card. 

None of the profiles for 'Settings for the selected device' match the capabilities of the M-Audio card (1 set of stereo inputs and 1 set of stereo outputs). So where are these profiles coming from? Which do I select for the M-Audio card?

What do the Input and Output tabs in <System><Preferences><Sound> mean? Are these different to the hardware tab? The 'Output' tab lists2 devices for sound output:  'Internal Audio Analog Stereo, Stereo' twice. What devices are these ?

If the 'system' actually knows what these devices are, by device name, why aren't these names shown in this applet?

---

### Post by lidex on 2010-12-05
Confusing, yes. Let's take a look at some system info. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Also provide these outputs please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by XEtedBear on 2010-12-05
> **lidex said:**
> Confusing, yes. Let's take a look at some system info. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Also provide these outputs please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

THanks for this clear instruction; here are the results:

Alsa script output link:  
[http://www.alsa-project.org/db/?f=e1b9e1f7ca41e51ccb178c725b5afc9c42a1919b](http://www.alsa-project.org/db/?f=e1b9e1f7ca41e51ccb178c725b5afc9c42a1919b)

dmidecode BIOS output:
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 0229    
	Release Date: 05/29/2007
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
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
		AGP is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported

This result surprises me: BOOT from CD is definitely not supported on this motherboard - because my CDROM is a SATA drive. There is a technical support answer on the ASUSTek knowledge base confirming that this motherboard cannot be booted from a SATA CDROM.

Next, Serial and Parallel adapter functions are disabled in BIOS - I have no use for them.


Handle 0x0036, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		en|US|iso8859-1
		de|DE|iso8859-1
		fr|FR|iso8859-1
	Currently Installed Language: en|US|iso8859-1

dmidecode baseboard output:
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer Inc.
	Product Name: A8V
	Version: Rev 1.xx
	Serial Number: MB-1234567890

Handle 0x0034, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description:   To Be Filled By O.E.M.

This really confuses me: when I look at the setting in BIOS for AC'97 it clearly says 'Disabled'.

---

### Post by lidex on 2010-12-05
That bios might need an update.
You can blacklist the via module and it won't load at bootup, in effect disabling that audio device.

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
At the bottom add this:
```
snd_via82xx
```
Save & close.
Reboot and run:
```
aplay -l
```

---

### Post by gordintoronto on 2010-12-05
> **XEtedBear said:**
> This result surprises me: BOOT from CD is definitely not supported on this motherboard - because my CDROM is a SATA drive.


However, you could install an IDE CD-ROM and boot from it.

---

### Post by XEtedBear on 2010-12-06
> **gordintoronto said:**
> However, you could install an IDE CD-ROM and boot from it.

True, indeed that is what I originally did until I walked past the PC one day not realising that the Rise of the Machines is happening right here in my study: the system quite deliberately opened the CD drawer just at that time, planning to trip me up and ensure that I lost an eye on the sharp-edged corner of the table. Huh - 'they' under-estimated me; I survived but the player didn't. The only available replacement at the time was SATA. 
I thought this was a good idea anyway because I previously only had 2 less-than-optimal solutions: place my Linux drive as slave on the primary IDE or have the IDE CD-ROM as slave to that drive on the secondary IDE. It was only later I discovered the design flaw in the A8V.


However, none of this affects the sound device questions that I have.

---

### Post by XEtedBear on 2010-12-06
> **lidex said:**
> That bios might need an update.


Actually I think the motherboard needs an update, with update_type=replace. 0229 is the last BIOS level available for the A8V.


Thanks for the advice on black-listing modules. I hope this is reversible.....

---

