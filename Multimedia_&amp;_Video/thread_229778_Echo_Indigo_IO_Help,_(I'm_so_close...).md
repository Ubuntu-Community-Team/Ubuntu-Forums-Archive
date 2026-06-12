---
title: "Echo Indigo IO Help, (I'm so close...)"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by adds2one on 2006-08-04
Hello,

The only thing stopping me from fully embracing Linux in general and Ubuntu in particular is the functioning of my Echo Indigo IO PCMCIA sound card.

I feel that I am very close to having it work. I will try and give as much information as I can so that someone can hopefully help me fulfill my dream of a Microsoft free laptop!

First of all, the card does function perfectly under Windows on this laptop and the power light does turn on in Linux.

I have followed the instructions at [https://help.ubuntu.com/community/EchoMia](https://help.ubuntu.com/community/EchoMia)
I have also found information on the Echo cards here [http://www.webalice.it/g_pochini/ead/](http://www.webalice.it/g_pochini/ead/)
I have also thoroughly read these related posts:
[http://www.ubuntuforums.org/showthread.php?t=142587&highlight=echo+layla+24+ubuntu](http://www.ubuntuforums.org/showthread.php?t=142587&highlight=echo+layla+24+ubuntu)
[http://www.ubuntuforums.org/showthread.php?t=199599](http://www.ubuntuforums.org/showthread.php?t=199599)
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

So what I have done so far is follow the instructions in the first link above (the EchoMia post), making sure that I used the name of my card, 'indigoio' instead of 'mia' and using 2.6.15-26-386 instead of 2.6.15-26-686 to correctly reference my own system.

The only hang up I encountered during the procedure outlined in the EchoMia post was that when I tried to configure alsa-utils I got this message at the end of the configure process:

```
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.12... not present.
configure: error: Sufficiently new version of libasound not found.

``` 
I was then unable to make or make install the alsa-utils, however from all my reading it seems that alsa-utils is extra anyway and not at all neccessary to get a sound card working. Still, any help with this small issue would be appreciated.

So it seemed that everything was going to be fine but I rebooted and my Echo Indigo IO still did not work.

I tried sudo modprobe snd_indigoio which seemed to do nothing.

I tried aplay -l and there is no sign of my Indigo IO, just the Intel on board sound which works fine.

alsamixer only comes up for the default Intel soundcard. 

echomixer gives this sad message:
```
No Echoaudio cards found, sorry.
```

I then tried lspci -v and got the following related info:
```
0000:03:00.0 Multimedia controller: Motorola DSP56361 Digital Signal Processor (rev 01)
        Subsystem: Echo Digital Audio Corporation Indigo IO
        Flags: medium devsel, IRQ 11
        Memory at f6000000 (32-bit, non-prefetchable) [size=1M]
```

next I tried hwinfo which seems to say that the driver is active and confirms that I modprobed the correct device:
```
28: PCI 300.0: 0480 Multimedia controller
  [Created at pci.277]
  UDI: /org/freedesktop/Hal/devices/pci_1057_3410
  Unique ID: svHJ.WBwF3XNH0e5
  Parent ID: GA8e.qfTO22bUWE9
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:01.0/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: unknown
  Model: "Echo Digital Audio Indigo IO"
  Hotplug: CardBus
  Socket: 0
  Vendor: pci 0x1057 "Motorola"
  Device: pci 0x3410 "DSP56361 Digital Signal Processor"
  SubVendor: pci 0xecc0 "Echo Digital Audio Corporation"
  SubDevice: pci 0x00a0 "Indigo IO"
  Revision: 0x01
  Memory Range: 0xf6000000-0xf60fffff (rw,non-prefetchable)
  IRQ: 11 (176382 events)
  Module Alias: "pci:v00001057d00003410sv0000ECC0sd000000A0bc04sc80i00"
  Driver Info #0:
    Driver Status: snd_indigoio is active
    Driver Activation Cmd: "modprobe snd_indigoio"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (CardBus bridge)
```

then I looked in dmesg and found this:
```
[17179592.856000] ALSA /home/jjob/alsa-driver-1.0.12rc2/pci/echoaudio/../../alsa-kernel/pci/echoaudio/echoaudio.c:46: get_firmware(): Firmware not available (-2)
[17179592.856000] ALSA /home/jjob/alsa-driver-1.0.12rc2/pci/echoaudio/../../alsa-kernel/pci/echoaudio/echoaudio_dsp.c:249: Firmware not found !
[17179592.856000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[17179592.856000] Echoaudio Indigo IO: probe of 0000:03:00.0 failed with error -2
```

There seems to be a problem with the firmware not being found even though I followed the instructions in the EchoMia post linked to above and did do this during the installation process:
```
sudo cp /lib/firmware/ea/* /lib/firmware/2.6.15-26-386/
```

I also checked those files referenced above and they do contain the indigo_dsp.fw and indigo_io_dsp.fw files.

Finally, from the g_pochini link (also listed above) I read this:

```
Make sure that /lib/firmware is a symbolic link to /usr/lib/hotplug/firmware or vice-versa:

$ ls -la /lib/firmware
lrwxrwxrwx 1 root root 26 Aug 15 2005 /lib/firmware -> /usr/lib/hotplug/firmware/

If it isn't, do it, otherwise the firmware loader will not be able to find the files.
```

So the most likely thing to me seem to be that the firmware isn't referenced properly, but as I do not have /usr/lib/hotplug/firmware folder I am at a loss what to do.

If anyone has any ideas I would love to hear them.

Thank you so much if you have taken the time to read this post. I have tried many distros and may forums and am really taken by Ubuntu. This is a great community and I look forward to serving it as well as recieving help.

- J

---

### Post by adds2one on 2006-08-05
Anyone got any ideas?

---

### Post by ronoc on 2006-08-07
Hi,
have you tried from terminal >> dmesg.
Does this give you any extra information?
If I remember correctly the firmware should be installed properly before installing the drivers (don't quote on that it's just an inkling I have)
secondly do you boot with the card inserted?
Thirdly dapper should already have support for hotscript stuff. Strictly speaking it does not use hotscript but a more up to date thing called udev.
you seem to be almost there. when i initially tried I was getting similar errors. I reinstalled the firmware with the symbolic link in place, made sure the echo drivers were being loaded at startup. I forget what file I had to edit to do this but it was in one of the post regarding thi. 
(either way you can always at runtime load with sudo modprobe "mia"?)

I would also resolve the alsa utils problem as this is could  be the root of your problems. have you tried searching for those libs in synaptic.

---

### Post by adds2one on 2006-08-07
Hi ronoc,

The dmesg output was in my original post. Here it is again: ```
[17179592.856000] ALSA /home/jjob/alsa-driver-1.0.12rc2/pci/echoaudio/../../alsa-kernel/pci/echoaudio/echoaudio.c:46: get_firmware(): Firmware not available (-2)
[17179592.856000] ALSA /home/jjob/alsa-driver-1.0.12rc2/pci/echoaudio/../../alsa-kernel/pci/echoaudio/echoaudio_dsp.c:249: Firmware not found !
[17179592.856000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[17179592.856000] Echoaudio Indigo IO: probe of 0000:03:00.0 failed with error -2
```

Could you take a look at it and tell me what you think?

I am booting up with the card inserted.

I reinstalled the firmware but nothing changed.

Which symbolic link did you make?

I think that the Echo drivers are being loaded because in hwinfo I see this:

```
 Driver Status: snd_indigoio is active
```

Is there any other way for me to check if the drivers are loaded?

Thanks so much for responding!:D

---

### Post by adds2one on 2006-08-07
I'm starting to think that the problem has to do with the hotplug scripts. I was just told "As of Ubuntu 6.06 "dapper", hotplug is no longer included in the distribution. It's been replaced by udev+hal."

So did you have to install the hotplug scripts yourself? If so, what do I install and how?

---

### Post by malras on 2006-08-19
Hi adds2one:

I have  exactly the same problem with my indigo io and ubuntu dapper. I recently changed from suse to ubuntu (which feels great),  but, however,  the indigo io ran smoothly with suse... (which had hotplug on by default, if I remember correctly)

Did you manage to get the card run? Recompiling the kernel with hotplug enabled may be a solution. I tried this but ran into multiple troubles with kernel compilation (first time i did this), so I have no results till now. Maybe you have a alternative solution by now? 

Best,
malras

---

### Post by adds2one on 2006-08-20
Hi Malras,

No I have not got my indigoio to work in ubuntu yet. I haven't had a lot of time to work on it but am hoping to have it sorted before the new school year in september. I will be sure to post any success that I have here. Please let me know if you have any luck too.

---

### Post by Rob_Frohne on 2006-08-30
Sorry that this is a "Me too!" post.  The only difference I have here is that the light on the card doesn't light up for me.

Rob   :-k

---

### Post by agrabah on 2006-09-05
OK, girls and boys, I've got it. It least I solved it here on my box (Kubuntu Dapper 6.06).

To outline the problem: this particular card has no firmware on it; it has to be loaded into the memory at boot.
The firmware loader uses hotplug scripts, which were made obsolete in Ubuntu / Kubuntu. They have to be installed for it to work.

The procedure:

I followed the post about the Echo Mia sound card, mentioned in the first post of this thread.

After that I installed the "latest" hotplug scripts (you can get them at [ftp://ftp.kernel.org/pub/linux/utils/kernel/hotplug/hotplug-2004_09_23.tar.bz2);](ftp://ftp.kernel.org/pub/linux/utils/kernel/hotplug/hotplug-2004_09_23.tar.bz2);)  Yes, they are old, but they work. Unzip the file and read the instalation instructions and follow it.

Next step: make sure there are echo firmware (*.fw) files in /lib/firmware/ea
If not - you probably haven't compiled or installed alsa-firmware; see the aforementioned post on Echo Mia.

The last step - I had to contact Giuliano Pochini (the man who wrote the drivers for the card) to sort it out. We found out there was a typo in the makefiles of alsa-firmware for the echoaudio firmware files - one of the firmware files didn't compile; so just open a console, go to the directory with alsa-firmware source files. In my case this is:
```
/home/tine/Samogradnja/alsa-firmware-1.0.12/echoaudio
```  

Run this command:

```
./fw_writer DSP/LoaderDSP.c loader_dsp.fw 
```

And then:

```
sudo cp loader_dsp.fw /lib/firmware/ea
```

Reboot, and then do:
```

dmesg | grep echo
```

Which will tell you if the firmware was initialized.

From then on go back to Echo Mia post.

I hope it will help someone. Many thanks to Giuliano Pochini.

Tine

---

### Post by malras on 2006-09-07
Hi guys,

thanks a lot for the help! Tine's method worked for me too! 

Best,
malras

---

### Post by adds2one on 2006-09-07
This seems to have worked although I still have no output from my IndigoIO.

Everything seems in order, I unmuted the channels in alsamixer and in echomixer. The firmware is loaded.

When I go to System->Preferences->Sound there is no sound card at all listed as 'default sound card' so I can't choose to use the IndigoIO over my laptops built in sound.

What am I still missing? I manually did sudo modprobe snd-indigoio even though I think hotplug is doing this automatically. Do I need to add snd-indigoio to /etc/modules?

Is there some other way for me to select my IndigoIO as my prefered audio card?

---

### Post by agrabah on 2006-09-07
Check the Echo Mia post about setting indexes for the various soundcards on your system; I set my Echo Indigo IO to index 0 in the file /etc/modprobe.d/alsa-base

Just add the following lines to the end of the file, thus making your indigo the default sound card:

```
options snd_indigoio index=0
options snd_ali5451 index=1
```

Instead of snd_ali5451 insert the name of the module of your other sound card.

You will have to reload alsa - the fastest way is just to reboot your computer. 

Hope this helps.

Tine

---

### Post by adds2one on 2006-09-07
That did it!!

I am so happy to have my IndigoIO working!! :D 

Thanks for your help Tine, and big thanks to Giuliano Pochini for all of his help too.

Now I can't wait for EnergyXT2 Linux version to be finished!

[http://www.xt-hq.com/](http://www.xt-hq.com/)

---

### Post by slag on 2006-09-20
I think I'm not getting hotplug set up correctly.  All I could find in the instructions is to do a "sudo make install."

agrabah, could you please clarify what needs to be done to get hotplug set up correctly?  I have all the echo/indigo firmware in /lib/firmware/ea, but it won't load until I get hotplug installed.

---

### Post by blitze on 2006-12-02
You know, it's a bloody pain in the rear that audio takes a bit of tweeking to get going but, thanks for the hand hold.

It took me a little to get my head around but everything is working a treat now on my Gina3g and now I can watch movies, listen to music and pull my haid out over VSTi's and Reaper.

Thanks again.:mrgreen:

---

### Post by bozo_the_grey on 2007-03-17
I'm trying to make my Echo Indigo IO work.
I don't manage to make install hotplug on ubuntu edgy 6.10
But to me seems that I can install alsa firmware anyway without error messages.
Anyone managed to make the sound card work without hotplug?


Error when trying to install hotplug:

/usr/bin/install -c -D sbin/hotplug /sbin/hotplug
/usr/bin/install -c -d /etc/hotplug/{usb,pci}
/usr/bin/install -c -D etc/hotplug.d/default/default.hotplug /etc/hotplug.d/default/default.hotplug
for F in etc/hotplug/{*.{agent,rc},hotplug.functions} ; do \
            /usr/bin/install -c $F /etc/hotplug ; \
            done
/usr/bin/install: cannot stat `etc/hotplug/{*.{agent,rc},hotplug.functions}': No such file or directory
make: *** [install] Error 1

---

