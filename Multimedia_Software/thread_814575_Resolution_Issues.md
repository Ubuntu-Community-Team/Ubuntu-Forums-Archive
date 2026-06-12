---
title: "Resolution Issues"
date: 2008-05-31
forum: Multimedia Software
---

### Post by koster.will on 2008-05-31
I trust this is the correct Forum... 
Regardless, today is my first day using Ubuntu, so I am quite new to this environment. I have tried multiple fixes to set my resolution higher than 800x600 but Xorg continues to confound me by placing my resolution quite small. I am running the integrated Via Unichrome Pro chipset on my Intel board with an old CRT. (I already have refresh rates etc. defined through nano...) Can anyone help me? Just let me know what info you need to help me diagnose this very annoying problem...

---

### Post by unutbu on 2008-05-31
To change resolution, you might want to try these commands

```

gnome-display-properties
gksudo displayconfig-gtk
sudo dpkg-reconfigure -phigh xserver-xorg

```
I think they all do basically the same thing, but if one doesn't work, it wouldn't hurt to try the others.

If none of that works, please post

```
lspci
lsusb
sudo lshw -C video
cat /etc/X11/xorg.conf | perl -ne "print unless (m/^#/)"

```

---

### Post by koster.will on 2008-05-31
I attempted to use the first basic screen resolution script but since it is the same as the option set under system and draws from the same source code, it didn't change anything. The gksudo script you posted allowed me to set the monitor as a CRT with 1280x1024 as 'natural' resolution along with setting the video card as Via and not the Vega or whatever Xorg determined mine to be. However, upon a reset of Xorg after saving the settings, nothing had changed. The reconfiguration script I could not access:

```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080531205518

```

I have attached the data you requested... Thank you for your help, even if I fail at implementing it successfully...

---

### Post by koster.will on 2008-06-01
I have tried specifying the monitor a number of different ways... but Xorg is just not recognizing my onboard video card or my monitor. (Both of which are old...) It wouldn't have anything to do with my OC'ing the processor and video card would it?

---

### Post by housam on 2008-06-01
try this :
System > Preferences > Screen Resolution
If you didn't find your settings , try the following :

```
sudo nano /etc/usplash.conf
```
 you will got something like that 

> # Usplash configuration file
# These parameters will only apply after running update-initramfs. 
 
add the required resolution 

> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=[COLOR="red"]1280[/COLOR]
yres=[COLOR="Red"]800[/COLOR] 
 
set [COLOR="red"]x & y[/COLOR] as you want then reboot and type :

```
sudo dpkg-reconfigure usplash
```
 then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________

---

### Post by unutbu on 2008-06-01
I don't have an experience with OC'ing. Does that affect the maximum pixel clock of the card?

Let's check that the via module is present and loaded by the kernel:
```
lsmod | grep via
locate via.ko
```

Let's check to see what via driver you have available:
```
apt-cache policy xserver-xorg-video-via
apt-cache policy xserver-xorg-video-unichrome
apt-cache policy xserver-xorg-video-savage
apt-cache policy xserver-xorg-video-openchrome
```

Let's try to manually force X to use the via driver, by adding the "Driver" line to the "Device" Section of /etc/X11/xorg.con:
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"via"
EndSection
```

After you edit /etc/X11/xorg.conf, log out of your Xsession and then press Ctrl-Alt-Backspace to restart X. Please post /var/log/Xorg.0.log.

Here is [an example of an xorg.conf for the Via S3 Unichrome pro igp]("http://ubuntuforums.org/showthread.php?t=514704").

---

### Post by koster.will on 2008-06-01
Thank you for your responses. The first script, /etc/usplash.conf, the resolution is 1024 x 768, but that resolution is not usable in my screen resolution under system - preferences.

Upon a reboot and then running the second script, nothing changes...

When querying the system for Via data, it outputs

```
snd_via82xx            29464  3 
gameport               16008  1 snd_via82xx
snd_ac97_codec        101028  1 snd_via82xx
snd_pcm                78596  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9728  1 snd_via82xx
snd                    56996  20 snd_rtctimer,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro              9876  0 
i2c_core               24832  1 i2c_viapro
via_agp                11136  1 
agpgart                34760  1 via_agp
via_rhine              26632  0 
mii                     6400  1 via_rhine
sata_via               12420  0 
pata_via               13316  2 
libata                159344  4 pata_acpi,sata_via,pata_via,ata_generic

```

via.ko outputs

```
/lib/modules/2.6.24-16-generic/kernel/drivers/ata/pata_via.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/ata/sata_via.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/char/drm/via.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/i2c/busses/i2c-via.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/ata/pata_via.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/ata/sata_via.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/char/drm/via.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/i2c/busses/i2c-via.ko

```

```
xserver-xorg-video-via:
  Installed: 1:0.2.2-5
  Candidate: 1:0.2.2-5
  Version table:
 *** 1:0.2.2-5 0
        500 http://ca.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status

xserver-xorg-video-unichrome:
  Installed: (none)
  Candidate: 1:0.2.6.99-0ubuntu1
  Version table:
     1:0.2.6.99-0ubuntu1 0
        500 http://ca.archive.ubuntu.com hardy/universe Packages

xserver-xorg-video-savage:
  Installed: 1:2.1.3-5
  Candidate: 1:2.1.3-5
  Version table:
 *** 1:2.1.3-5 0
        500 http://ca.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status

xserver-xorg-video-openchrome:
  Installed: 1:0.2.901-0ubuntu4
  Candidate: 1:0.2.901-0ubuntu4
  Version table:
 *** 1:0.2.901-0ubuntu4 0
        500 http://ca.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status

```

I am trying the edit of the X11 file now...

---

### Post by koster.will on 2008-06-02
bump?

---

### Post by unutbu on 2008-06-02
Make a copy of your current xorg.conf just in case.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-20080602
sudo gedit /etc/X11/xorg.conf
```
Edit xorg.conf to include the lines in bold:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	**Driver		"via"**
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
   	[B]Option          "DPMS"
        HorizSync       30.0 - 70.0
        VertRefresh     50.0 - 160.0[/B]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        [B]DefaultDepth    16
   	SubSection "Display"
   	   Modes        "1280x1024"
   	EndSubSection[/B]
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

Log out of your gnome/X session. Press Ctrl-Alt-Backspace to restart X. Is your resolution now 1280x1024? Hopefully this will work.

If it does not, press Ctrl-Alt-F2 and log in to get to a text terminal. 

First, collect some data about the running X process:

```
cat /var/log/Xorg.0.log > ~/Xoutput
xvidtune -display :0.0 -show >> ~/Xoutput
```

Next, revert back to the old xorg.conf:

```
cd /etc/X11
sudo cp xorg.conf-20080602 xorg.conf
```

Press Ctrl-Alt-F7 to get back to the X session, and press Ctrl-Alt-Backspace to restart X again. Please post the contents of ~/Xoutput.

---

### Post by koster.will on 2008-06-02
bump....?

---

### Post by Dave Otter on 2008-06-02
alt + F2 >>sudo displayconfig-gtk
click on Model then chose your screan model >> ok

---

