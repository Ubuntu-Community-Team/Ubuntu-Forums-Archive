---
title: "Built in Microphone Doesn't Work"
date: 2010-06-10
forum: Multimedia Software
---

### Post by lisar915 on 2010-06-10
Hi everyone,

I'm using a Sony Vaio PCG-K33 laptop with Ubuntu 8.04.  My internal microphone doesn't work, even though it appears to be properly set up.  I looked on some other threads mentioning the Alsa mixer.  When I type in alsamixer into the terminal and get that Alsa screen, my left and right arrows don't work.  Also, I don't see any option of changing from analog to digital.  So if anyone has suggestions, I'm all ears.  

Thanks.
Lisa

---

### Post by lidex on 2010-06-13
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

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

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

---

### Post by owain123 on 2010-06-13
> **lisar915 said:**
> Hi everyone,

I'm using a Sony Vaio PCG-K33 laptop with Ubuntu 8.04.  My internal microphone doesn't work, even though it appears to be properly set up.  I looked on some other threads mentioning the Alsa mixer.  When I type in alsamixer into the terminal and get that Alsa screen, my left and right arrows don't work.  Also, I don't see any option of changing from analog to digital.  So if anyone has suggestions, I'm all ears.  

Thanks.
Lisa

Have you tried going into Sound Preferences --> Input and changing the 'connector' options?

This worked for me. :)

---

### Post by lisar915 on 2010-06-14
@lidex:  I installed the gnome alsamixer.  Then I went to the Pulse Audio input devices tab, where analog microphone/microphone 1 is checked off.  Under the sound preferences box, all the options are checked, which includes mic, mic boost (+20 DB) and mic select.  

@Owain123 I sent into systems, then preferences, then sound, and from there, input.  My default is analog microphone 1.  I tried changing it to analog microphone 2, analog input, analog line in and analog video.  But still, every time I tried and record with the sound recorder, all I get is background static.  

Any other suggestions?  

Thanks.

---

### Post by lidex on 2010-06-15
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by lisar915 on 2010-06-15
@lidex -- here you go:
```

Linux lisa-laptop 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686 GNU/Linux
lisa@lisa-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: A5451 [ALI 5451], device 0: ALI 5451 [ALI 5451]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
lisa@lisa-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                  1.0.20+dfsg-1ubuntu5                                       ALSA driver configuration files
rc  alsa-firmware-loaders                      1.0.15-2ubuntu4                                            ALSA software loaders for specific hardware
ii  alsa-oss                                   1.0.17-1                                                   ALSA wrapper for OSS applications
rc  alsa-source                                1.0.16-0ubuntu4                                            ALSA driver sources
rc  alsa-tools-gui                             1.0.15-2ubuntu4                                            GUI based ALSA utilities for specific hardwa
ii  alsa-utils                                 1.0.20-2ubuntu6                                            ALSA utilities
ii  alsamixergui                               0.9.0rc2-1-9                                               graphical soundcard mixer for ALSA soundcard
rc  alsaplayer-common                          0.99.80~rc4-1                                              PCM player designed for ALSA (common files)
rc  alsaplayer-gtk                             0.99.80~rc4-1                                              PCM player designed for ALSA (GTK version)
ii  bluez-alsa                                 4.51-0ubuntu2                                              Bluetooth audio support
ii  gnome-alsamixer                            0.9.7~cvs.20060916.ds.1-2                                  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                         0.10.25-2ubuntu1.2                                         GStreamer plugin for ALSA
rc  libclalsadrv1                              1.2.2-1ubuntu2                                             ALSA driver C++ access library
ii  libesd-alsa0                               0.2.41-5                                                   Enlightened Sound Daemon (ALSA) - Shared lib
ii  libsdl1.2debian-alsa                       1.2.13-4ubuntu4                                            Simple DirectMedia Layer (with X11 and ALSA 
ii  libsnack2-alsa                             2.2.10-dfsg1-8ubuntu1                                      Sound extension to Tcl/Tk and Python/Tkinter
lisa@lisa-laptop:~$ head -n 1 /proc/asound/card*/codec#*
```

---

### Post by lisar915 on 2010-07-09
Hi again,

I tried adjusting the connector options but still, all I get is static when I try to record my voice.  Any other suggestions?

Thanks.
lisar915

---

### Post by lidex on 2010-07-10
What was this output:
```
head -n 1 /proc/asound/card*/codec#*
```

And one more:
```
lsmod | grep snd
```

OK, I lied:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by lisar915 on 2010-07-10
@lidex - Here's the output from the terminal after I typed in those commands:

```
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Phoenix Technologies LTD
	Version: R0104X3
	Release Date: 09/01/2004
	Address: 0xE3190
	Runtime Size: 118384 bytes
	ROM Size: 512 kB
	Characteristics:
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		8042 keyboard services are supported (int 9h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		AGP is supported
		Smart battery is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported

```

---

### Post by lidex on 2010-07-10
Have you considered a bios update?
I'm only seeing the output of one command here

---

