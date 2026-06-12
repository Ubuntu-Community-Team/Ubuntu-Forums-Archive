---
title: "Alsa drivers..."
date: 2011-06-03
forum: Multimedia Software
---

### Post by Norred on 2011-06-03
I tried to follow the directions in the  Comprehensive Sound Problem Solutions Guide....

It said to post a new thread if it failed... and it did and to post the error... it gave me a log viewer so i am wondering how i can get to that log to show you the log.....

I am trying to get my sound(and microphone) working ...  I have a IP-35 E motherboard which has the Realtek High Definition... 

thanks in advance for help...

using 11.04

---

### Post by lidex on 2011-06-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Norred on 2011-06-03
Actually... I reinstalled ubuntu all together and i got my sound back... but im back to where i was... i tried to install the realtek HD drivers from the realtek site and thats when i lost my sound all together.  I really want my microphone to work correctly ...i tried messing with gnome alsa mixer but nothing works.  I get a little something when i try to speak.. but its like the computer can barely hear me..

im using a headset microphone fyi

---

### Post by lidex on 2011-06-03
See my previous post.

---

### Post by Norred on 2011-06-03
ok.. here it is    

[http://www.alsa-project.org/db/?f=3d84f57dd23631e8e5632a207c112b1ad5908254](http://www.alsa-project.org/db/?f=3d84f57dd23631e8e5632a207c112b1ad5908254)



thanks

---

### Post by lidex on 2011-06-03
You're going to need to supply a model switch but that requires a little more info, specifically:
```
Manufacturer:      System Manufacter
Product Name:      System Product Name
Product Version:   System Version

```

---

### Post by Norred on 2011-06-03
ok,  that would be...

Manufacturer:      Abit
Product Name:      IP35-e
Product Version:   ??

Are you talking about the motherboard?? or the sound driver.. and if so how do i find out??  I know its Realtek High Definition     have it installed on my windows 7 partition...

---

### Post by lidex on 2011-06-04
Try these:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by Norred on 2011-06-04
Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies, LTD
	Version: 6.00 PG
	Release Date: 02/29/2008
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
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
		Targeted content distribution is supported

Handle 0x0013, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		n|US|iso8859-1
		n|US|iso8859-1
		r|CA|iso8859-1
	Currently Installed Language: n|US|iso8859-1


# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: [http://www.abit.com.tw/](http://www.abit.com.tw/)
	Product Name: IP35-E  (Intel P35+ICH9/R)
	Version: 1.0
	Serial Number:

---

### Post by lidex on 2011-06-04
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=6stack-dig" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Norred on 2011-06-04
derron@Destroyer:~$ echo "options snd-hda-intel model=6stack-dig" | sudo tee -a /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=6stack-dig

---

### Post by lidex on 2011-06-04
Make sure to reboot and post an updated alsa-info.

---

### Post by Norred on 2011-06-04
[http://www.alsa-project.org/db/?f=ed1467c369fbaefb8542984bf82c4f5e6d488636](http://www.alsa-project.org/db/?f=ed1467c369fbaefb8542984bf82c4f5e6d488636)


here you go...

---

### Post by Norred on 2011-06-04
and btw.. by looking at others alsa-info..   i noticed that its the name of the computer... i built this computer myself...

---

### Post by lidex on 2011-06-04
OK. Where are we now? Sound works, mic does not?
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

From ubuntu wiki:
> Changing default subdevice configuration

Some sound devices have multiple capture subdevices (eg. hda-intel), 
but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. 
ALSA may not be configured to use your preferred device as subdevice #0 by default.

Open the pulseaudio record meter (pavumeter --record)
Talk into your chosen device while you carry out the process and watch the meter.
Some channels are quite noisy even with no input (especially on integrated chipsets), 
so we are watching for movements that correspond to our voice. 

Use alsamixer -c n (where n is your sound card number, probably 0)
Press F4 to get to the capture console
Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), 
and the volume turned up.
Check the first input source is switched to your chosen plug (Mic, in my case) 
At this point, you should see the record meter bouncing in response to your voice.
I found that I had to repeat this procedure each time I wanted to use the Mic, 
even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized 
until it was repeated. This also works if you use the "Options" tab in the standard mixer app to do the same thing.

---

### Post by Norred on 2011-06-04
ok... that worked!!     thankyou so much....

---

### Post by Norred on 2011-06-04
Actually im listening to myself fine now.. but i hear static in the background.. when i play back...

---

### Post by lidex on 2011-06-04
Make sure to mute unused capture devices.

---

