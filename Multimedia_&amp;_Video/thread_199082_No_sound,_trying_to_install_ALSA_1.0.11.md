---
title: "No sound, trying to install ALSA 1.0.11"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by namnam on 2006-06-18
Hi all

After installing Ubuntu 6.06, my soundcard wasn't detected (correctly?).

lspci | grep audio
> 
0000:00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)


lshw
> 
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: M5455 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 4
             bus info: pci@00:04.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: ioport:c800-c8ff iomemory:faeff000-faefffff irq:225

When looking in my motherboard manual, the description of the built in audio device is this:
> 
ADI AD1888 SoundMax 6-channel audio codec support for S/PDIF out interface


After reading the other no-sound-threads, it seemed my best bet would be to install the newest ALSA version (1.0.11). I started following the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=187156](http://ubuntuforums.org/showthread.php?t=187156)

First of, it said no C compiler was found, so I installed one by running:
> 
sudo apt-get install build-essential


Then it couldn't find "version.h" when it was looking for the linux headers, so I had to install those too by runnning:
> 
sudo apt-get install linux-headers-<my kernel version number>


Now, running "sudo ./configure --with-kernel=/usr" seems to go well, but when I run "make install", I get this:
> 
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/per/download/alsa-dapper-1.0.11/alsa-driver-1.0.11/acore'
make: *** [install-modules] Error 1

(This is only the end of the log, should I post the rest as well?)

Anyone knows what's going on? I'm very new to Linux.

Thanks in advance!

---

### Post by HanZo on 2006-06-28
hmm you're not alone out there... have the same problem... no wonder people don't use linuz that much... there's always something that does not work as it should.
still there doesn't seem to be solution to the problem... and I am not really sure I know what the problem really is...

---

### Post by HanZo on 2006-06-29
I tried Suse 10.1 same problem... but now I found something... there is one thing where Suse beats Ubuntu by far: confi utils (very good for lazy ppl like me) Yast gives me the option to turn on two "workarounds" for a) problematic interrupts on some motherboards (buggy irq) and b) problematic codec semaphor (bool) (sorry translating this from german so may not be 100% accurate). know what, now everything works fine.. card is detected and sounds ok! looked at the driver it is using it is detected as M5455 PCI AC-LINK Controller Audio device using the snd-intel8x0 driver module.
hope this can be any help... unfortunately I don't know how to activate these workarounds in dapper...

---

### Post by marciovinicius on 2006-07-20
I have exactly the same problem!
This is realy deceptive...
but I don't want to move to Suse (yet). can someone else help us?...

I've been searching Alsa-Project.org... I realized that ALsa doesn't support                                Analog Devices AD1888 SoundMax... But I tried to configure my soundcard as AD1887 (the nearest number) reading this <http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Analog+Devices&card=.&chip=AD1881%2C+AD1881A%2C+AD1885%2C+AD1886%2C+AD1887%2C+AD1980%2C+AD1981A%2C+AD1981B%2C+AD1985&module=intel8x0>
but I didn't understand anything... It looks like something (or everything) doesn't match...

Actually, I don't even know if I should use [[COLOR=Black]intel8x0[/COLOR]]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Analog+Devices&card=.&chip=AD1881%2C+AD1881A%2C+AD1885%2C+AD1886%2C+AD1887%2C+AD1980%2C+AD1981A%2C+AD1981B%2C+AD1985&module=intel8x0") or [via82xx]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Analog+Devices&card=.&chip=AD1881%2C+AD1881A%2C+AD1885%2C+AD1886%2C+AD1887%2C+AD1980%2C+AD1981A%2C+AD1981B%2C+AD1985&module=via82xx")...

How can I configure a Soundcard in Ubuntu?

I'm new in Linux.

:confused::confused::confused::confused:

---

