---
title: "[SOLVED] No Sound At All..."
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by fourthofjuly on 2008-02-02
Had no sound in  in Fiesty, even Fedora, SuSE & so on.

Sound works in Win XP. Have moved on from Feisty to Gutsy, but still no signs of sound?

I have an Intel D945GCL original motherboard with on-board sound, Pentium D 3.0 GHz, 160 GB SATA HDD & 1GB RAM.

In Ubuntu sound preferences, under Default Mixer Tracks, listed device are HDA Intel (ALSA mixer) and SigmaTel STAC9221 A1 (OSS Mixer).

Am a newbie, but struggling with this problem for a long time. Have learnt a lot of commands in the process:

[COLOR="Red"]**devang@devang-desktop:~$ lspci**[/COLOR]
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

**[COLOR="Red"]devang@devang-desktop:/$ lspci | grep -i audio[/COLOR]**
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

**[COLOR="Red"]devang@devang-desktop:/$ cat /proc/asound/cards[/COLOR]**
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x501c0000 irq 22

[COLOR="Red"]**devang@devang-desktop:/$ aplay -l**[/COLOR]
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


Have to switch to XP only for music. Please help....

Kind Regards,

Devang.

---

### Post by Fechter on 2008-02-02
Have you tried any settings at System-Properties-Sound?

---

### Post by fourthofjuly on 2008-02-02
thanks ...

sound preferences, under Devices...

Yes, under sound events, Test sound ... can hear Beep Beep Beep Beep Beep Beep, but otherwise nothing...

I tried changing from Autodetect to STAC92xx Analog, ALSA etc. but no success.

---

### Post by j0eb0b on 2008-02-02
You might want to take a look at this link on alsa-project.

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

I'm not sure which sound chip your MB uses but maybe the chip is not supported by alsa.  I had problems with sound when I first built my machine and discovered that my on board sound chip (a Karajan 8ch operating on an AMD/nF4 MB) was not supported.  The fix for me was disable on board sound and add an Audigy sound card.

---

### Post by fourthofjuly on 2008-02-02
I guess my chipset is

ICH southbridge HD-audio and modem  ( ICH7)

Correct me if I am wrong...

What next?

---

### Post by fourthofjuly on 2008-02-03
[B][COLOR="Red"]I hope someone can get me out of this?

I need to get the sound working in Ubuntu, since I don't won't to switch over to XP every time for my music...[/COLOR][/B]

I have posted the outputs from lspci, aplay -l etc. commands.

Please help...

Thanks & Kind Regards,

Devang.

---

### Post by Mze on 2008-02-03
Check this [thread]("http://ubuntuforums.org/showthread.php?t=685619") out.

See if any of the suggestions there work for you.

---

### Post by fourthofjuly on 2008-02-03
Mze,

thanks,

I did check out the link you've recommended, but did not get much help...

---

### Post by Mze on 2008-02-03
Another [link]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/install-ubuntu-feisty-fawn-on-a-dell-latitude-d820") that should solve your sound problem.

Your chipset is the same as the laptop on the page, so if you follow the threads in the SOUND section, I'm sure you'll be able to get your sound working.

---

### Post by fourthofjuly on 2008-02-05
> **Mze said:**
> Another [link]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/install-ubuntu-feisty-fawn-on-a-dell-latitude-d820") that should solve your sound problem.

Your chipset is the same as the laptop on the page, so if you follow the threads in the SOUND section, I'm sure you'll be able to get your sound working.
Sir, thank you so much... I now have sound working, was struggling since over last 6 months... the solution I found...

added the following line to my /etc/modprobe.d/alsa-base file:

**options snd-hda-intel model=ref**

thank you all...

Now I need not switch to XP as I can play my music in Ubuntu...!!!

Kind Regards,

Devang.

---

### Post by nullfactor on 2008-02-05
I have the same chipset... nothing worked for me until I did the following:

1) ```
 sudo -s -H
```

2)  Enter super user's password

3)  ```
cd /boot/grub
```

4)  Edit the file "menu.lst" with the text editor of your choice... myself, I use vi.
  
     ```
vi menu.lst
```

5)  Locate the kernel you are booting.  It should read similar to the following (note:  it may not be exact... but it will be close):

```
 title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=486bfabb-be86-4fbd-8ff0-53cc012b98d1 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
```

6)  At the end of the line that begins with "kernel", add the following:
     
      ```
acpi=off
```

7)  Reboot your computer.

8)  Enjoy sound!!! 

Good luck!  This worked for me... so hopefully, you'll enjoy the benefits, as well.

---

