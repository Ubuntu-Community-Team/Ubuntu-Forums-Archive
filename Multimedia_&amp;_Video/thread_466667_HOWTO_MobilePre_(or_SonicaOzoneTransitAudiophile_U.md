---
title: "HOWTO: MobilePre (or Sonica/Ozone/Transit/Audiophile USB) with firmware loader"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by paulg on 2007-06-07
*****See the new [thread]("http://ubuntuforums.org/showthread.php?p=5300948") for insrtuctions in using madfuload in Hardy. The howto below applies to Fiesty and Gutsy only******

First of all, the newer MobilePre's apparently work out of a box in which case you will not need to do anything. I have a MobilePre circa. 2003 which requires the firmware loader to work. If you follow these steps you should be able to  replace MobilePre with Sonica/Ozone/Transit/Audiophile USB if you have one of the other devices. The older devices require firmware and loader available here:
[http://usb-midi-fw.sourceforge.net/]("http://http://usb-midi-fw.sourceforge.net/")

This had been working for me for sometime and seemed to be set-off by Dapper (?) to some degree and now definitely would not work with Fiesty. I read on a post about a person who could boot into Windows, let Windows load the firmware and then boot into Linux without powering down and have it work. That's when I realized I had the same issue. From what I can tell, an upgrade to udev has rendered the udev rule file the installer copies over useless. I found [this solution]("http://sourceforge.net/tracker/index.php?func=detail&aid=1622573&group_id=87777&atid=584353") in the bug-tracker on sourceforge and it fixed my problem. Hot-plugging of my MobilePre works again! Here's how I did it.

[LIST=1]
[*]Install the [firware]("http://http://usb-midi-fw.sourceforge.net/") from the link above. Install directions are given on the site and view the README in the tarball for more help on compiling.
[*]The installer will create a udev rule in /etc/udev/rules.d/42-madfuload.rules
You will need to open the file with your favourite editor. I suggest the following command in terminal:
```
~$ sudo nano /etc/udev/rules.d/42-madfuload.rules
```
[*]Basically all of the lines are incorrect so you may as well comment all of them with a '#'. You could delete them but you may want to keep the one for the MobilePre so you can copy the product ID and firmware.
[*]Find the entry for MobilePre (or Sonica/Ozone/Transit/Audiophile) create a new line and paste the following
```
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2804", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma004103.bin -D $env{DEVNAME}"
```
[*]Replace the product ID and the firmware (file name ending with '.bin') in the above line with your device ID. Summary is below but you should be able to verify this in the original udev rule file.

[LIST]
[*]MobilePre
Product ID == 2804
firmware == ma004103.bin

[*]Sonica
Product ID == 2805
firmware == ma005101.bin

[*]Ozone
Product ID == 2808
firmware == ma008100.bin

[*]Transit
Product ID == 2806
firmware == ma006100.bin

[*]Audiophile USB
Product ID == 2803
firmware == ma003101.bin[/list]
[*]Just need to restart the udev listening engine:
```
 $ sudo /etc/init.d/udev restart
```
[/list]

If you have questions post below and I'll do my best to respond.

UPDATE 2007/10/20: Per sonium's post below, I can confirm that this works in Gutsy. Updating from Feisty did not break it.

~pAul.

---

### Post by Chris Parsons on 2007-06-28
I have tried to install the new firmware off of the given link and recieve the following error message.

> checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


Yes, i'm a noob...

thanks for your time

---

### Post by paulg on 2007-06-28
Try:

```
~/$ sudo aptitude install build-essential
```

That should get you going. Looks like you're missing the 'C' compiler and probably some other things. The 'build essential' package should install everything you need to use make successfully. Let me know how it goes.

---

### Post by paletti on 2007-08-08
thanks this worked fine for me , i can see the ozone now in the device manager...

now it's time to get lost in ubuntu studio :)

---

### Post by sonium on 2007-10-14
Thank you, I was looking for a year for something like this. Also works on 7.10 x64. You made my day :)

---

### Post by silicium on 2007-10-23
Hi,
how do you check if the firmware is loaded when plugging the MobilePre, and where is the device manager ? I'm new to linux (but not to other unix). I installed Ubuntu studio 7.10 on an used server (Asus CUR-DLS, 1 GB ECC, dual P3/933, 18 GB U160), then followed this HOWTO. Booting install CD required noapic nolapic options. After installing, I tried to look at the status of my USB devices, but lsusb hangs and does not respond to kill -9. :confused:

---

### Post by paulg on 2007-10-23
'lsusb' would tell you if the firmware had loaded. You can also check with alsa using the command 'asoundconf list' which will list all valid [Alsa] soundcards in the system. If it has installed it will show up here. 

OK, I had to look up what those boot options were and I'm still not sure I understand but I'll just throw some things to try anyway (in no particular order)...

You needed these boot parameters to install but have you tried disabling the options and booting normal since you've installed them? From my basic understanding isn't APIC necessary for PCI/USB control in a SMP system? If that's correct then you are disabling USB at boot so of course calling the bus with lsusb wouldn't work....

Could you try acpi=off and lapci=off as alternatives? (this goes against what I suggest above but yeah, really just throwing out everything I'm finding)

I also found a couple interesting answers [here]("http://ubuntuforums.org/showthread.php?t=406893&highlight=noapic+USB") and [here]("http://lists.debian.org/debian-amd64/2007/07/msg00210.html").

Try installing one of the other kernels. Perhaps -386 instead of generic. Or boot into an alternative kernel and purge the generic kernel and then reinstall it (sudo aptitude purge linux-image-generic).

Are you running a kernel for SMP systems? I *think* the current generic kernels support SMP but I'm not sure. I ran a dual celeron system way back and had to roll my own kernel to enable SMP support.

Could you try a 2.4 kernel build? (I don't know if they are still loading pre-built 2.4 kernels into the repository)

Do you have the latest BIOS for the board installed? (note there's always some risk in damaging your equipment when updating the motherboard BIOS make sure you read the manufacturers directions)

[http://support.asus.com/download/download.aspx?modelname=CUR-DLS&SLanguage=en-us]("http://support.asus.com/download/download.aspx?modelname=CUR-DLS&SLanguage=en-us")

That's all I have right now. If I think of anything else I'll post it. By all means post back if something works. I'd personally start with the easy stuff (kernel boot parameter changes, BIOS) and then move onto the more tricky things like compiling a kernel.

---

### Post by silicium on 2007-10-24
Thanks for fast support. Latest BIOS has been flashed. Unlike install CD that required option noapic, grub's default menu.lst boots without any extra option. But lsusb still hangs even before plugging any USB device. The kernel is SMP (see attached dmesg). I found that the quad ethernet card shares IRQ 30 with USB ohci_hcd that complains (Unlink after no-irq...). The USB OHCD has PCI IRQ9 under Win2K while PnP ACPI subsystem has ISA IRQ9 and NICs have 20/21/29/31/30. So Linux disables the ISA IRQ and this prevents it from beeing used from the PCI bus...

---

### Post by tktabla on 2007-10-24
Hi all
I am trying to use MobilePre on a brand new HP box with the latest Debian distribution. Since I have Kernel 2.6 alsa is already included and since I got my MobilePre 1 year ago (silver and black model of course)  it should work out of the box but it does not.
I followed the steps in the first post (BTW great info, thanks!) but it still does not work.

/proc/asound cards shows the following:

```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff8000 irq 193
 1 [MobilePre      ]: USB-Audio - MobilePre
                      M Audio MobilePre at usb-0000:00:1d.1-1, full speed

```
so the card is there but if I start Audacity for example, nothing is shown in the two "Device:" drop-down menues at Preferences>Audio I/O.

Since I am not a  Linux guru I am kind of lost. Any ideas?

Many thanks in advance.

Gian

---

### Post by silicium on 2007-10-24
Good news ! The IRQ mapping was corrected with boot option acpi=force. 'lsusb' can see my USB devices and I will proceed with firmware downloader installation...:KS

---

### Post by paulg on 2007-10-24
> **silicium said:**
> Good news ! The IRQ mapping was corrected with boot option acpi=force. 'lsusb' can see my USB devices and I will proceed with firmware downloader installation...:KS

Nice! That is good news. I hope your next post is one announcing success.

---

### Post by paulg on 2007-10-24
> **tktabla said:**
> Hi all
/proc/asound cards shows the following:

Gian

Hey Gian, what does this command return in terminal?
```
~/$ asoundconf list
```

---

### Post by silicium on 2007-10-24
> **paulg said:**
> I hope your next post is one announcing success.
You guessed it ! asoundconf list ==> MobilePre and M2x2 . But other bleak issues are coming... Totem hung after a few minutes while playing a mp3 track :-({|=

---

### Post by tktabla on 2007-10-25
Hi all,
a read on a spanish page that a guy is using Mobile Pre USB just with the generic USB audio driver. Looks like it works just fine. My question is: how to use that generic driver instead of the one I am trying to use now? Not sure which are the required steps. The device manager shows the Mobile Pre card but there's no way to assign any driver from there.

Thanks

Gian

---

### Post by silicium on 2007-10-26
>just with the generic USB audio driver
It depends on the MobilePre revision. As said on the first post here, the new ones have a firmware in their ROM with generic USB audio compliance, while older ones need a custom loader and firmware to be downloaded from PC to their RAM. If you look at 'lsusb' output for an old one, you will see two different IDs before and after loading the two *.ihx files with fxload. If you want to see what happens when you plug an USB device, you can stop udev service and run udevd in foreground with --verbose option. The old MobilePre's are silver and blue while the new ones have black instead of blue. Or your example is using a better customized distro with preinstalled firmware loader.

---

### Post by tktabla on 2007-10-26
I finally decided to install Ubuntu and everything worked out of the box just fine.

Cheers
Gian

---

### Post by Porsenna81 on 2008-01-06
Hi everyone.
I'm trying to install m-audio mobile pre usb  (firmware v1.03) on a sony vaio fe48e with Ubuntu 7.10.
It didn't work "out of the box" so I tried with the firmware loader but it still doesn't work.
I can't find it in Preferences->Audio.

This is my output of lsusb:

Bus 005 Device 004: ID 05ca:1836 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0763:200f Midiman 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

This is my 42-madfuload.rules:

# madfuload.rules - udev rules for loading firmware into M-Audio DFU devices

# DEVPATH=="/*.0" selects interface 0 only
# (some udev versions don't work with SYSFS{bInterfaceNumber})

# Audiophile
#ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2803/*", RUN+="/usr/local/sbin/madfuload -l -n -f /usr/local/share/usb/maudio/ma003101.bin"
# MobilePre
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="200f", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma004103.bin -D $env{DEVNAME}"
#ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2804/*", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma004103.bin"
# Sonica
#ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2805/*", RUN+="/usr/local/sbin/madfuload -l -n -f /usr/local/share/usb/maudio/ma005101.bin"
# Transit
#ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2806/*", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma006100.bin"
# Ozone
#ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2808/*", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma008100.bin"

# vim: ft=conf

This is my output of asoundconf list:

Names of available sound cards:
Intel

This is my  /proc/asound/cards

0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd2300000 irq 23


Someone can help?

---

### Post by paulg on 2008-01-07
Porsenna81, 

The 'lsusb' command looks like it's returning the right thing but your UDEV line is entered incorrectly. Replace SYSFS{idProduct}=="200f" with SYSFS{idProduct}=="2804".
Maybe also try install 'alsa-utils'?

```
sudo aptitude install alsa-utils
```

I think you may also need the snd_usb_audio module. 

```
sudo modprobe usbcore
```

What do you get when you put in the following command?

```
asoundconf list
```

Let me know how it goes.

---

### Post by Porsenna81 on 2008-01-08
Thank you for your answer.
I replaced the correct idproduct in 42-madfuload.rules, but it didn't change anything.

I've got alsa-utils (however I tried to install them again, but they were up to date).

This is my output of asoundconf list:
```
Names of available sound cards:
Intel
```
That is it doesn't see my usb M-audio.

I think it's a problem of the module snd-usb-audio.

This is my output of modprobe snd-usb-audio:
```
WARNING: Error inserting snd_usb_lib (/lib/modules/2.6.22-14-generic/kernel/sound/usb/snd-usb-lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.22-14-generic/kernel/sound/usb/snd-usb-audio.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

dmesg says:

```
blabla...

[10644.392000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_receive
[10644.392000] snd_usb_lib: Unknown symbol snd_rawmidi_receive
[10644.392000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_empty
[10644.392000] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_empty
[10644.392000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit
[10644.392000] snd_usb_lib: Unknown symbol snd_rawmidi_transmit
[10644.392000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_ack
[10644.392000] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_ack
[10644.392000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_peek
[10644.392000] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_peek
[10644.392000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_new
[10644.392000] snd_usb_lib: Unknown symbol snd_rawmidi_new
[10644.392000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_set_ops
[10644.392000] snd_usb_lib: Unknown symbol snd_rawmidi_set_ops
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_ctl_add
[10644.404000] snd_usb_audio: Unknown symbol snd_ctl_add
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_pcm_new
[10644.404000] snd_usb_audio: Unknown symbol snd_pcm_new
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_card_register
[10644.404000] snd_usb_audio: Unknown symbol snd_card_register
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_card_free
[10644.404000] snd_usb_audio: Unknown symbol snd_card_free
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_card_proc_new
[10644.404000] snd_usb_audio: Unknown symbol snd_card_proc_new
[10644.404000] snd_usb_audio: Unknown symbol snd_usb_create_midi_interface
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_pcm_stop
[10644.404000] snd_usb_audio: Unknown symbol snd_pcm_stop
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_pcm_hw_constraint_minmax
[10644.404000] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_minmax
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_ctl_find_id
[10644.404000] snd_usb_audio: Unknown symbol snd_ctl_find_id
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_ctl_new1
[10644.404000] snd_usb_audio: Unknown symbol snd_ctl_new1
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_component_add
[10644.404000] snd_usb_audio: Unknown symbol snd_component_add
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_pcm_hw_rule_add
[10644.404000] snd_usb_audio: Unknown symbol snd_pcm_hw_rule_add
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_card_new
[10644.404000] snd_usb_audio: Unknown symbol snd_card_new
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_pcm_lib_ioctl
[10644.404000] snd_usb_audio: Unknown symbol snd_pcm_lib_ioctl
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_hwdep_new
[10644.404000] snd_usb_audio: Unknown symbol snd_hwdep_new
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_pcm_new_stream
[10644.404000] snd_usb_audio: Unknown symbol snd_pcm_new_stream
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_card_free_when_closed
[10644.404000] snd_usb_audio: Unknown symbol snd_card_free_when_closed
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_ctl_notify
[10644.404000] snd_usb_audio: Unknown symbol snd_ctl_notify
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_pcm_set_ops
[10644.404000] snd_usb_audio: Unknown symbol snd_pcm_set_ops
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_pcm_hw_constraint_list
[10644.404000] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_list
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_device_new
[10644.404000] snd_usb_audio: Unknown symbol snd_device_new
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_card_disconnect
[10644.404000] snd_usb_audio: Unknown symbol snd_card_disconnect
[10644.404000] snd_usb_audio: disagrees about version of symbol snd_pcm_period_elapsed
[10644.404000] snd_usb_audio: Unknown symbol snd_pcm_period_elapsed
[10644.404000] snd_usb_audio: Unknown symbol snd_usbmidi_disconnect
[10685.052000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_receive
[10685.052000] snd_usb_lib: Unknown symbol snd_rawmidi_receive
[10685.052000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_empty
[10685.052000] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_empty
[10685.052000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit
[10685.052000] snd_usb_lib: Unknown symbol snd_rawmidi_transmit
[10685.052000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_ack
[10685.052000] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_ack
[10685.052000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_peek
[10685.052000] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_peek
[10685.052000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_new
[10685.052000] snd_usb_lib: Unknown symbol snd_rawmidi_new
[10685.052000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_set_ops
[10685.052000] snd_usb_lib: Unknown symbol snd_rawmidi_set_ops
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_ctl_add
[10685.060000] snd_usb_audio: Unknown symbol snd_ctl_add
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_pcm_new
[10685.060000] snd_usb_audio: Unknown symbol snd_pcm_new
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_card_register
[10685.060000] snd_usb_audio: Unknown symbol snd_card_register
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_card_free
[10685.060000] snd_usb_audio: Unknown symbol snd_card_free
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_card_proc_new
[10685.060000] snd_usb_audio: Unknown symbol snd_card_proc_new
[10685.060000] snd_usb_audio: Unknown symbol snd_usb_create_midi_interface
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_pcm_stop
[10685.060000] snd_usb_audio: Unknown symbol snd_pcm_stop
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_pcm_hw_constraint_minmax
[10685.060000] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_minmax
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_ctl_find_id
[10685.060000] snd_usb_audio: Unknown symbol snd_ctl_find_id
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_ctl_new1
[10685.060000] snd_usb_audio: Unknown symbol snd_ctl_new1
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_component_add
[10685.060000] snd_usb_audio: Unknown symbol snd_component_add
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_pcm_hw_rule_add
[10685.060000] snd_usb_audio: Unknown symbol snd_pcm_hw_rule_add
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_card_new
[10685.060000] snd_usb_audio: Unknown symbol snd_card_new
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_pcm_lib_ioctl
[10685.060000] snd_usb_audio: Unknown symbol snd_pcm_lib_ioctl
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_hwdep_new
[10685.060000] snd_usb_audio: Unknown symbol snd_hwdep_new
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_pcm_new_stream
[10685.060000] snd_usb_audio: Unknown symbol snd_pcm_new_stream
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_card_free_when_closed
[10685.060000] snd_usb_audio: Unknown symbol snd_card_free_when_closed
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_ctl_notify
[10685.060000] snd_usb_audio: Unknown symbol snd_ctl_notify
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_pcm_set_ops
[10685.060000] snd_usb_audio: Unknown symbol snd_pcm_set_ops
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_pcm_hw_constraint_list
[10685.060000] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_list
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_device_new
[10685.060000] snd_usb_audio: Unknown symbol snd_device_new
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_card_disconnect
[10685.060000] snd_usb_audio: Unknown symbol snd_card_disconnect
[10685.060000] snd_usb_audio: disagrees about version of symbol snd_pcm_period_elapsed
[10685.060000] snd_usb_audio: Unknown symbol snd_pcm_period_elapsed
[10685.060000] snd_usb_audio: Unknown symbol snd_usbmidi_disconnect
[11061.268000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_receive
[11061.268000] snd_usb_lib: Unknown symbol snd_rawmidi_receive
[11061.268000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_empty
[11061.268000] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_empty
[11061.268000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit
[11061.268000] snd_usb_lib: Unknown symbol snd_rawmidi_transmit
[11061.268000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_ack
[11061.268000] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_ack
[11061.268000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_transmit_peek
[11061.268000] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_peek
[11061.268000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_new
[11061.268000] snd_usb_lib: Unknown symbol snd_rawmidi_new
[11061.268000] snd_usb_lib: disagrees about version of symbol snd_rawmidi_set_ops
[11061.268000] snd_usb_lib: Unknown symbol snd_rawmidi_set_ops
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_ctl_add
[11061.272000] snd_usb_audio: Unknown symbol snd_ctl_add
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_pcm_new
[11061.272000] snd_usb_audio: Unknown symbol snd_pcm_new
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_card_register
[11061.272000] snd_usb_audio: Unknown symbol snd_card_register
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_card_free
[11061.272000] snd_usb_audio: Unknown symbol snd_card_free
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_card_proc_new
[11061.272000] snd_usb_audio: Unknown symbol snd_card_proc_new
[11061.272000] snd_usb_audio: Unknown symbol snd_usb_create_midi_interface
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_pcm_stop
[11061.272000] snd_usb_audio: Unknown symbol snd_pcm_stop
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_pcm_hw_constraint_minmax
[11061.272000] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_minmax
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_ctl_find_id
[11061.272000] snd_usb_audio: Unknown symbol snd_ctl_find_id
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_ctl_new1
[11061.272000] snd_usb_audio: Unknown symbol snd_ctl_new1
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_component_add
[11061.272000] snd_usb_audio: Unknown symbol snd_component_add
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_pcm_hw_rule_add
[11061.272000] snd_usb_audio: Unknown symbol snd_pcm_hw_rule_add
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_card_new
[11061.272000] snd_usb_audio: Unknown symbol snd_card_new
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_pcm_lib_ioctl
[11061.272000] snd_usb_audio: Unknown symbol snd_pcm_lib_ioctl
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_hwdep_new
[11061.272000] snd_usb_audio: Unknown symbol snd_hwdep_new
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_pcm_new_stream
[11061.272000] snd_usb_audio: Unknown symbol snd_pcm_new_stream
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_card_free_when_closed
[11061.272000] snd_usb_audio: Unknown symbol snd_card_free_when_closed
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_ctl_notify
[11061.272000] snd_usb_audio: Unknown symbol snd_ctl_notify
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_pcm_set_ops
[11061.272000] snd_usb_audio: Unknown symbol snd_pcm_set_ops
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_pcm_hw_constraint_list
[11061.272000] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_list
[11061.272000] snd_usb_audio: disagrees about version of symbol snd_device_new
[11061.272000] snd_usb_audio: Unknown symbol snd_device_new
[11061.276000] snd_usb_audio: disagrees about version of symbol snd_card_disconnect
[11061.276000] snd_usb_audio: Unknown symbol snd_card_disconnect
[11061.276000] snd_usb_audio: disagrees about version of symbol snd_pcm_period_elapsed
[11061.276000] snd_usb_audio: Unknown symbol snd_pcm_period_elapsed
[11061.276000] snd_usb_audio: Unknown symbol snd_usbmidi_disconnect
```

My /etc/modprobe.d/alsa-base is:

```
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
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

Could it be a conflict with oss and its modules for usb (i read something about that in snd-usb-audio documentation)?
I tried to blacklist it adding

blacklist audio 

in /etc/modprobe.d/blacklist-oss, but I didn't obtained any result.

---

### Post by Porsenna81 on 2008-01-08
It was a problem with module snd-usb-audio.
I recompiled alsa drivers into the kernel following this: [http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio]("http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio")

Now I can see USB Audio in preferences->audio, I can hear sound throught outputs of my M-audio mobile pre usb, and register my guitar throught its inputs. :lolflag:

---

### Post by paulg on 2008-01-08
Glad to hear you got that part working at least. Based on your initial post I think this may have been your problem all along and I'm not sure you needed the madfuload firmware loader at all (it won't hurt anything just being there).

Try using alsamixer in a terminal. Unmute everything and turn all the volumes up until you find the right one. Also, don't forget to adjust the gain setting on the built-in preamp with one of the knobs on the front. Of course, green on the indicator LED means there's a [good] signal, red LED means the signal is clipping [bad].

---

### Post by paulg on 2008-01-08
Oh, also don't forget to select the MobilePre as the default card. When I first installed the card I found the selector in Gnome buggy and didn't always switch over properly (this was way back in 5.something). It may work fine now but I still always use asoundconf (even though the Gnome configurator is just a front end for these commands).

Also, the mobilepre has hardware monitoring so depending on what software you're using you may want to mute/unmute this option. You can mute it if you need to send to software first (like if you're using Jack Rack for guitar effects). It's one of the volume controls in the alsamixer. The hardware monitoring is convenient as you don't need to open software just to play.

```
~/ $ asoundconf set-default-card MobilePre
~/$ asoundconf set-default-card Intel
```

If I've remembered the command correctly those two commands will switch your working soundcards. If you have a program open you'll need to restart it after you change cards (unless you want to continue using the card) . You can get a list of all the options with asoundconf --help. And asoundconf list will of course give you the correct identification for your cards.

---

### Post by Porsenna81 on 2008-01-08
I found how to to set volumes on alsamixer by switching default sound card or by calling the mixer with options.

Thank you very much for your help. I'm new in using linux but I get each day more satisfied.

---

### Post by Porsenna81 on 2008-01-09
I just have something to add abount multiple sound cards.
I hope it can be helpful for someone.

Since M-Audio mobile pre usb is seldom used as main (or the only) sound card it have to work together with the internal one.
However I need it to do that.

The tutorial I linked above from alsa-project doesn't explain how to do that: it just says how to get usb-audio working (it's part of the documentation of snd-usb-audio module).

To make the two sound cards work together I had to compile the module configuring it for both kinds of sound card I have: intel CH7 and M-audio mobile pre usb.

To do this just configure with:
```
./configure --with-cards=hda-intel,usb-audio --with-oss=yes --with-sequencer=yes
```

(Obvioulsy if I had another sound card instead of the intel I had to change "hda-intel" with the correct module for my sound card.)

---

### Post by Bapman on 2008-04-16
Hi,

 I am thinking of buying a Transit usb card but I would like to know if it still works flawlessly with firmware uploader.
 I will also really need the optical output to work. Does it work for you ?

If not I will try a Terratec Aureon MkII but the quality is not as good I think !

Thanks ;)

---

### Post by paulg on 2008-04-16
I can't say for certain this is the case for the Transit, but for newer versions of the MobilePre the firmware loader is not required. It "just works."

My MobilePre doesn't have an optical/TOSLINK out so I could not say for certain. Anyone else out there monitoring the thread with the answer to Bapman's question?

---

### Post by pyutaros on 2008-05-19
Hi everyone.  Great information in this thread.  Unfortunately, I still can't seem to get my MobilePre USB working under Hardy Heron.  I'll list what I tried, followed by some output to show what's on my system.

[LIST=1]
[*]I installed the firmware as directed in this comment: [http://ubuntuforums.org/showpost.php?p=2796830&postcount=1](http://ubuntuforums.org/showpost.php?p=2796830&postcount=1).  (PaulG)  I also had to end up installing the C compiler.
[*]I tried everything discussed here: [http://ubuntuforums.org/showpost.php?p=4089772&postcount=18](http://ubuntuforums.org/showpost.php?p=4089772&postcount=18).  (PaulG)
[*]I tried what Porsenna81 mentions here: [http://ubuntuforums.org/showpost.php?p=4096393&postcount=20](http://ubuntuforums.org/showpost.php?p=4096393&postcount=20).
[/LIST]

I'm kind of at a loss at this point.  I've already gone way beyond my frame of knowledge by following all these directions, which is good.  My problem is specifically that USB audio does not show up in preferences >> sound.  Here are some outputs:

lsusb
```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0763:2804 Midiman 
Bus 001 Device 001: ID 0000:0000
```

42-madfuload.rules
```
# madfuload.rules - udev rules for loading firmware into M-Audio DFU devices

# DEVPATH=="/*.0" selects interface 0 only
# (some udev versions don't work with SYSFS{bInterfaceNumber})

# Audiophile
#ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2803/*", RUN+="/usr/local/sbin/madfuload -l -n -f /usr/local/share/usb/maudio/ma003101.bin"
# MobilePre
#Original syntax from firmware - ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2804/*", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma004103.bin"
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2804", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma004103.bin -D $env{DEVNAME}"
# Sonica
#ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2805/*", RUN+="/usr/local/sbin/madfuload -l -n -f /usr/local/share/usb/maudio/ma005101.bin"
# Transit
#ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2806/*", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma006100.bin"
# Ozone
#ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2808/*", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma008100.bin"

# vim: ft=conf
```

asoundconf list
```
Names of available sound cards:
ICH5
```

/proc/asound/cards is blank (maybe this is my problem?)

alsa-base
```
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
```

I obviously have the BLUE and gray model.  Thanks in advance to anyone who can help with this.

---

### Post by digitalcat on 2008-05-19
I'm having the same problem with Hardy and M-audio sonica. Had tried to replace the kernel with an older version and that worked out fine. But I'm wondering if there is another way around?

---

### Post by pyutaros on 2008-05-21
Well, at least I now know that my card can work.  I ended up creating another partition on my hard drive and installed Gutsy 7.10 on it.  I followed PaulG's first set of instructions, and voila!  I now have USB Audio under Preferences >> Sound.  
The only issue I'm having now is during the sound capture test.  I get an error: ```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```  I remember getting this error on another box when trying to fiddle around with Skype.  The solutions had something to do with GStreamer and Esound.  Of course, I haven't even done updates yet on this clean install, so it may fix itself when all of that is done.
It strikes me that having two different versions installed at all times is a great way to help the community test for new versions and updates.  I'll likely boot into my Hardy install later and file a bug report for the Mobile Pre issue.  The question is, who do I file it with?  Is this a launchpad issue, or do I want to go to ALSA and file the report.  I'll post an update when I find the solution to the Gutsy sound capture error.

---

### Post by perottol on 2008-05-23
A lot of good reading here. I seem to have my M-audio Mobile Pre working on Ubuntu 8.04. Well, at least in Preferences->Audio. When plugged in I get "USB Audio" as an option, and with this selected I hear sound in the card when I press the test button.

My problem now is that Amarok still uses the internal sound card. I have tried different settings in the Xine-penel in Amarok, but with no result.

Anyon ehave an idea?

My setup:
PC: Fujitsu Siemens Amilo Pro V2000
Soundcard: M-Audio MobilePre USB
OS: Ubuntu 8.04

---

### Post by paulg on 2008-05-31
Seems to be broken in Hardy. I haven't had a chance to investigate but will update when I get it working again.

===edit==============
See [here](http://ubuntuforums.org/showthread.php?t=846621) for madfuload installation instructions under Hardy. Instructions on this thread will still work for Feisty and Gutsy installations.

---

