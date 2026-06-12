---
title: "Sound blaster live! external - Remote control"
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by sonicste on 2007-01-25
(ubuntu 6.06)
I bought a sound blaster live! external USB; it cames with a remote control that does not work.
I would like to control a LIRC-compatile program.

Please help!!!
Thanks!

---

### Post by Spin Doctor on 2007-01-25
Is the IR receiver a USB stick?

---

### Post by sonicste on 2007-01-26
No, the receiver is embedded into the sound card.

Here is the link to the product:
[http://www.soundblaster.com/products/product.asp?category=1&subcategory=206&product=10702](http://www.soundblaster.com/products/product.asp?category=1&subcategory=206&product=10702)

The soundcard basically works out of the box at least in a stereo configuration.
It is recognized as a SB Live! 24-bit external.
The most annoying thing is that the remote control does not work.

Please help!
Thanks!

---

### Post by sonicste on 2007-01-26
Some news:

According to this document:
[http://www.alsa-project.org/changes/v1-0-11--v1-0-12.txt](http://www.alsa-project.org/changes/v1-0-11--v1-0-12.txt)

The ALSA versione 1.0.12 willa add the support!!!!!!!!!!!!!!!

Ok, now how can I install ALSA 1.0.12?
Any Howto?

Thanks!

---

### Post by Spin Doctor on 2007-01-26
I am running Edgy. And this is the WIKI I used to get my remote to work.

[https://help.ubuntu.com/community/Install_Lirc_Edg](https://help.ubuntu.com/community/Install_Lirc_Edg)

General page about Linux Infrared Remote Control: [www.lirc.org](www.lirc.org)

---

### Post by sonicste on 2007-01-29
sorry for my late answer.

I upgraded to Edgy.
Now I'm following the howto.
[https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)
During the configuration of lirc-modules-source it ask me to select a driver (cmdir. gpio etc...)

Wich Driver should I select to use the receiver of the Sound Blaster Live! external USB?

Thanks!

---

### Post by Squee22 on 2007-01-31
[http://www.develia.org/documents.php?l=2&f=1&p=lirclivedrive](http://www.develia.org/documents.php?l=2&f=1&p=lirclivedrive)

this worked great for me. but mine isn't the USB variant. try this out but replace "Live_midi" with the creative usb driver

---

### Post by sonicste on 2007-02-02
Eureka! now the remote control works!

How-to use the Creative Rm-1500 remote control with sound blaster live! external USB on ubuntu 6.10 Edgy.

1. Install Lirc:
	sudo apt-get install lirc

2. Modify /etc/lirc/hardware.conf
	LIRCD_ARGS="-d hw:External"
	DRIVER="alsa_usb"

4. Edit /etc/lirc/lircd.conf
	copied from a section of this file:
	[http://lirc.sourceforge.net/remotes/creative/lircd.conf.alsa_usb](http://lirc.sourceforge.net/remotes/creative/lircd.conf.alsa_usb)

5. Edit the file ~/.lircrc

6. reboot

7. sudo /etc/init.d/lirc start

8. Test with irw
	
9. sudo irexec (can be started at boot as a daemon with the --daemon option)

Thanks!

---

### Post by Spin Doctor on 2007-02-10
Cool you got it to work!!

---

### Post by dummy_drop on 2007-05-29
> **sonicste said:**
> Eureka! now the remote control works!

How-to use the Creative Rm-1500 remote control with sound blaster live! external USB on ubuntu 6.10 Edgy.

1. Install Lirc:
	sudo apt-get install lirc

2. Modify /etc/lirc/hardware.conf
	LIRCD_ARGS="-d hw:External"
	DRIVER="alsa_usb"

4. Edit /etc/lirc/lircd.conf
	copied from a section of this file:
	[http://lirc.sourceforge.net/remotes/creative/lircd.conf.alsa_usb](http://lirc.sourceforge.net/remotes/creative/lircd.conf.alsa_usb)

5. Edit the file ~/.lircrc

6. reboot

7. sudo /etc/init.d/lirc start

8. Test with irw
	
9. sudo irexec (can be started at boot as a daemon with the --daemon option)

Thanks!

I'm trying to get the remote control to work with my sound blaster live external and feisty.
Is there a more detailed set of instructions?

This is what I have for hardware.conf
> # /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS="-d hw:External"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="alsa_usb"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""


lircd.conf is as follows
> #
# this config file was automatically generated
# using lirc-0.8.0(userspace) on Sun Aug 13 19:42:12 2006
#
# contributed by 
#
# brand:                       Creative
# model no. of remote control: 
# devices being controlled by this remote: Sound Blaster Live! External USB
#

begin remote

  name  Creative_SBL
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          315937
  toggle_bit      0


      begin codes
          touche1                  0x74
          touche2                  0x70
          touche3                  0x6F
          touche4                  0x75
          touche5                  0x7B
          touche6                  0x87
          touche7                  0x76
          touche8                  0x7C
          touche9                  0x88
          touche0                  0x7F
          CMSS                     0x8E
          EAX                      0x73
          vol-                     0x9C
          vol+                     0x9D
          up                       0x84
          down                     0x72
          left                     0x78
          right                    0x8A
          ok                       0x7E
          return                   0x71
          start                    0x77
          cancel                   0x83
          record                   0x8C
          options                  0x7D
          display                  0x89
          previous                 0x80
          playpause                0x86
          next                     0x85
          slow                     0x82
          stop                    0x7A
          step                     0x81
      end codes

end remote

I wasn't sure what to put into the .lircrc file so I left it blank.

When I try /etc/init.d/lirc start, I get
> 
##################################################
## LIRC IS NOT CONFIGURED                       ##
##                                              ##
## read /usr/share/doc/lirc/html/configure.html ##
##################################################

Any ideas?

---

