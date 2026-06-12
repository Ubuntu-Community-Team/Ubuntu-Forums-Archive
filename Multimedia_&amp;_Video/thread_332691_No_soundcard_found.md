---
title: "No soundcard found"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by circles on 2007-01-06
Installed Kubuntu on my computer as second OS, In Windows XP sound works perfectly. I have nforce2 chipset and AC97 integrated sound card. So I don't remember exactly but I think I got the card working yesterday after 

sudo nano /etc/modprobe.d/alsa-base  and adding line 
"options snd-intel8x0 ac97_quirk=3" , then installing libxine-extracodecs from the multiverse repository.

However, today the system had no more sound.the mixer doesn't work, Kaffeine or amaroK don't either. 
aplay -l says: aplay: device_list:221: no soundcards found...

but when I insert lspci -v I get among the list:

0000:00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
        Subsystem: ASRock Incorporation: Unknown device 9761
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        I/O ports at d800 [size=256]
        I/O ports at e800 [size=128]
        Memory at ff6ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

So the system obiously sees and recognizes the soundcard.

sudo modprobe snd-intel8x0 says:
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.15-27-386/updates/alsa/pci/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Then I removed problematic packages:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

and installed them again:
sudo apt-get install linux-sound-base alsa-base alsa-utils

rebooted, nothing had changed.
Then I compiled the driver from alsa source:
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source

sudo dpkg-reconfigure alsa-source

and chose the right variant (intel8x0), compiling process didn't encounter any errors. 
As the second variant I tried:
 cd /usr/src sudo tar xjvf alsa-driver.tar.bz2 cd modules/alsa-driver and

sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=intel8x0 --with-oss=yes

It did the first command, but as for the second: sudo: ./configure: command not found

When I type in: alsamixer I get:
alsamixer: function snd_ctl_open failed for default: No such device

And under the Sound section of KInfoCenter I can read that there are no sound devices, no mixers etc in the config. 

Basically I tried everything from this thread:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

So do you guys have any ideas what to try next. My second day on Linux and I'm already ](*,)

---

