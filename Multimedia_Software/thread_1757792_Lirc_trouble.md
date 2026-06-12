---
title: "Lirc trouble"
date: 2011-05-13
forum: Multimedia Software
---

### Post by allmondjoy87 on 2011-05-13
I'm trying to get [(**this remote**)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880121003") to work with ubuntu 10.10.  As of now only a few of the buttons are working out of the box (vol+/-, pwr, arrows).

using synaptic i installed lirc and lirc-modules-source.

in the terminal i ran:

```
sudo dpkg-reconfigure lirc
```

and selected "none" for both prompts.

when i try to run irw and establish if my remote is working i get this!

```
brad@brad-Dimension-5100:~$ sudo /etc/init.d/lirc start
brad@brad-Dimension-5100:~$ sudo irw
connect: No such file or directory
brad@brad-Dimension-5100:~$ 
```

has anyone seen this before?

i think the driver is setup right because *some* buttons are working and..

```
brad@brad-Dimension-5100:~$ lsusb
Bus 005 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1784:0008 TopSeed Technology Corp. eHome Infrared Transceiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

/usr/src/lirc-0.8.7~pre3/drivers/lirc/lirc_mceusb.c

```
#define VENDOR_MITSUMI		0x03ee
#define VENDOR_TOPSEED		0x1784
#define VENDOR_RICAVISION	0x179d

...

	/* Topseed eHome Infrared Transceiver */
	{ USB_DEVICE(VENDOR_TOPSEED, 0x0007) },
	/* Topseed eHome Infrared Transceiver */
	{ USB_DEVICE(VENDOR_TOPSEED, 0x0008) },
	/* Topseed eHome Infrared Transceiver */
	{ USB_DEVICE(VENDOR_TOPSEED, 0x000a) },

...

static struct usb_device_id transmitter_mask_list[] = {
	{ USB_DEVICE(VENDOR_MICROSOFT, 0x006d) },
	{ USB_DEVICE(VENDOR_PHILIPS, 0x060c) },
	{ USB_DEVICE(VENDOR_SMK, 0x031d) },
	{ USB_DEVICE(VENDOR_SMK, 0x0322) },
	{ USB_DEVICE(VENDOR_SMK, 0x0334) },
	{ USB_DEVICE(VENDOR_TOPSEED, 0x0001) },
	{ USB_DEVICE(VENDOR_TOPSEED, 0x0006) },
	{ USB_DEVICE(VENDOR_TOPSEED, 0x0007) },
	{ USB_DEVICE(VENDOR_TOPSEED, 0x0008) },
	{ USB_DEVICE(VENDOR_TOPSEED, 0x000a) },
	{ USB_DEVICE(VENDOR_TOPSEED, 0x0011) },
	{ USB_DEVICE(VENDOR_PINNACLE, 0x0225) },
	{}
};

```

i've found a lircd.conf for the remote, and it hasn't added any functionality.  I'm just concerned that irw doesn't do anything at the moment.

help?

---

### Post by vidtek on 2011-05-16
> **allmondjoy87 said:**
> I'm trying to get [(**this remote**)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880121003") to work with ubuntu 10.10.  As of now only a few of the buttons are working out of the box (vol+/-, pwr, arrows).

using synaptic i installed lirc and lirc-modules-source.

in the terminal i ran:

```
sudo dpkg-reconfigure lirc
```and selected "none" for both prompts.

when i try to run irw and establish if my remote is working i get this!

```
brad@brad-Dimension-5100:~$ sudo /etc/init.d/lirc start
brad@brad-Dimension-5100:~$ sudo irw
connect: No such file or directory
brad@brad-Dimension-5100:~$ 
```has anyone seen this before?

i think the driver is setup right because *some* buttons are working and..

```
brad@brad-Dimension-5100:~$ lsusb
Bus 005 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1784:0008 TopSeed Technology Corp. eHome Infrared Transceiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```/usr/src/lirc-0.8.7~pre3/drivers/lirc/lirc_mceusb.c

```
#define VENDOR_MITSUMI        0x03ee
#define VENDOR_TOPSEED        0x1784
#define VENDOR_RICAVISION    0x179d

...

    /* Topseed eHome Infrared Transceiver */
    { USB_DEVICE(VENDOR_TOPSEED, 0x0007) },
    /* Topseed eHome Infrared Transceiver */
    { USB_DEVICE(VENDOR_TOPSEED, 0x0008) },
    /* Topseed eHome Infrared Transceiver */
    { USB_DEVICE(VENDOR_TOPSEED, 0x000a) },

...

static struct usb_device_id transmitter_mask_list[] = {
    { USB_DEVICE(VENDOR_MICROSOFT, 0x006d) },
    { USB_DEVICE(VENDOR_PHILIPS, 0x060c) },
    { USB_DEVICE(VENDOR_SMK, 0x031d) },
    { USB_DEVICE(VENDOR_SMK, 0x0322) },
    { USB_DEVICE(VENDOR_SMK, 0x0334) },
    { USB_DEVICE(VENDOR_TOPSEED, 0x0001) },
    { USB_DEVICE(VENDOR_TOPSEED, 0x0006) },
    { USB_DEVICE(VENDOR_TOPSEED, 0x0007) },
    { USB_DEVICE(VENDOR_TOPSEED, 0x0008) },
    { USB_DEVICE(VENDOR_TOPSEED, 0x000a) },
    { USB_DEVICE(VENDOR_TOPSEED, 0x0011) },
    { USB_DEVICE(VENDOR_PINNACLE, 0x0225) },
    {}
};

```i've found a lircd.conf for the remote, and it hasn't added any functionality.  I'm just concerned that irw doesn't do anything at the moment.

help?

Brad-
I posted a file a while back for the Topseed remote.
The one in the picture looks slightly different to the one they sell here in Australia, but it should still work with my file.

```
 
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.6(default) on Sun Jul 11 11:22:17 2010
#
# contributed by Tony Brown 
# vidtek99@gmail.com
#
# brand: Topseed 
# model no. of remote control: RM-VR1, TSGV-IR05
# Sold in Australia under the ROCK brand distributed by Anywhere
# devices being controlled by this remote:
# MCE style remote : translated to harmony 1100i controls MythTV

begin remote
  name  Topseed
  bits           13
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2709   841
  one           458   429
  zero          458   429
  pre_data_bits   24
  pre_data       0x1BFF83
  gap          106951
  min_repeat      1
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          
      btn_1                    0x1BFE
          btn_2                    0x1BFD
          btn_3                    0x1BFC
          btn_4                    0x1BFB
          btn_5                    0x1BFA
          btn_6                    0x1BF9
          btn_7                    0x1BF8
          btn_8                    0x1BF7
          btn_9                    0x1BF6
          btn_0                    0x1BFF
          key_power                0x1BF3
          key_epg                  0x1BD9
          key_play                 0x1BE9
          key_stop                 0x1BE6
          key_rewind               0x1BEA
          key_fastforward          0x1BEB
          key_record               0x1BE8
          key_back                 0x1BDC
          key_mute                 0x1BF1
          key_enter                0x1BF4
          key_clear                0x1BF5
          key_volumeup             0x1BEF
          key_volumedown           0x1BEE
          key_channelup            0x1BED
          key_channeldown          0x1BEC
          key_left                 0x1BDF
          key_right                0x1BDE
          key_up                   0x1BE1
          key_down                 0x1BE0
          key_ok                   0x1BDD
          key_pause                0x1BE7
          key_next                 0x1BE5
          key_previous             0x1BE4
          key_red                  0x1BA4
          key_green                0x1BA3
          key_yellow               0x1BA2
          key_blue                 0x1BA1
          key_info                 0x1BF0
          key_exit                 0x1BF2
          key_dvd                  0x1BDB
          key_favorites            0x1BA5
          key_radio                0x1BAF
          key_tv                   0x1BDA
          key_video                0x1BB5
          key_zoom                 0x1BD8
          key_pvr                  0x1BB7
          key_player               0x1BB8
          key_file                 0x1BB6
      key_audio           0x1BB8
      key_goto           0x1BA5
      key_media           0x1BB7
      key_menu           0x1BF0

      end codes

end remote



```You need several things to work together to make lirc work correctly.
in /etc/lirc there is a file:   hardware.conf

excerpt from the first part:
> 
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
Note where it says:     REMOTE_DEVICE="/dev/lirc0"

This must relate to your file  /dev/lirc0
sometimes it will be another device such as:   REMOTE_DEVICE="/dev/lircd"

They must match.

Try again from there.

You don't say what end programme you are using, if it's Mythtv you need a lircrc file in the ~/.mythtv folder.
Then remember that naming conventions are critical between the 2 files lircd.conf and .lircrc

if volume up is vol+ in the lircd.conf, ensure the same naming conventions apply in .lircrc

Best of luck, Tony

---

### Post by allmondjoy87 on 2011-05-17
Tony,

just changing the /etc/lirc/hardware.conf doesn't help w/ the irw situation.  So i had to do
```
sudo dpkg-reconfigure lirc
```
again, and then select "Windows Media Center Transceivers/Remotes (all)".  This populated /etc/lirc/hardware.conf to look just like yours.  I don't think that /dev/lirc0 is created unless you go through this process.

After looking in my /dev folder i discovered my computer wanted to make it "lircd" so i changed it in my /etc/lirc/hardware.conf and rebooted.

```
brad@brad-Dimension-5100:~$ ls /dev/lir*
/dev/lircd

```
so now my hardware.conf looks like
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lircd"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
```
2 things happened:

I lost control i previously had with the remote (arrows and vol+/-).  I assume this means lirc has taken over whatever driver was previously running?

```
sudo irw -d
``` worked (appeared to hang)! but it didn't print anything to screen when i mashed the remote.  However the light on the receiver still blinked w/ every push.

i have a pretty old computer (pentium 4 era) so i'm looking to run something light, haven't decide between boxee or xbmc w/ a minimal skin yet.  

If i'm not running xbmc/boxee i shouldn't need to match the lircd files correct?  For example, shouldn't the volume+/- work from the desktop once i get lirc running correctly?  I was hoping to get some feedback from irw before i jumped into matching lircd.conf files.

finally, where should the lircd.conf file be stored? Can i move it to /etc/lirc and then point "REMOTE_LIRCD_CONF" in hardware.conf to look for it there?  Should i append what you supplied to the one in mceusb/lircd.conf.mceusb? or should i just use what you gave me and overwrite the one lirc generated?

thanks for your help man!

-brad

---

### Post by vidtek on 2011-05-17
Brad-

Firstly the end programme you use dictates where the files go.
If you don't intend to use Mythtv then disregard the .lircrc file altogether.

> just changing the /etc/lirc/hardware.conf doesn't help w/ the irw situation. So i had to do
Code:
sudo dpkg-reconfigure lirc
again, and then select "Windows Media Center Transceivers/Remotes (all)". This populated /etc/lirc/hardware.conf to look just like yours. I don't think that /dev/lirc0 is created unless you go through this process.

After looking in my /dev folder i discovered my computer wanted to make it "lircd" so i changed it in my /etc/lirc/hardware.conf and rebooted.
Reconfiguring lirc as at the top of your post is spot on to get the correct drivers for your remote, as is changing the lirc0 to lircd. 

It is imperative to get irw working (as root) before you go any further (incidentally what is the -d parameter on your command?)
I have found it's better to do a reboot rather than trying to stop/restart the lirc daemons between attempts to get things working.

Tony.

---

### Post by allmondjoy87 on 2011-05-18
ignore that -d, i must have been sleepy when i wrote that.  when i type 
```
sudo irw
```
and press any button on the remote nothing happens...

what should irw be outputting when i press buttons?  Does irw only work assuming i have a lircd.conf that corresponds to my remote?  Or should it be printing whatever is on the socket?  If irw outputs nothing, does this mean my driver isn't working correctly?

---

### Post by vidtek on 2011-05-19
> **allmondjoy87 said:**
> ignore that -d, i must have been sleepy when i wrote that.  when i type 
```
sudo irw
```
and press any button on the remote nothing happens...

what should irw be outputting when i press buttons?  Does irw only work assuming i have a lircd.conf that corresponds to my remote?  Or should it be printing whatever is on the socket?  If irw outputs nothing, does this mean my driver isn't working correctly?

Brad-

silly me I tried to replicate your problems and stuffed my system.

I will have to restore from a ghost image when I get time.

No time at the moment, work pressures, sorry can't help for a while, maybe someone else can assist.

Tony.

---

### Post by vidtek on 2011-05-20
> **vidtek said:**
> Brad-

silly me I tried to replicate your problems and stuffed my system.

I will have to restore from a ghost image when I get time.

No time at the moment, work pressures, sorry can't help for a while, maybe someone else can assist.

Tony.

OK got a few mins.  

I purged lirc completely after frying it before 
```

sudo apt-get purge lirc

```

then installed mythbuntu control centre ```


sudo apt-get install mythbuntu-control-centre
```

(note the correct spelling of centre for our colonial friends across the Pacific)

and click the link for infra-red 

it all works well again.

Mythtv is a pain to install but so worth the effort.

Best regards, Tony.

---

### Post by allmondjoy87 on 2011-05-23
thanks man,

i'll give it a shot when i get home and let you know how it works

---

### Post by allmondjoy87 on 2011-06-02
Still no dice on this topic... has anyone gotten this remote to work correctly with their setup?

---

### Post by vidtek on 2011-06-02
> **allmondjoy87 said:**
> Still no dice on this topic... has anyone gotten this remote to work correctly with their setup?

Ok, off work now, broke my right collarbone so 1 left-finger typing and left mouse real slowwwwww....

how far did you get, did you purge lirc?

Tony

---

### Post by allmondjoy87 on 2011-06-02
> **vidtek said:**
> Ok, off work now, broke my right collarbone so 1 left-finger typing and left mouse real slowwwwww....

how far did you get, did you purge lirc?

Tony

i did, and followed your other instructions as best i could.  would you mind doing your steps in a terminal and copy/pasting them here so i can see what we are doing differently?

---

### Post by vidtek on 2011-06-02
> **allmondjoy87 said:**
> i did, and followed your other instructions as best i could.  would you mind doing your steps in a terminal and copy/pasting them here so i can see what we are doing differently?

Brad-

If you go back to post #7, and purge lirc and then install myth control centre as in that post, that should get irw to work.
here is a sample from irw.

```
tony@workshopultimate:~$ irw
000000037ff07bdd 00 OK mceusb
000000037ff07bdd 01 OK mceusb
000000037ff07bde 00 Right mceusb
000000037ff07bde 01 Right mceusb
000000037ff07bde 02 Right mceusb
000000037ff07bde 00 Right mceusb
000000037ff07bde 01 Right mceusb
000000037ff07bdf 00 Left mceusb
000000037ff07bdf 01 Left mceusb
000000037ff07bfe 00 One mceusb
000000037ff07bfe 01 One mceusb
000000037ff07bf7 00 Eight mceusb
000000037ff07bf7 01 Eight mceusb
000000037ff07bf2 00 Home mceusb
000000037ff07bf2 01 Home mceusb
000000037ff07be9 00 Play mceusb
000000037ff07be9 01 Play mceusb
000000037ff07be9 02 Play mceusb
000000037ff07be6 00 Stop mceusb
000000037ff07be6 01 Stop mceusb
000000037ff07be6 02 Stop mceusb
000000037ff07bea 00 Rewind mceusb
000000037ff07bea 01 Rewind mceusb
```

mythtv is very resource light if you have a slow machine.

Tony.

---

### Post by allmondjoy87 on 2011-06-08
there's gotta be something i'm missing...
```
**brad@brad-Dimension-5100:**~$ sudo apt-get purge lirc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lirc is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libftdi1 python-mysqldb setserial mythbuntu-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
**brad@brad-Dimension-5100:~$** sudo apt-get purge mythbuntu-control-centre 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mythbuntu-control-centre is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libftdi1 python-mysqldb setserial mythbuntu-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
**brad@brad-Dimension-5100:~$** sudo apt-get install mythbuntu-control-centre 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libftdi1 setserial
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mythbuntu-control-centre
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/108kB of archives.
After this operation, 893kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  mythbuntu-control-centre
Install these packages without verification [y/N]? y
Selecting previously deselected package mythbuntu-control-centre.
(Reading database ... 150507 files and directories currently installed.)
Unpacking mythbuntu-control-centre (from .../mythbuntu-control-centre_0.62-0ubuntu1_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up mythbuntu-control-centre (0.62-0ubuntu1) ...
Processing triggers for python-central ...
**brad@brad-Dimension-5100:~$** irw
The program 'irw' is currently not installed.  You can install it by typing:
sudo apt-get install lirc
**brad@brad-Dimension-5100:~$** 

```

thanks for all of your help so far

---

### Post by vidtek on 2011-06-09
> **allmondjoy87 said:**
> there's gotta be something i'm missing...
```
**brad@brad-Dimension-5100:**~$ sudo apt-get purge lirc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lirc is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libftdi1 python-mysqldb setserial mythbuntu-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
**brad@brad-Dimension-5100:~$** sudo apt-get purge mythbuntu-control-centre 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mythbuntu-control-centre is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libftdi1 python-mysqldb setserial mythbuntu-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
**brad@brad-Dimension-5100:~$** sudo apt-get install mythbuntu-control-centre 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libftdi1 setserial
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mythbuntu-control-centre
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/108kB of archives.
After this operation, 893kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  mythbuntu-control-centre
Install these packages without verification [y/N]? y
Selecting previously deselected package mythbuntu-control-centre.
(Reading database ... 150507 files and directories currently installed.)
Unpacking mythbuntu-control-centre (from .../mythbuntu-control-centre_0.62-0ubuntu1_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up mythbuntu-control-centre (0.62-0ubuntu1) ...
Processing triggers for python-central ...
**brad@brad-Dimension-5100:~$** irw
The program 'irw' is currently not installed.  You can install it by typing:
sudo apt-get install lirc
**brad@brad-Dimension-5100:~$** 

```

thanks for all of your help so far

Brad-
Go to Mythbuntu Control Centre (from your desktop applications menu)scroll down to infra-red and install a remote.

Tony

---

