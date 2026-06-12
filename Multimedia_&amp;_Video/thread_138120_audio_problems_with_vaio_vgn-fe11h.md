---
title: "audio problems with vaio vgn-fe11h"
date: 2006-03-01
forum: Multimedia &amp; Video
---

### Post by nicola76b on 2006-03-01
hi all. First off all SORRY for my english..

i'm ney in ubuntu. I come from debian sarge, i've just change my laptop and i decided to try ubuntu 5.1. Installation was easy (in debian seems VERY DIFFICULT due video problems) , but i have some problems with audio (i don't heard sounds..)

Here's my lscpi output:
-------------------------------
0000:00:00.0 Host bridge: Intel Corp.: Unknown device 27a0 (rev 03)
0000:00:01.0 PCI bridge: Intel Corp.: Unknown device 27a1 (rev 03)
0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 02)
0000:00:1c.0 PCI bridge: Intel Corp.: Unknown device 27d0 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corp.: Unknown device 27d2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corp.: Unknown device 27d4 (rev 02)
0000:00:1c.3 PCI bridge: Intel Corp.: Unknown device 27d6 (rev 02)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 02)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 02)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b9 (rev 02)
0000:00:1f.1 IDE interface: Intel Corp.: Unknown device 27df (rev 02)
0000:00:1f.2 IDE interface: Intel Corp.: Unknown device 27c4 (rev 02)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d8 (rev a1)
0000:06:00.0 Network controller: Intel Corp.: Unknown device 4222 (rev 02)
0000:0a:03.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:0a:03.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:0a:03.2 Unknown mass storage controller: Texas Instruments: Unknown device 803b
0000:0a:08.0 Ethernet controller: Intel Corp.: Unknown device 1092 (rev 02)
---------------------------------

lshw:
---------------------------------
...
*-multimedia
             description: Multimedia controller
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:d2300000-d2303fff irq:22
....
---------------------------------


I remember that in debian i can configure alsa with "alsaconf", but in ubuntu i can't find command also if alsa-utils seems installed.

I don't know if now it is just configured, i anly know that i cant heard NOTHING..
thanks to anyone,

    Nicola

---

### Post by bernardfrancois on 2006-03-01
Try **modprobe snd-intel8x0** and see if you get any sound.

I got this information here: [https://wiki.ubuntu.com/HowToSetupSoundCards?highlight=%28sound%29](https://wiki.ubuntu.com/HowToSetupSoundCards?highlight=%28sound%29) (read more there).

---

### Post by nicola76b on 2006-03-02
thanks, but not work.
i try "modprobe snd-intel8x0", but i don't get any sound..

when i launch alsamixer
---------
card: HDA Intel
chip: Sigmatel ID 7661
View: [playback] caputure all
Item:  pcm
----------
but i can  see ONLY 1 bar (PCM): is strange, in old dell-inspiron laptop i can see more than ONE bar..

is possible that ubuntu don't recognize the correct sound card? where can i find the real sound card information WITHOUT open my laptop? (i search on google and on sony site but i don't find any usefull information...  SONY VAIO VGN-FE11H)

Thanks!!!!!!!

    Nicola

---

### Post by bernardfrancois on 2006-03-02
When I launch alsamixer here, I also only get one bar for PCM.

You should check the url I posted in my previous post and follow the instructions.

You can also check [www.linux-laptop.net](www.linux-laptop.net) and [www.tuxmobil.org](www.tuxmobil.org), maybe you can find more about your laptop there.

[edit]
I also checked the site of alsa, here I found a list of probably supported intel sound chipsets: [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Intel#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Intel#matrix)

Try to execute the following commands (try the first command, check if you have sound; try the next command if it didn't work, etc):
```

modprobe snd-hda-intel
modprobe snd-intel8x0m

```
[/edit]

---

### Post by nicola76b on 2006-03-06
i follow with attention your suggestions and instruction on previous link but i cant heard no sound.

on windows i use hw-detect software to try to found effective audio pheriferical and it seems a sigma tel audio (intel corp 82801G - ich7 family)

i use gnome, in up tray, right clic on audio icon, under preferences i can choose "sigma tel id 7661 (OSS mixer)" or "HDA intel (alsa mixer)".
Under system-->preferences-->audio   i see ONLY hda intel and NO sigma tel..
It could be a problem??


In previous post (4 days ago), when i said 
"but i can see ONLY 1 bar (PCM): is strange, in old dell-inspiron laptop i can see more than ONE bar.."

i want to say that i can see ONLY pcm bar and no OTHER bar, i think that is not normal..

thanks,
by 
   Nicola

---

### Post by bernardfrancois on 2006-03-06
Maybe you can solve the one-bar-problem by reinstalling alsa mixer (by marking it for re-installation in synaptic). I think it must be in the *alsa-utils* package, but I'm not sure. Maybe you can re-install *alsa-base* as well at the same time.

---

### Post by carlstanford on 2006-03-10
Ciao Nicola: I've the same laptop with a Dapper running a 2.6.15 smp kernel and I have the same problem you described with alsa.
I guess you are Italian, so feel free to write me in pvt to giorrrgio at gmail dot com, maybe we can share some progresses!
Neither I could find alsaconf within the alsa-util package, so I downloaded the latest version of alsa-utils from alsa project site. Alsaconf recognize the sound card and install it without problems, though still no audio, with alsamixer showing only the pcm channel.
I've already tried Breezy before Dapper with a 2.6.13 kernel and then with a 2.6.15 stolen from Debian unstable, but no success, neither that times.

Anyone has any hint?

Bye

---

### Post by bernardfrancois on 2006-03-11
Maybe it would be good for u guys to continue posting here, then other people can help you and people having the same problem might find some hints here.

What you can do is check your BIOS setup utility to see the I/O, IRQ, DMA and DMA2 values of your sound card.

Let's say if you see that IO=530, IRQ=5, DMA=1 and DMA2=0, then you can try this:

```

modprobe snd-hda-intel io=0x530 irq=5 dma=1 dma2=0

```

If you don't get any sound (after verifying if your soun't isn't muted or at a very low level in **alsamixer**) you can try this:

```

modprobe snd-intel8x0m io=0x530 irq=5 dma=1 dma2=0

```

Offcourse with the values you found in bios and not the ones I've put here as an example.

---

### Post by carlstanford on 2006-03-20
Good news!
I've managed to get the sound working!
With a cvs snapshot of alsa and a patch by Ariel Vardi ([https://launchpad.net/distros/ubuntu/+source/alsa-driver/+bug/33719](https://launchpad.net/distros/ubuntu/+source/alsa-driver/+bug/33719)) all is working!
The snapshot is dated 2006-03-13 because the nightly snapshot doesn't compile for me..
Here is a mini howto:
```

mkdir alsa

cd alsa

cvs -q -f -z3 -d ":pserver:anonymous:@cvs.sourceforge.net:/cvsroot/alsa" export -D 2006-03-13 alsa-driver

cvs -q -f -z3 -d ":pserver:anonymous:@cvs.sourceforge.net:/cvsroot/alsa" export -D 2006-03-13 alsa-kernel

wget http://librarian.launchpad.net/1728369/vaio-stac7661-test3.diff

patch -p0 <vaio-stac7661-test3.diff

cd alsa-driver

./cvscompile

sudo make install

echo "options snd-hda-intel model=vaio" | sudo tee -a /etc/modprobe.d/snd-hda-intel

```

Then if you reboot everything should work :-)
Thanks to Ariel Vardi for his great work!

**************EDIT******************
With a fresh 2.6.15-19 dapper kernel audio works on the fly!

---

### Post by nordboi on 2006-03-22
Thanks alot!! :)

---

### Post by nordboi on 2006-03-23
Oh I forgot to mention that this also work for people who got ICH6 :)

---

