---
title: "Yet another sound problem"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by floke on 2006-11-18
Hi,

I have no sound at all from Ubuntu6.10.

Here are the results of some bash entries....

lspci -v gives =

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 217
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at af10 [size=16]
        Capabilities: <access denied>

 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

aplay --list-devices : Gives =

card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lsmod | grep snd : Gives =

snd_hda_intel          20116  2 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  2 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  2 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

cat /proc/asound/cards : gives =

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x55080000 irq 58


My name is also listed after audo:x89 from using 'sudo gedit /etc/groups'

Have also tried altering the settings in alsamixer

The one thing that seems to be a clue is this...

sudo totem : gives = 

(totem:21335): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

** (totem:21335): WARNING **: Failed to connect to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I haven't yet tried anything to do with eg ndiswrapper etc. since I want to make sure that I have all the right bits and pieces actually installed first (drivers, modules etc) before I move on to other measures.

If anyone has any thoughts then please help!

Steve

---

### Post by joegiampaoli on 2006-11-23
Maybe you wanna try this guide.
Hope it helps. Cheers.

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

### Post by floke on 2006-11-27
Nothing gives!

Have tried just about every conceivable thing there is. My PC detects the card, all the drivers are loaded, all the alsamixer settings are in the right place - but no sound](*,) 

S

---

### Post by foxmulder881 on 2006-11-27
What version of Ubuntu did you use before Edgy and did you have sound then?

---

### Post by floke on 2006-11-29
This is the first time I have used ubuntu. The sound works fine in XP (though clearly no reason to go back to it):mrgreen: The sound also works fine with my headphones. Modinfo soundcore tells me that the module is there - so clearly all the modules are loaded and the soundcard is being recognised - it just wont connect the sound to the speaker!

Incidentally, have also tried the live Dapper CD and the Knoppix CD and the sound doesn't work on those either.

Bummer.

---

