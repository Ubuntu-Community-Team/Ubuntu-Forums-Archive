---
title: "Multiple Sound Cards"
date: 2008-09-17
forum: Multimedia Software
---

### Post by markbuntu on 2008-09-17
Multiple Sound Cards/Hardware Devices

Many people here seem to be under the impression that Ubuntu does not support more than one sound card and that having more than one sound card will create insoluble difficulties. **This is not true.** Setting up for multiple sound cards/devices takes little time and a little understanding about how to do it, that's all. You can have your multiple sound devices up and running in 10 minutes or less by following these directions. If you have any usb devices this will help you.

If your sound card is listed in System/Preferences/Sound, you can make use of it. You can use as many sound cards as you can fit in or on your computer. You can use them separately, or combine them into a number of useful configurations. Many  semi-solutions have been available with ALSA for quite a while but this generally involves skillful editing of the asoundrc file and does not address the problematic issue of synchronization of sound device clocks. A gradual drift in clock timing makes these ALSA solutions only partly successful. There are some high end professional audio cards like the Hammersmith and M-Audio line that have provisions for clock timing synchronization, but they are far beyond the needs and pocketbooks of most users. This is about setting up your system so controlling multiple sound devices is easy and convenient.

** Assigning Default Devices**
A common problem that arises with multiple pci sound cards/devices is that they are not always assigned the same device number on each boot. This can result in an undesirable change in the default ALSA sound device. In order to remedy this problem we can explicitly assign the default device numbers of our sound card drivers by adding lines at the end of the  /etc/modprode.d/alsa-base file like this (These are mine):
```

options snd_hda_intel index=0
options snd_cmipci index=1
options snd_atiixp index=2
options snd_usb_audio index=3

```

This way each device will always be numbered the same. 

You can use:
```

cat /proc/asound/modules

```
 to discover your sound device driver module names and their order. The code is the the driver names, not the sound card names so be sure to use the driver names or you will get errors when ALSA starts up. You can change the order around as you desire. There is more on assigning cards here

[http://alsa.opensrc.org/index.php/MultipleCards](http://alsa.opensrc.org/index.php/MultipleCards)

For multiple usb devices

[http://alsa.opensrc.org/index.php/MultipleUSBAudioDevices](http://alsa.opensrc.org/index.php/MultipleUSBAudioDevices)

**Changing Your Default Sound Card**
The biggest problem with multiple sound cards seems to be that many people do not know how to direct their applications to use one or the other.
If you are using just ALSA the easiest way to choose between multiple sound cards is to get:

asoundconf-gtk 

This little application can be found in System/Preferences as Default Sound Card. Open it and choose your default sound card. All your applications going through ALSA will now use this card. But, to use your other sound card, you must change the default again and this will effect all your applications and they must be restarted for the changes to take place. 

If you are using PulseAudio, you can choose pulseaudio in Default Sound Card and use the PulseAudio Volume Control to direct your application to whichever sound card you want to use while they are playing and without restarting them.

** Using Multiple Sound Cards with PulseAudio**
If you still have bad feelings about PulseAudio, it is due more to an incomplete implementation in the default Ubuntu installation than the Pulse Audio program itself or its developers. If you would like to get PulseAudio working properly and have all your applications use it so you can use more than one sound card more effectively, you can follow my guides here:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If you need more extensive help you can go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If you do not have your sound set up so all your applications play through PulseAudio and have applications that bypass PulseAudio or are using OSS4, then the following will not necessarily give you positive results. If you are using jackd, there is some information in the second guide above that may also be helpful to understanding this issue.

PulseAudio will automatically detect and make available any sound card which ALSA can find and has a driver for. Unfortunately, PulseAudio is currently unable to detect secondary audio devices that ALSA does not detect as Device 0. This includes digital outputs, secondary dacs, and sound devices incorporated into some newer video cards. These can still be controlled from the ALSA mixers but PulseAudio is unable to detect and use them at this time. This has been fixed in Pulseaudio 0.0.15 which is unfortunately not available for Ubuntu users yet. But there is a way to add support in Pulseaudio for these devices manually. Directions for doing so are here

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

** Controlling Playback and Devices with Multiple Sound Cards**
The PulseAudio Volume Control will list all the the devices it can detect in the Output Devices tab. It will also list all applications that are currently using the Pulse Audio sound server in the Playback window.  You can right click on any application in that window and choose Move Stream to move it to another device. It is that simple.  You can also control the volume of both individual playback streams and the output devices by moving the sliders. You can select any listed output device as the default by right clicking on it.

Another way to control the volume of any device you are using is to select it with the Volume Control applet on your panel. You can use your mixer directly or you can select the mixer in the Volume Control by right clicking and choosing Open Volume Control/File/Change Device. This will allow you to choose and control any hardware or virtual device. To use your multimedia keys for control you need to select the device in System/Preferences/Sound/Default Mixer Tracks.

**Simultaneous Output**

In the PA Device Chooser/Configure Local Sound Server/Simultaneous Output there is a check box for Simultaneous Output to all local sound cards. If you select it this will add a new Output Device in the PA Volume Control listings 
Simultaneous output to ALSA PCM.......(all your sound hardware devices).......
You can select this device in the PA Volume Control just like any other and it will direct streams to all your sound devices simultaneously so you can have sound in your speakers and usb headset etc at the same time.

**Combining Sound Cards**
PulseAudio also has provisions for making and using more versatile virtual devices like module-combine and module-oss-mmap.To use these, we must edit the etc/pulse/default.pa file to call the modules.

This is how you can manually create a virtual device that will allow you to output to two sound cards at the same time using module-oss-mmap and module-combine:

Open etc/pulse/default.pa in an editor as sudo.

```

sudo gedit /etc/pulse/default.pa

```

At the end of the file, add these lines
```

load-module module-oss-mmap device="/dev/dsp" sink_name=output0
load-module module-oss-mmap device="/dev/dsp1" sink_name=output1
load-module module-combine sink_name=combined master=output0 slaves=output1
set-sink-default combined

```

You can have more than one slave sink attached to the combined sink, and hence combine any number of sound cards. 

**Using Multiple Sound Cards for Surround Sound**
You can also use multiple sound cards for surround sound by combining them and remapping the outputs. 

```

    load-module module-oss-mmap device="/dev/dsp" sink_name=output0 channel_map=left,right channels=2
    load-module module-oss-mmap device="/dev/dsp1" sink_name=output1 channel_map=rear-left,rear-right channels=2
    load-module module-combine sink_name=combined master=output0 slaves=output1 channel_map=left,right,rear-left,rear-right channels=4

```
    The channel mappings for the sinks must be explicit to make sure everything is routed correctly. Once again, you can use any number of cards as slaves, explicitly mapping their outputs. module-oss-mmap can also be used to remap the outputs of a single sound card.


If you have any questions or problems or additions or comments, please feel free to post here.

Best Regards,

Mark

EDIT: 02/22/09 Major edit

---

### Post by stoneage on 2008-09-27
Every once in a while(about weekly, sometimes two or three times a week), I boot into silence and have to change the sound configuration to get it working again. I have onboard sound - HDA Intel, and an SB Audigy(ca0106) and sometimes switching 'Sound Preferences => 'Default Mixer Tracks' from HDA to ca0106 fixes it, sometimes switching 'Multimedia Systems Selector' => 'Default Output'from ALSA to Autodetect, sometimes to ESD or OSS.

Any idea what might be causing the loss of sound?


64 bit Ubuntu Hardy

---

### Post by markbuntu on 2008-09-27
The most likely reason is that your computer is assigning different irqs to your sound card sometimes when it boots up. If you follow the part above labeled  Assigning Default Devices you can avoid that problem by specifically setting the device numbers of your card so they are consistent over reboots.

---

### Post by stoneage on 2008-09-27
Thanks for the information, I hope it is that simple, it has been going on for over a year.

aplay -l gives me:-

```
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So if I add:-

```
options snd_ca0106 index=0
options snd_ca0106 index=1
options snd_ca0106 index=2
options snd_ca0106 index=3
options snd_hda_intel index=4
options snd_hda_intel index=5

```

to alsa-base, would that be right?

---

### Post by markbuntu on 2008-09-27
No, you should just have to list each card once.

options snd_ca0106 index=0
options snd_intel index=1

---

### Post by markbuntu on 2008-09-27
I made a serious error in the OP. You need to use

```

cat /proc/asound/modules

```
to determine how to edit etc/modprobe.d/alsa-base

I am so sorry for anyone I have misled. Anyway, it is fixed.

---

### Post by stoneage on 2008-09-28
cat /proc/asound/modules lists:-

organic@organic-desktop:~$ cat /proc/asound/modules
 0 snd_ca0106
 1 snd_hda_intel


Is there anything else it could be? It has been a problem since installing Gutsy then continued after updating to Hardy, so I'm considering a clean install for Intrepid but would rather know what the problem is. 

Thanks for your assistance.

EDIT - Whoops; sorry, I misread that. I have added 
options snd_ca0106 index=0
options snd_intel index=1

to /etc/modprobe.d/alsa-base and will post back in a few days to update if it solves it. Thanks again.

---

### Post by dgoddard1 on 2008-09-30
Markbuntu,  I followed your suggestion that I come here from 
     [http://ubuntuforums.org/showthread.php?p=5877560#post5877560](http://ubuntuforums.org/showthread.php?p=5877560#post5877560)
And I am at least marginally in over my head here.  

To save time for those who wonder what this is about, My sound system went dead apparantly when I got gnome-ppp installed and a few other things that got my usb modem working on my new laptop.

I did try using the cat command in an attempt to clairify my situation and turned up the following responses.

First, In terminal mode I tried what is between the ####'s:
##############
user1@dell-desktop:~$ cat /proc/asound/modules
 0 snd_hda_intel
user1@dell-desktop:~$ 
##############

Second, in terminal mode  I tried what is between the XXXXX's:
XXXXXXXXXXXXXXX
user1@dell-desktop:~$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
user1@dell-desktop:~$ 

XXXXXXXXXXXXXXX

I see some indication in the last stuff above about modem and usb ports, but I don't really grasp the significance.  I specifically note the modem and usb entries because my modem is a usb modem since Dell did not see fit to build in a modem on the Studio laptop 1535 they sold me.

Can anyone here see what I should do next.

---

### Post by markbuntu on 2008-10-01
I don,t have more than a minute here but the 0 before snd_hda)intel indicates the module has been disabled, maybe by ppp.
Look in 

/etc/modprode.d/alsa-base 

and remove the 0 from in front of the snd_had_intel if you can find it. I will be back after work and give you a hand if no one else can.

---

### Post by dgoddard1 on 2008-10-01
> **markbuntu said:**
> ... the 0 before snd_hda)intel indicates the module has been disabled, maybe by ppp.
Look in 

/etc/modprode.d/alsa-base 

and remove the 0 from in front of the snd_had_intel if you can find it. ...

I did a search of /etc/modprobe.d/alsa-base using gedit.  no phrase containing "had" can be found, let alone "snd_had_intel"

---

### Post by eponymous on 2008-10-01
thanks for this. i'm going to try using your pulseaudio info to get an extra line in for my turntable.

---

### Post by Yellow Pasque on 2008-10-01
> **dgoddard1 said:**
> I did a search of /etc/modprobe.d/alsa-base using gedit.  no phrase containing "had" can be found, let alone "snd_had_intel"
It's a typo. The module is snd-hda-intel (HDA = High Definition Audio)

---

### Post by stoneage on 2008-10-01
I'm afraid it didn't work out.

With sound working and 
 ```
cat /proc/asound/modules
 0 snd_ca0106
 1 snd_hda_intel

```

I added 
```
#Explicitly assign the default device numbers of the sound cards
options snd_ca0106 index=0
options snd_intel index=1
```

to /etc/modprobe.d/alsa-base and today booted into silence with
 ```
cat /proc/asound/modules
 0 snd_hda_intel

```

It seems the soundcard has been removed as an option. ca0106 isn't listed under System => Preferences => Multimedia Systems Selector or under any of the System => Preferences => Sound options. 


Any idea what might be going on ?

---

### Post by markbuntu on 2008-10-01
You put in the wrong thing. You used snd_intel index=1 instead of 

snd_hda_intel index=1

The 0 you see in /proc/asound/modules means that device is disabled. Try again and reboot.

---

### Post by stoneage on 2008-10-01
So I disabled the soundsystem?

Duhh! How am I going to learn the command line when I haven't yet learned how to read and write.

Thank you, I made the change and still have sound. I'll check it out over the next few days. I work with 3D cgi software, modeling during the day and rendering the images overnight, so sometimes the machine is running for days at a time. It's looking(sounding) good though, you may have saved me the time and trouble of recustomising after a clean install with Intrepid.

---

### Post by stoneage on 2008-10-01
.........and I double posted.......

---

### Post by markbuntu on 2008-10-01
If you really need that machine, do not jump to Intrepid unless you have some insoluble problem that has a known fix. In other words you find something that says Intrepid kernel 2.6.27 includes the fix for known problem blah blah blah... which is your exact problem. 

Also, it would be a good idea to peruse the Launchpad Intrepid bug site and the Development forum here before jumping.

---

### Post by stoneage on 2008-10-01
Well, ironically enough it was the sound I was hoping to fix; that and being able to use gcc-4.3, but I have a copy of that from Launchpad(working fine), so I suppose I should go check that out. As far as I am aware it is included with 8.10. The only other thing is to update the graphics driver - just can't find the time to build one. Thanks for the heads up - I will look into it and consider carefully. Haven't visited the Development forum yet - on my way now.

---

### Post by dgoddard1 on 2008-10-01
> **Temüjin said:**
> It's a typo. The module is snd-hda-intel (HDA = High Definition Audio)

Uhhhh, I am still stuck, I went back and searched with the hda instead of had and did not find it either.  Is the problem in alsa-base?  I really don't know how to read that file yet.

---

### Post by markbuntu on 2008-10-02
> **dgoddard1 said:**
> Uhhhh, I am still stuck, I went back and searched with the hda instead of had and did not find it either.  Is the problem in alsa-base?  I really don't know how to read that file yet.

Most likely you are running a script that is disabling your sound card or changing it from the default.

Where did you get the directions on how to set up the modem and connection. Can you give me a link?

---

### Post by dgoddard1 on 2008-10-02
> **markbuntu said:**
> Most likely you are running a script that is disabling your sound card or changing it from the default.

Where did you get the directions on how to set up the modem and connection. Can you give me a link?

So far as I know, the only 2 things that I did were
A.
Install gnome-ppp from the .deb file I downloaded and put in the phone number etc. of my internet service provider
B.
Follow steps 1-3 of the troubleshooting instructions for Linux on the CD that came with my US Robotics Model 5637 usb modem.  I have cut and pasted those instructions below:  After completeing step 3 the modem worked.  The next day I noticed that I did not have any sound but I had not done anything else in the intrim except some browsing and e-mail.

##### US Robotics Trouble Shooting instructions follow: #####

Troubleshooting:

Open a terminal shell and log in as root.

1. Verify modem enumeration with the following command:

lsusb

Below is an example output.

Bus 001 Device 002: ID 0baf:0303 U.S. Robotics

2. Verify the CDC ACM module as loaded with the following command:

lsmod

If the version of Linux kernel has the CDC ACM driver compiled into it, you
should now be able to use a terminal emulator program (for example: minicom)
to attach to the modem.

If the kernel has the CDC ACM driver built as a module, then you may have to
enable the driver with the following command:

modprobe acm
(used in 2.4.x kernels)

modprobe cdc_acm
(used in 2.6.x kernels)

3. Verify device node creation.

Some distributions will automatically create a device node
for the modem in /dev. Below is the device node as created in Fedora 7.

crw-rw---- 1 root uucp 166, 0 2007-09-12 10:33 ttyACM0

The CDC ACM driver allows up to 32 modems. If the device node does not exist,
create one using the following command:

mknod /dev/ttyACM0 c 166 0

Additional device nodes can be created for additional modems as follows:

mknod /dev/ttyACM1 c 166 1
mknod /dev/ttyACM2 c 166 2
mknod /dev/ttyACM3 c 166 3

4. Access the modem.

Use a terminal emulator program (for example: minicom) to access the modem using
the device node created above. For example, setup the serial port for minicom to
use the device node /dev/ttyACM0.

5. Internet dialers.

Applications such as WvDial and KPPP may require access to the modem via the
/dev/modem device node.

You can set up a symbolic link from /dev/modem to the ACM modem device by using
the following command:

ln -s /dev/ttyACM0 /dev/modem

##### US Robotics Trouble Shooting instructions end: #####

---

### Post by markbuntu on 2008-10-03
Hmmm... sorry  for making you wait. What does aplay -l tell you?

---

### Post by dgoddard1 on 2008-10-05
> Hmmm... sorry for making you wait. What does aplay -l tell you? 

####### results of aplay -l #########

user1@dell-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
user1@dell-desktop:~$ 

####### end results of aplay -l #########

---

### Post by markbuntu on 2008-10-06
Try this, at the end of /etc/modprobe.d/alsa-base add this line:

options snd_hda_intel index=0

Also, you can look in this guide here which is pretty comprehensive for sound troubleshooting and fixing messed up configurations. Do not be afraid to follow the links:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by dgoddard1 on 2008-10-06
There are known problems involving the sound and modem interfering with each other at 
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues)
They are listed as problems #1 & #2.  These sound very much like my problem except that my problem was not precipitated by upgrading the version or the kernel.

I would appreciate knowing if anyone with more substantial understanding than mine believes that replacing the sound card driver and/or the modem driver is what my case requires similar to what is done in cases #1 and #2.  Should that be the case, I would need to know which terminal mode commands apply in my case.  I have a little knowledge of such things and could guess but a little knowledge can be a dangerous thing.

---

### Post by bring on 2008-10-31
Thanks for your clear explanation of pulseaudio, i do have one remaining question though..

> **markbuntu said:**
> Multiple Sound Cards

** Controlling Playback and Devices with Multiple Sound Cards**
The PulseAudio Volume Control will list all the the devices it can detect in the Output Device Window. It will also list all applications that are currently using the Pulse Audio sound server in the Playback window.  You can right click on any application in that window and choose Move Stream to move it to another device. It is that simple.  You can also control the volume of both individual playback streams and the output devices by moving the sliders. You can select any listed output device as the default by right clicking on it.



I have 2 sound devices, i have made one of those devices 'default sink'.
Whenever i use PulseAudio Volume Control to select a playback application to send it's output to the non-default sink, that works fine, but when i quit that particular application and start it the next time, it will revert to output to the default sink again.
 
Is there any way to permanently bind an application to a certain sink?

---

### Post by markbuntu on 2008-10-31
Hmmm, that is a very good question, something I have never considered since it is so easy to change the streams but I can see how that would be very handy. I will do a little research and post a reply here. In the meanwhile, if you find a way to do this please post it here and I will add it to the OP.

Thanks for bringing that up.

---

### Post by bring on 2008-11-09
Right, i've figured out what the problem was. 

In Ubuntu, the pulseaudio daemon is started with the "--system" option, which means that the daemon runs system-wide, and as a result the saved settings for volume, sink etc. are not stored per-user, but system-wide (see also [http://www.pulseaudio.org/wiki/SystemWideInstance]("http://www.pulseaudio.org/wiki/SystemWideInstance"))

After starting the daemon without the system-wide option, the sink and volume info is properly stored and retrieved.

---

### Post by markbuntu on 2008-11-09
> **bring said:**
> Right, i've figured out what the problem was. 

In Ubuntu, the pulseaudio daemon is started with the "--system" option, which means that the daemon runs system-wide, and as a result the saved settings for volume, sink etc. are not stored per-user, but system-wide (see also [http://www.pulseaudio.org/wiki/SystemWideInstance]("http://www.pulseaudio.org/wiki/SystemWideInstance"))

After starting the daemon without the system-wide option, the sink and volume info is properly stored and retrieved.

I was sort of wondering why that was happening since pulseaudio was not doing that to me.

---

### Post by edyeeh on 2008-11-09
> cat /proc/asound/modules

```
choi@Edgene:~$ cat /proc/asound/modules
cat: /proc/asound/modules: No such file or directory
```

this happened to me. I can't find the alsa mixer in the sound preferences either.

---

### Post by markbuntu on 2008-11-11
Is your sound working at all?

---

### Post by psyke83 on 2008-11-11
> **bring said:**
> Thanks for your clear explanation of pulseaudio, i do have one remaining question though..



I have 2 sound devices, i have made one of those devices 'default sink'.
Whenever i use PulseAudio Volume Control to select a playback application to send it's output to the non-default sink, that works fine, but when i quit that particular application and start it the next time, it will revert to output to the default sink again.
 
Is there any way to permanently bind an application to a certain sink?

Yes, it's possible - there's two options.

Option 1:
1. Delete your PulseAudio user configuration:```
$ rm ~/.pulse/*
```
2. Open PulseAudio Volume Control, Output Devices tab. Right-click on desired output device and set as default.

N.B.: you need to delete your ~/.pulse/volume-restore.table as it saves the recently-used sink for applications. This means that applications will used their last-saved sink rather than the default sink. Deleting this file resolves the problem (though you can manually move streams per-application via PA Volume Control if you wish).

Option 2 (if the first method doesn't work):
1. Open the PulseAudio Manager, Devices tab. Double-click on the sink that you wish to make the default, and copy the entire device name to the clipboard.

2. Edit /etc/pulse/default.pa:
```
$ gksudo gedit /etc/pulse/default.pa
```

At the end of the file, you'll see these three lines:
```
### Make some devices default
#set-default-sink output
#set-default-source input
```

Change the middle line to:
```
### Make some devices default
set-default-sink [COLOR="Red"]desiredsinkname[/COLOR]
#set-default-source input
```

N.B. Be sure to remove the comment (#), and replace [COLOR="Red"]desiredsinkname[/COLOR] with the sink name you copied from PulseAudio Manager.

Edit: applications should remember the last-used sink, so following option 1 (deleting your "volume-restore.table" file) may resolve the problem.

---

### Post by markbuntu on 2008-11-11
module-volume-restore will read the ~/.pulse/volume-restore.table and play your  application in the last used sink at the last used volume when you reopen it. 

You will not be running pulseaudio in system mode unless you have put the line:

system-instance = yes

in your /etc/pulse/daemon.conf file, which apparently bring did somewhere along the line. As he has discovered, module-volume-restore is not available when pulseaudio is running as a system daemon which, by the way, is not reccomended by the pulseaudio developers for general use.

---

### Post by doubleij on 2008-12-24
Hi,
Running 8.04 on Dell XPS m1330 (came pre-installed from Dell). Sound Preferences in Gnome says I use ALSA. Built in sound card works great out of the box (snd_hda_intel) but I'm an audiophile and I'm trying to connect the laptop to my external sound card. I modified the alsabase file as directed at this post. Here's the relevant part of the alsabase file. I added the last two lines.
> 
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd_usb_audio index=0
options snd_hda_intel index=1 


After reboot, I checked my modules and came up with the following:
> 
cat /proc/asound/modules
 1 snd_hda_intel
 2 snd_usb_audio


I installed the Default Sound Card option described above, but I could not see usb_audio as an option to switch to. Instead, I had hda_intel and default. Selecting either option gives me sound from the laptop speakers. I can't select an option to send sound to my usb_audio card!

What should I do next? Thanks in advance...

---

### Post by doubleij on 2008-12-24
Update: My sound preferences were set to "autodetect." I changed everything to Alsa and now I have no trouble getting sound through my USB audio, which is listed as Default.

Next problem: playing through my usb_audio card via virtual box (Hardy Heron host, Windows XP guest). I want to play music through Media Monkey, but whenever I run virtual box my USB audio card disappears from the Default Sound Card preferences dialog. I can only select Intel. My Audio preferences in Virtual Box are set to Alsa. If I try to play a track in Media Monkey, no sound comes through either sound card.

So how do I get my guest Windows system to recognize and use the USB audio sound card? Alternatively, if someone suggests something native that is as intuitive to use as Media Monkey, I'm happy to switch. I've done a lot of looking and testing, and everything is iTunes friendly -- nothing for audiophiles. Tried Amarok, Listen, Rhythmbox. Trying Quod Libet. 

I know this a bit off topic. If anyone can suggest a better place for my comments, I'm happy to post elsewhere.

---

### Post by markbuntu on 2008-12-29
I'm sorry for the late reply, I have been away. So, you figured out your original problem I see, that's great.

The best way to select your usb device is in the pulseaudio volume control. You should set the Default Sound Card option and the Sound preference to pulseaudio.

There is more, much more, on setting up your sound here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I am not very familiar with virtual box but you may want to check the virtual box permissions, they may be set to deny access to sound for guests. If that does not fix your problem I suggest using search to see if there is already a thread on this problem and if that fails, start a new thread since that problem is unrelated to this thread.

---

### Post by doubleij on 2009-01-01
Thanks for the info. I did a lot of looking before I posted here. It looks like some users were able to successfully export sound to an external card using Virtual Box. I couldn't figure out how to do it and couldn't find any how to threads to help. Part of the guest OS recognizes the USB device, but the hardware dialog in the control panel does not include the USB device so the correct driver can't find the USB device either.

I've given up on the virtual box solution for the moment. It works better for my music to have a cheap dedicated desktop anyways. I'll keep an eye out for a fix or how to. 

Thanks again...

---

### Post by ussndmac on 2009-01-01
I have spent a lot of time reading the info presented by markbuntu and have begun to understand the sound architecture.

I understand there is somewhere where you can define what device the hardware buttons on the keyboard control. Currently mine control the first Capture device that shows up in gnome-alsa-mixer. I'd like them to control the master out. I've not been able to find it.

That, and how to control the level of the system sounds with respect to other sound sources are minor issues I'd like to solve.

In a larger view I'd like to determine a sensible configuration for my system.

My ultimate goal is to use the system to record using a Presonous FP-10. That seems to work and when I start up Jack it finds the 10 I/O's of the FP-10. So far so good.

Now I'd like to, for example start Audacious and hear it's out put from my onboard sound hardware. At this point if I send it's output to Jack, I can patch it to the outputs of the FP-10, but the outputs of the alsa or pulseaudio system don't show up in Jack.

If I route the audacious to pulseaudio, I find no way to route pulse audio to Jack.

Just seems to make sense to use the onboard output to monitor rather than sending back down the firewire to the FP-10 for some situations. And it would allow me to minimize switching the monitors/headphones between the headphone jack and the FP-10 outputs. 

Ardour seems to record from the FP-10 just fine (still need to work on XRUNs, but that's another issue).

Any pointers or discussion that might lead me to an "Aha moment" would be greatly appreciated.

Regards,
Mac

---

### Post by markbuntu on 2009-01-01
Look in the **Ubuntu Studio and jack** section of this guide for getting pulsaudio routed to jack.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by ussndmac on 2009-01-01
markbuntu,

Sorry about that I saw your other response to my post after posting this.

I have now read this and have installed the pulseaudio modules for jack and added the script to Jack.

Here's my current observations:

- I see no jack devices shown in pulse device chooser.
- I see nothing about "moving streams" in any of the pulse apps
- Jack will start and see my FP-10, but I have no indication of the script running
- using adacious to test, selecting Jack creates 2 output channels in Jack
- selecting pulse in adacious does nothing and audacious won't play (i.e. hit the play buton in adacious and it does nothing, does not even display the song to be played)
- after changing the timeout in jack it fails to start the server.
- set timeout back to 500 and it starts server and fp-10 appears normal.

Thanks,
Mac

---

### Post by ussndmac on 2009-01-02
Follow up:

I went to a terminal window and entered the script commands.

The response was "module load failed".

I started pacmd and got the same results. I'm guessing this is why I don't see PA sink/sources in Jack.

Is it possible the debian package is not rev compatible with my 0.9.10 package of PA?

---

### Post by markbuntu on 2009-01-02
> **ussndmac said:**
> Follow up:

I went to a terminal window and entered the script commands.

The response was "module load failed".

I started pacmd and got the same results. I'm guessing this is why I don't see PA sink/sources in Jack.

Is it possible the debian package is not rev compatible with my 0.9.10 package of PA?

No, that should not be a problem since Hardy and Intrepid and Debian Lenny are all using pulseaudio 0.9.10 and I have this working in Hardy and Intrepid.

You will see the jack devices in the pa volume control if the modules load properly. This is also where you can move streams by right clicking on them and choosing move stream.

Usually you need to restart audacious after changing its configuration so try that.

It is possible that pulseaudio is crashing when jack control starts. You can try stopping jack in jack control and then starting pulse and then restarting jack and see if the modules load, they should.

---

### Post by ussndmac on 2009-01-02
Since pulse is running before jack is started I have tried the start up sequence one at a time.

Does jack have to present when Pulse is instructed to load the module?

I have tried issuing the load module command in pacmd with and without Jack running, same error.

I expect that when the script runs it gets the same error, though I don't know how to see the output of the script when Jack runs it.

---

### Post by ussndmac on 2009-01-02
PS: PA Volume control shows only the ALSA PCM STAC92xx analog devices

---

### Post by markbuntu on 2009-01-02
Pulseaudio and Jack both need to be running to load the modules or there will be no place for them to hook in.

---

### Post by ussndmac on 2009-01-02
So the pulse jack modules should load if both are running and I issue the load-module command in pacmd.

The load-module fails every time. So it must be failing when it runs from the script in Jack. Does the script run after Jack starts or after the "Start Jack Server" command executes in Jack?

---

### Post by markbuntu on 2009-01-02
The script runs after the jack daemon starts. 

Also, you need to run pactl to load and unload modules dynamically in a running daemon.


[http://linux.die.net/man/1/pactl](http://linux.die.net/man/1/pactl)

---

### Post by ussndmac on 2009-01-02
So here's what I did to try this by hand:

- disable script in Jack
- quit Jack
- start jack
- start jack server
- open terminal window
- enter pactl load-module <pajack module name>

two thing of note happen:

- Jack message window show a Jack connection graph change
- then pactl returns "Module initialization failed"

The above happens each time I enter the pactl command.

---

### Post by markbuntu on 2009-01-02
Well, that seems like some small progress. The module is trying to load and jack is responding to it. Pulseaudio could be crashing when jack control starts up, it shouldn't, but it might. Try this

Start jack control
re-enable the script
make sure pulseaudio is running by opening the pulseaudio volume control
start jack daemon from jack control

Also, check the script for typos. I mistype all the time myself.

---

### Post by ussndmac on 2009-01-02
I agree, something is trying to happen.

I'll check for typos, I've been doin cut-n-paste from both the script and the web page, and I thought I did a cut-n-paste to create the file...

I won't get to attempt this until tomorrow at this point.

Thanks for the help and I'll check in tomorrow.

Mac

---

### Post by ussndmac on 2009-01-03
Ok,

So I checked spelling and there was no issue.

Is it possible that when Jack has started its server and attached to the firewire device with freebob, that the pulse jack module doesn't work?

---

### Post by markbuntu on 2009-01-04
> **ussndmac said:**
> Ok,

So I checked spelling and there was no issue.

Is it possible that when Jack has started its server and attached to the firewire device with freebob, that the pulse jack module doesn't work?

I am not vary familiar with freebob but that is a distinct possibility since this seems to work with everything else. You may want to ask about this on the pulseaudio mailing list or the pulse IRC cahnnel which you can find by going here:

[http://www.pulseaudio.org/](http://www.pulseaudio.org/)

Let me know what you find out.

---

### Post by ussndmac on 2009-01-04
Yes, well, so far I have gone to the pulse IRC channel 3 times, and have gotten no response each time.

I posted to the pulse mail list yesterday, have seen no replies as yet.

---

### Post by dmn01 on 2009-02-27
I have a problem with default addressing for multiple sound cards.  There is a HDA Intel on the motherboard, a HDA Intel on the graphics card, and a USB microphone on the monitor.  From lspci:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]

and from aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


and from /proc/asound/modules

 0 snd_hda_intel
 1 snd_usb_audio
 2 snd_hda_intel

Since two of the cards have the same name, I'm not sure how to assign the default device indices.  The method suggested in this thread's original post requires an entry in /etc/modules.d/alsa-base, but I don't see how to differentiate between the two snd_hda_intel devices.

Any suggestions?

---

### Post by markbuntu on 2009-02-27
There seems to be a way to do it with aliases. I am not positive but I think you would need to alias the names of the cards.
There is more about that here

[http://alsa.opensrc.org/index.php/MultipleCards](http://alsa.opensrc.org/index.php/MultipleCards)

For USB devices

[http://alsa.opensrc.org/index.php/MultipleUSBAudioDevices](http://alsa.opensrc.org/index.php/MultipleUSBAudioDevices)

I have also just added these links to the OP. I had been meaning to so for a while, thanks for the push.

regards,
mark

---

### Post by gvvsss on 2009-03-10
Hi

I have a similar but different situation.

I have ASUS M3N78-VM Motherboard on which NVIDIA HD Audio and VIA VT1708B coexist.

I get sound sometimes, and sometimes I donot get sound, I have to restart twice or thrice for it to work.

But  cat /proc/asound/modules does not show me anything at all. 

Please  help me.

---

### Post by markbuntu on 2009-03-10
> **gvvsss said:**
> Hi

I have a similar but different situation.

I have ASUS M3N78-VM Motherboard on which NVIDIA HD Audio and VIA VT1708B coexist.

I get sound sometimes, and sometimes I donot get sound, I have to restart twice or thrice for it to work.

But  cat /proc/asound/modules does not show me anything at all. 

Please  help me.

Ok, let's try to see what's happening here. Could you please attach the output of the following for when sound is working and when it is not:

lspci

cat /proc/asound/cards

cat /proc/asound/modules

aplay -l

You can also try removing and reinstalling the alsa packages in case something went wrong with the auto-detection causing to not load the modules

```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```


Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

``` 

(3)Don't forget to Reboot

---

### Post by Chemical Imbalance on 2009-03-12
> **gvvsss said:**
> Hi

I have a similar but different situation.

I have ASUS M3N78-VM Motherboard on which NVIDIA HD Audio and VIA VT1708B coexist.

I get sound sometimes, and sometimes I donot get sound, I have to restart twice or thrice for it to work.

But  cat /proc/asound/modules does not show me anything at all. 

Please  help me.

Same problem here--same mobo

I also get nothing after  cat /proc/asound/modules

My sound works in the livecd

---

### Post by markbuntu on 2009-03-12
Are you using a restricted driver for the nvidia?
If so, this seems to be a common problem and there are quite a few threads around here about that. You might want to search them out. One thread mentioned a bios update, another that the nvidia driver disabled the on-board soun in the bios, there are a number of things that seem to go wrong on some particular machines using the nvidia driver.

---

### Post by Chemical Imbalance on 2009-03-12
I upgraded to Jaunty and everything seems to now be working--including sound devices.

---

### Post by robytrevi on 2009-04-20
Hi, I'm new here.
I use Ubuntu Hardy and I'm trying an external sound card (sblive). Surround work fine, but just with one program at a time; I have to stop (not pause), for example, audacious to show a youtube video.
I use ALSA and I like it (I don't like pulseaudio).
This is my .asoundrc file:
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/roby/.asoundrc.asoundconf>
pcm.!default {
      type plug
     slave.pcm "surround51"
   slave.channels 6
 route_policy duplicate
}

pcm.!spdif {
      type plug
      slave.pcm "hw:0,1"
}


pcm.analog {
     type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
      pcm surround51;
      format S32_LE;
}
Can I have sound from different program at the same time?
Thank's

---

### Post by markbuntu on 2009-04-20
You can do that without pulseaudio but you need to remove pulse completely from your system and install libesd-alsa and maybe change a bunch of other stuff around. I do not really know for sure so I cannot recommend doing this. 

Better would be to just setup pulse properly which you can do in about 10 minutes or less

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

For surround sound with pulseaudio

[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

For digital output with pulseaudio

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

---

### Post by robytrevi on 2009-04-21
Thank's,
i try to delete pulse packages, but nothing change, so I reinstalled them. So I wait for Jaunty and maybe I will upgrade my system and I will use pulse... Maybe...
 Bye

---

### Post by johnjoy on 2009-08-14
Sir,
I did the following:

johnjoy@johnjoy-laptop:~$ cat /proc/asound/modules 
 0 snd_hda_intel

Does it mean that I have only one sound device?
Then why does sound work randomly? I have had sound only for 3 times, when I started Ubuntu Jaunty.

Please sir, help me out.

Thanking You,
John Joy

---

### Post by ForgivenByJC on 2009-11-16
Is it possible...?
Current setup
CA0106 (default) 5.1 channel
ALi 5455 2.0 channel

Using the ALi 5455 for MythTV playback on 32" CRT.  Want to use the lfe from CA0106 to make the 32" CRT 2.1 channel.  This would combine the ALi 5455 as it currently is, and add just the lfe channel from the CA0106.  Is it possible to keep my current CA0106 5.1 channel my default and add the lfe to the ALi 5455 to make it 2.1 channel?  I have searched, but have not had any luck locating any information for this on Karmic 9.10.

---

### Post by ForgivenByJC on 2009-12-17
No one has any ideas about combining selective channels from multiple sound cards?  That is surprising.

Now I am running into another problem.  Everytime I reboot my computer, the volume is set to mute on both cards within pulseaudio.  I have to open pavucontrol to unmute the secondary sound card.  Why is this?  Does anyone else experience anything like this?

John

---

### Post by markbuntu on 2009-12-17
> **ForgivenByJC said:**
> No one has any ideas about combining selective channels from multiple sound cards?  That is surprising.

Now I am running into another problem.  Everytime I reboot my computer, the volume is set to mute on both cards within pulseaudio.  I have to open pavucontrol to unmute the secondary sound card.  Why is this?  Does anyone else experience anything like this?

John

You can do that with the pulseaudio module combine. You can read about it at the pulse faq.

A lot of people have reported that problem, I do not have it myself so...

---

### Post by Yudin on 2009-12-26
I have ASUS P5Q-EM motherboard. It have only one sound card

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

I want to translate front speakers via hdmi and rear+center speakers via analog output.
So I write in default.pa

    load-module module-alsa-source device=hw:0,3 sink_name=output0  channel_map=left,right channels=2
    load-module module-alsa-source device=hw:0,0 sink_name=output1 channel_map=center,rear-left,rear-right channels=3
    load-module module-combine sink_name=combined master=output0 slaves=output1 channel_map=left,right,center,rear-left,rear-right channels=5

And it's doesn't work.

pulseaudio command output:
E: module-alsa-source.c: Failed to parse module arguments
E: module.c: Failed to load  module "module-alsa-source" (argument: "device=hw:0,3 sink_name=output0  channel_map=left,right channels=2"): initialization failed.
E: main.c: Module load failed.

Where I mistake?

---

### Post by ForgivenByJC on 2010-02-16
> **markbuntu said:**
> You can do that with the pulseaudio module combine. You can read about it at the pulse faq.

A lot of people have reported that problem, I do not have it myself so...
The PA FAQ suggests using module-oss-mmap (as do you in the OP).  From all that I have read OSS is not being used by default on Ubuntu (9.10 currently).  So, is module-oss-mmap the right thing to use?  Perhaps module-alsa-sink, instead or something else?

If module-oss-mmap is the current thing to use, how do you find which card is which dsp?

I have searched on Google module-combine, channel combine and many others I cannot remember.  I have not been able to find an instance of someone documenting combining specific channels from two different cards, just combining multiple cards.  Is there a decent howto out there somewhere?

---

### Post by hobbyhack on 2010-08-30
Great document!!!  I am running ubuntu 10.04 with 2 sound cards.  One for system stuff and the other for a headset.

I have everything working except for some reason pulseaudio doesn't remember to use my headset sound card for the google talk plugin for firefox or chrome.  Other browser plugins do remember which device to use correctly.

This is a brand new browser plugin for linux although I think it has been available for windows and Mac for a while.  [http://www.google.com/chat/voice/](http://www.google.com/chat/voice/)  .  It shows up as Google Talk Plugin in the Pulse Volume Control panel and I am able to manually change the sound device just fine.

If it were anything else it wouldn't be a big deal but I am trying to use this as an alternate phone in my alternate office.  Which works great except me fumbling to answer the application and change the audio device while someone is listening and waiting for me to be able to say hello.

Any ideas on how to either hard code this one or make pulse audio remember which device to use for this plugin?

Thanks

---

### Post by hobbyhack on 2010-08-30
I posted this in a google forum also since it does seem to be an issue specifically with the plugin.

[http://www.google.com/support/forum/p/chat/thread?tid=10ffe01c3a4779f5&hl=en&fid=10ffe01c3a4779f500048f113b5257c4](http://www.google.com/support/forum/p/chat/thread?tid=10ffe01c3a4779f5&hl=en&fid=10ffe01c3a4779f500048f113b5257c4)

---

### Post by hobbyhack on 2010-08-30
FYI - The fix for the Google plugin not using the last device is to hard code the right device in google settings. 

[https://mail.google.com/mail/?shva=1#settings/chat](https://mail.google.com/mail/?shva=1#settings/chat)

---

### Post by jlbrewer on 2010-10-21
Hi,

I'm on a fairly new install of Meerkat.  I've tried going through this guide (as well as one that had me uninstalling pulseaudio to revert to legacy options - I ended up reversing it) and come to the conclusion that I really need a 'For Dummies" edition.  I'm setting machines up for work after we made the somewhat drastic decision of abandoning Windows - MS sales department managed to personally **** us off.  But my Ubuntu experience has previously been limited to casual experiments and shell admin for my website + Drupal.

We want Skype set up to use seperate sound cards: the onboard Intel/Realtek for front port mic and headset voice, the Asus Xonar PCI-e and the speakers for ringing and everything else (though for private listening to music we might want to be able to switch that occasionaly).  Skype has the ability to do this built in, but with pulseadio, all it sees is the pulseaudio server.  When I removed pulseaduio it sees the individual devices, but there I was able to get the speakers and headphone working correctly and not the microphone.

Pulseaudio obviously has the ability to see what applications are using it, but I can't find the controls, if there are any, to control what it does with them.

Turns out I was trying to follow the outdated guide, maybe I will need another go at it tomorrow...but any input in the meantime would help.

---

### Post by barindra on 2011-01-16
i have a onboard intel hda sound card & a creative ca0106 soundblaster card. the problem is sometimes the sound is good,but sometimes the sound scratchy.in this case if i decrease the volume scratching is quite less. whats is prb? and what to do?

---

### Post by faibistes on 2011-03-15
I have the following sinks:
1) USB soundcard 
2) RTP sink that streams only to 127.0.0.1

I listen to (2) in localhost via vlc, which in turns encodes and compresses the stream and sends it to a Mac that in turns plays it with VLC.
I have created sink (3), which combines (1) and (2) via module-combine.
The problem is the 5-second delay between (1) and (2), that makes (3) useless. Is there any way to add an artificial delay to (1)? ç
Please don't give me the "Stream the raw, uncompressed bits", or "Why would you want to do that?" stuff. If you are really curious on why on  earth I would want to do that, I'll explain it, but please assume that I need to do it that way.

---

### Post by xthatrox on 2011-09-12
Just as an update to others, here is a solution.  If you are running Ubuntu Natty: you can simply install "paprefs" through System-->Administration-->Synaptic Package Manager which will give you the easy to use PulseAudio Preferences GUI.  It let's you combine all sound cards together into a combined output device which you can then select as your default output in order to have sound sent to all devices.  As another benefit, it allows you to share your audio over the network.  This is just a front-end to modify the /etc/pulse/default.pa config file, but it's quite convenient.  

[http://mygeekopinions.blogspot.com/2011/06/paprefs-app-to-configure-pulseaudio.html](http://mygeekopinions.blogspot.com/2011/06/paprefs-app-to-configure-pulseaudio.html)

Hope this saves someone else some time.

---

### Post by hcforde on 2011-09-14
I read the OP and my issue is this. I want to install UBUNTU as a host and then VIRTUALBOX.  In VB I want to have 4 instances of Windows7 64bit or XP 32bit.  Each instance of windows needs to access a seperate sound card or USB sound device and output simultaneously.  Will your instructions work for a senario like this?  It would seem that as long as the host can make the distinction, the guest can be assigned a device, especially a USB device.  Is there anything I am missing before I start this project.

BTW:The application I am using does not allow the assignment of a sound card.

Thanks

---

### Post by allelliott on 2011-09-17
i have an emu 1212m a delta 1010lt and atascamm164uf usb mixer, unbutu only sees the delta card and only 1 analog in and out. the delta card has drivers from a third party developer, but i can't get them to install, i'm about 9 hours old at unbutu, so any newby help is greatly appreciated.

---

### Post by majedaly on 2011-11-13
Hello, and thanks for your extensive how to.
I have a question. can I use one ubuntu box with 2 headsets connected to different sound cards to actually talk to each other? Like an intercom sort of thing?
Appreciate your help. Thanks

---

