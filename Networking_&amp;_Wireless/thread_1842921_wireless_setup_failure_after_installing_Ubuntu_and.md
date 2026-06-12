---
title: "wireless setup failure after installing Ubuntu and lubuntu 11.04"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by michael2009 on 2011-09-12
I have already posted about this issue at the Ubuntu network and wireless forum, in the thread:

'[SOLVED] THE beginners solution for fixing up Broadcom BCM43xx and Wireless Cards'

 and then, wrongly I think, at <https://launchpad.net/ubuntu/+source/gnome-nettool>. 

So first, my apologies for the repetition. I hope this is the right place to get some answers.

 Using the documentation at <[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)>,  I could identify the correct driver and relevant packages for a Compaq  Evo n400c laptop, which is using a LINKSYS PCMCIA wireless card that  requires the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g  Wireless LAN Controller [14e4:4318].


 According to the documentation, I should install the b43 driver. I  followed the installation of both the b43-fwcutter and firmware-b43-installer packages.When this did not work, I tried with the firmware-b43-lpphy-installer  package, but it still did not work, despite repeated removals and  reinstallations. Finally, I used the ndiswrapper for the driver on the  Linksys installation CD as a last resort, and it is now working.
 

The strange thing about all this is that the wireless drivers  installed automatically on the Compaq Evo when completing previous  Ubuntu installations i.e. JJ, 10.04 and 10.10.  I also tried installing  the regular Ubuntu 11.04 on my wife's Compaq Presario v6000 laptop and  was unable to get the built in wireless card to work, yet the previous  installation of Ubuntu 10.10 had no such problems, installing the  drivers automatically. So I reinstalled Ubuntu 10.10 and her wireless is  working fine again, running 10.10. So until I find a workable solution  on 11.04, I am very wary of upgrading from 10.10 on the Compaq Presario.
 

I want to continue running lubuntu 11.04 on the Compaq Evo because it  is faster and smoother than Ubuntu 10.10 for this computer, but I am  not happy about being forced to use ndis wrapper. I have read that ndis wrapper can actually break your system. So I am asking for  assistance in setting up the b43 drivers in preference to the  ndiswrapper that I have currently installed, and that is why I am  reposting here.


 Is this an issue with 11.04 Natty Narwhal only, and does it mean that  the b34 drivers are no longer included in the installation?


 Or am I missing something?

---

### Post by praseodym on 2011-09-12
Hi,

please show the following outputs:

```
iwconfig
lsmod
sudo iwlist scan
rfkill list
dmesg | egrep 'b43|ndis'
```
You can install the attached firmware, just extract it to /lib/firmware.

---

### Post by michael2009 on 2011-09-12
hi and thanks for your reply. Here are the outputs:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


~$ lsmod
Module                  Size  Used by
vesafb                 13449  1 
snd_maestro3           22973  1 
snd_ac97_codec        105614  1 snd_maestro3
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_maestro3,snd_ac97_codec
snd_page_alloc         14073  1 snd_pcm
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ndiswrapper           192828  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
irda                  185091  0 
snd                    55295  9 snd_maestro3,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
pcmcia                 39671  0 
parport_pc             32111  1 
yenta_socket           27230  0 
serio_raw              12990  0 
soundcore              12600  1 snd
i2c_piix4              13095  0 
crc_ccitt              12595  1 irda
pcmcia_rsrc            18292  1 yenta_socket
shpchp                 32345  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
e100                   40108  0 
floppy                 60032  0 

~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


~$ rfkill list

(No results!)


~$ dmesg | egrep 'b43|ndis'
[   25.225370] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   25.326069] usbcore: registered new interface driver ndiswrapper


I am not quite sure what the last one means. I have already completely removed ndiswrapper, and also broadcom-sta-common and firmware-b43-ipphy-installer packages via Package Manager. I have reinstalled the b43-fwcutter and firmware-b43-installer packages with the package  manager, which completed successfully according to the details window. I  then rebooted the computer, and did a search using Additional Drivers,  but still nothing. I still am not getting the firmware offered as a  download either.

Thanks for the Broadcom_Firmware.tar.gz. I shall post again after extracting it.

---

### Post by michael2009 on 2011-09-12
hmm... I downloaded the tar.gz, then tried to extract it to the /lib/firmware folder, but got the following error message:

' Extraction not performed

You don't have the right permissions to extract archives in the folder "file:///lib/firmware" '

I am guessing I need to be root to do this, but I have never figured out how to become root, and I can't find a root account in the Users and Groups list. 

My User account is a custom type and has almost all the administrator permissions, what else do I need to do?

---

### Post by nm_geo on 2011-09-12
~$ lsmod
Module                  Size  Used by
**ndiswrapper           192828  0** 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0

ndiswrapper is still running

To remove it run this in terminal one line at a time.

```
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf 
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```

---

### Post by michael2009 on 2011-09-13
Thanks. Here are the outputs: 

~$ sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk

Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package ndiswrapper-common is not installed, so not removed
Package ndiswrapper-utils-1.9 is not installed, so not removed
The following packages will be REMOVED
  ndisgtk*
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


~$ sudo rm /etc/modprobe.d/ndiswrapper.conf
~$ sudo rm -r /etc/ndiswrapper/*
~$ sudo depmod -a

(no outputs)

---

### Post by michael2009 on 2011-09-13
Success! Hooray! 

After running the scripts given by nm_geo in the post above, I rebooted the computer. The processor was busy for a while, then, when I clicked the network status monitor icon on the taskbar, I had  new option for wlan in addition to etho on the drop-down list. Selecting wlan, and unplugging the ethernet cable, everything is working fine now with the wireless connection between 91-94%.

Thank you nm_geo :)

---

### Post by michael2009 on 2011-09-13
Thanks also to praseodym.

---

### Post by michael2009 on 2011-09-16
Having solved the wireless problem on my laptop running lubuntu 11.04, I am turning my attention to my wife's laptop, currently running Ubuntu 10.10 Maverick Meerkat. I want to upgrade to 11.04, but I am concerned that the wireless network, which set itself up automatically with Ubuntu 10.10, may be adversely affected by the upgrade. 

 The command line: 

lspci -vvnn | grep 14e4

tells me that the Network Controller is Broadcom Corporation BCM4311 802.11b/g WLAN.

Is anyone out there capable of reassuring me that all the current settings and  driver capabilities will be preserved when upgraded? I am planning to do  the internet upgrade that is currently being offered by Update Manager  at regular intervals.

Another concern I have with running 11.04 on a Compaq Presario V6000  laptop, is whether I am likely to experience any loss of speed compared  to running 10.10, which is currently very fast and smooth,  and looks great, with Display  Preferences set to Medium. Without referring to the specs, I recall that the processor is a Pentium  Dual Core (or Duo Core), T2080 1.73GHz, and the Memory is 992MB. HDD is 120GB ATA Toshiba MK1246GSX.

---

### Post by wildmanne39 on 2011-09-16
Hi, you will have to reinstall your drivers, but the sta driver in additional drivers do not work in 11.04, you will need to install this.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
``` 
Thank you

---

### Post by michael2009 on 2011-09-17
Thanks for your reply wildmanne39. You wrote that the sta drivers in additional drivers do not work in 11.04. If that is the case, then why are they  there in the first place? Are they downloaded automatically in the upgrade to 11.04? If so, it means that all the sta packages, and any other wireless driver packages like ndiswrapper, will have to be removed, and purged from the system, possibly involving the same awkward process that I have just been through to install the 
[FONT=monospace]b43-fwcutter & firmware-b43-installer[/FONT] packages on my other laptop. What a pain.

---

### Post by wildmanne39 on 2011-09-17
Hi, the sta driver is there but is not installed unless you activate it in additional drivers. So it does not need to be removed unless it was activated.

My understanding there is a work around to get the sta driver to work but I have never tried it, so the easiest is to install the b43, if you want the sta driver you can research it and try to figure it out but in my opinion when the other driver does a great job I see no reason to go looking for how to make the sta driver work since it is suppose to work by just activating it.

They do work for some cards just not very many because of a regression in other words there is a bug in the 11.04 kernel, I do not know if it will be fixed in 11.10 or not.
Thank you

---

### Post by michael2009 on 2011-09-17
OK, thanks for the information. Such a shame that 11.04 looks so good, but doesn't install the wireless drivers as effortlessly as 10.10 on the Compaq Presario. 

I have noticed a lot of posts here about wireless issues with 11.04, many similar to mine, and affecting a range of different computer brands and hardware. Yet the official documentation only offers the ndiswrapper solution, which is reportedly unstable, and inferior to the very common broadcom drivers. Do the 11.04 developers know about these problems? Can they make sure they fix it so it is at least as efficient as 10.10? Or will we have to wait for the next version to see an improvement?

---

### Post by wildmanne39 on 2011-09-17
Hi, I do not know I am just a volunteer here that tries to help people fix problems, I do not have all the answers, you can help by reporting bugs to launchpad so they can be fixed, the more people involved the better.
Thank you

---

### Post by nm_geo on 2011-09-17
> **michael2009 said:**
> OK, thanks for the information. Such a shame that 11.04 looks so good, but doesn't install the wireless drivers as effortlessly as 10.10 on the Compaq Presario. 

I have noticed a lot of posts here about wireless issues with 11.04, many similar to mine, and affecting a range of different computer brands and hardware. Yet the official documentation only offers the ndiswrapper solution, which is reportedly unstable, and inferior to the very common broadcom drivers. Do the 11.04 developers know about these problems? Can they make sure they fix it so it is at least as efficient as 10.10? Or will we have to wait for the next version to see an improvement?

michael2009,

It is really easy to get Natty running on the bcm4311 chip if you want to try it. I run 10.04, 11.04 and test 11.10 on that same chipset 
I have all of them running with the b43-fwcutter and firmware-b43-installer. Just avoid the additional driver recommendation go straight to Synaptic and install those two.

Or in terminal.

```
sudo apt-get install b43-fwcutter firmware-b43-installer

```reboot with ethernet cable NOT connected and you are golden.. Mine are all very stable too.

---

### Post by michael2009 on 2011-09-18
OK, thanks for your encouragement  nm_geo.  I shall get around to it probably sometime in the next few weeks. What about the next release, do you know when a stable version is likely to be available?

---

### Post by wildmanne39 on 2011-09-18
Hi, my understanding was you got it to work already using that method since it was previously posted in this thread, if I was incorrect I am sorry for that I thought you was just letting of steam from going through the process.
Thank you

---

### Post by tjeremiah on 2012-01-27
> **praseodym said:**
> Hi,

please show the following outputs:

```
iwconfig
lsmod
sudo iwlist scan
rfkill list
dmesg | egrep 'b43|ndis'
```
You can install the attached firmware, just extract it to /lib/firmware.

this firmware is a life saver. Literally after extracting, my wireless worked. No headaches, no searching for the right dependencies all day. It just worked :D

---

