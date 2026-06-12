---
title: "No sound on clean 10.04 Lucid Lynx on a Thinkpad T61"
date: 2010-09-26
forum: Multimedia Software
---

### Post by Morten Hattesen on 2010-09-26
I've installed a clean Ubuntu 10.04 Lucid Lynx on my ThinkPad T61, and everything seems to be OK, but I am unable to get any sound output at all (internal speakers and external audio).

No system sounds, no sound from Movie Player, Rythmbox, Sound Recorder.

On my previous Ubuntu 9.04 and 9.10 I had no problems with sound (as far as I can recall).

Any hints to what I should do to try to get sound output?

The output from various sound related commands included below.

```

$ sudo lshw -C sound
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:17 memory:fe220000-fe223fff

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ dmesg|grep hda
[   12.901129] hda_intel: probe_mask set to 0x1 for device 17aa:20ac

$ head -n 1 /proc/asound/card*/codec#*
Codec: Analog Devices AD1984

```

---

### Post by Bill-Gates on 2010-10-13
I found this on the www so i am not sure that the source is trusted and i am far to new to know how to find out how to know a trusted source yet.


it worked for me and here is the site it came from




[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9891770](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9891770)




[FONT=arial]__[/FONT]

[FONT=arial]__[/FONT]
[FONT=arial]_**[IMG]http://www.unixmen.com/images/stories/linuxlogos/ubuntu.gif[/IMG]**_ Here are some of solutions that can help you resolve this issue. Please follow the steps bellow :
[/FONT]
  **Go to System -->Preferences-->Sound** and check  outputvolume if muted or not, if not muted then go further with the  steps bellow , if was muted ( In my case when i installed karmic koala)  then is resolved just you have to unchek mute.
 [IMG]http://i671.photobucket.com/albums/vv77/ZINOVSKY/volum.png[/IMG]
  
 [FONT=arial]First,  make sure  that slmodemd is not running.  with  this  command 

[/FONT]
 **[FONT=arial] pgrep slmodemd[/FONT]** [FONT=arial]if  the  package  installed remove  with  :[/FONT]
 **[FONT=arial]sudo apt-get remove sl-modem-daemon[/FONT]** [FONT=arial]
[/FONT]
 [FONT=arial]restart   your  computer then go  to System>Administration> Softwaresources>[/FONT]
 [FONT=arial]In  the Updates tab active "Unsupported Updates (karmic-backports),  The   reason  from this  is  to  install ALSA modules backports.[/FONT]
 
[LIST]
[*]**[FONT=arial]Now for ubuntu 9.10[SIZE=3] _*karmic koala:*_[/SIZE][/FONT]**
[/LIST]
 **[FONT=arial]sudo apt-get install linux-backports-modules-alsa-karmic-generic[/FONT]**  
 
[LIST]
[*]***For Ubuntu 10.04 [SIZE=3]_Lucid Lynx : _[/SIZE]***
[/LIST]
 **[FONT=arial]sudo apt-get install linux-backports-modules-alsa-lucid-generic[/FONT]** [FONT=arial][/FONT]
 [FONT=arial]After  you installed the backport module above for karmic or Lucid add the PPA  of Ubuntu Development Team Audio and update to download and install  their version of ALSA and PulseAudio packages.  

[/FONT]
 **[FONT=arial]sudo add-apt-repository ppa:ubuntu-audio-dev[/FONT]** **[FONT=arial] sudo apt-get update  [/FONT]** **[FONT=arial] sudo apt-get dist-upgrade[/FONT]** [FONT=arial]
[/FONT]
 [FONT=arial]Now  reboot  and  enjoy.
[/FONT]

---

