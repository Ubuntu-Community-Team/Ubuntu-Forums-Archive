---
title: "Yet another es18xx issue."
date: 2006-03-21
forum: Multimedia &amp; Video
---

### Post by outrage on 2006-03-21
After reading at least 10-15 threads about this card over the last 2 days, I at least have it being recognized at this point.  However, I still have no sound.

When going to System>Preferences>Sound, the ES1869 is listed.  Also, I can adjust the volume from alsamixer and the gnome volume control interface.  When attempting to play an .mp3 or .wav, however, no sound comes out.  No errors are given, it just doesn't play.  On boot, gnome seems like it attempts to play a sound, but it just gives a system beep instead.  When using totem or mozilla mplayer, it will go through the entire .mp3 file without error (and without sound), just as if the sound were muted....yet none of the channels are muted through the volume control.

So, I'm not sure if it's a configuration issue, or what I'm missing.  So here are the basics:
/etc/modules:
```
lp
mousedev
psmouse
snd-es18xx

```

/etc/modprobe.d/alsa-base
```
alias char-major-116 snd
alias snd-card-0 snd-es18xx
options snd-es18xx index=0 enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

```

lsmod |grep snd
```
snd_es18xx             30984  2
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_es18xx,snd_pcm_oss
snd_page_alloc         10600  1 snd_pcm
snd_opl3_lib           10624  1 snd_es18xx
snd_timer              24164  2 snd_pcm,snd_opl3_lib
snd_hwdep               8896  1 snd_opl3_lib
snd_mpu401_uart         7296  1 snd_es18xx
snd_rawmidi            24704  1 snd_mpu401_uart
snd_seq_device          8460  2 snd_opl3_lib,snd_rawmidi
snd                    54884  13 snd_es18xx,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9600  1 snd

```

So, with that said...help?  :confused:

---

### Post by FarEast on 2006-03-31
Hi, 

I have a laptop PC which has 'ESS solo-1' on board.  When I try to play a wave/mp3 file, I can hear something which is far from how it should sound.
I wonder if old-fashioned ISA sound chips are capable of playing back sound files sampled at 44100 Hz.
If this is the cause of your problem, editing the file '.asounrc' which exists in your home directory may help.

### BEGIN set-default-soundcard
# If the "### BEGIN..." and "### END..." comments are intact, then you
# can change your default soundcard with "set-default-soundcard(1)."
# Remove these comments if you want to maintain a custom configuration
# that should not be changed automatically.

# Default soundcard
defaults.pcm.card 0

### END set-default-soundcard
[COLOR="Green"]#describe the following:[/COLOR]
pcm.es {
    type hw
    card 0
    device 0
}
pcm_slave.sl2 {
    pcm es
    rate 11025
}
pcm.rate_convert {
    type rate
    slave sl2
}

----------
Then try the following:
[COLOR="Red"]- Execute '/etc/init.d/alsa-utils restart' as root.[/COLOR]
- Start xmms.
- Select Options > Preferences > Audio I/O Plugins
- Choose 'Alsa 1.2.10 output plugin' and click 'Configure'
- Type 'rate_convert' in the entry 'Audio device' and click 'OK'.

---

### Post by Raoul_Duke on 2006-04-22
I have spent 7+ hrs. reading every piece of info I could find regarding the ESS 1869 ISA on board sound that is common to most older Compaq Deskpros (or for that matter about any Compaq w/ a PII processor from 233mhz and up). I am a MCSA, but I have only played w/ Linux now and then. I have tried many flavors and I was only trying Edubuntu because I had an old stack of these I was going to turn into starter PC's to raise some money for our local BSA pack. What I found interesting, was that when I looked @ the Device Manager I would see a PnP device numbered 001869. I knew that this was the device, but it would not show any driver or other info. When I would look @ the sound properties, I would see no sound card to choose. During close of the system, it would show as the only fail (to shutdown the sound). I tried every modprobe suggestion to no avail. I attempted to edit etc/modules repeatedly until I found out that logging on as root was not available, so you must use the SUDO command before the gedit in a terminal window to be able to edit them (that had to be 1 1/2 hours of the total time finding out). I then tried everything I could find. I would get the mixer to not show an error, but still no sound, and no sound card showing available. Then, I ran accross your post. As follows:[QUOTE=outrage]
So, I'm not sure if it's a configuration issue, or what I'm missing.  So here are the basics:
/etc/modules:
```
lp
mousedev
psmouse
snd-es18xx

```

/etc/modprobe.d/alsa-base
```
alias char-major-116 snd
alias snd-card-0 snd-es18xx
options snd-es18xx index=0 enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

```
[/QUOTE]

So, I editted both of those files, adding the alsa-base code at the beginning of the entire file. The one thing I did do that you did not mention was to look in the BIOS and check the audio setting and make sure that they matched:
```
options snd-es18xx index=0 enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

```

The only other choice to those setting is disabled. After rebooting one last time, this worked for me. I don't know if any of this will help you but for those looking for a solution to the ESS 1869 audio problem for the Compaq Deskpro EN or other similar series, I hope this becomes some comfort.

Thank you for being the first one to point me in the right direction.

---

### Post by splinky on 2006-05-01
:)   :) 

Woohoo!  Thank you! Thank you!  This worked for me.  I have an older Compaq Armada 3500 63000/T/6400/0/0/1 and I installed Breezy about a month ago.  I love how easy it was to install, it even picked up my old 3com wireless B adapter...but no sound.  I had other issues with video...but resolved those with some googling and searching here on the forums.

---

### Post by beelzebub on 2006-05-07
Hi,

this works for me on an old Siemens Scenic Mobil 700 too :-)
Thanks too all

---

### Post by MonkeyBoy on 2006-05-07
I think I am experiencing the same issues as Outrage.  I'm running Breezy on an Armada 3500 and had the standard problem with es1869.  I checked the bios for the soundcard details and got the card recognised as above.  
However, it isn't behaving properly...Now when I start Ubuntu, and it tries to play the startup sound, the sound seems to play for about a second but then either keeps looping the same sound or crashes the startup.  

When asked to do anything useful like play a cd or any sound nothing happens, but on Totem the track timer ticks along with no sound.

I get the feeling that perhaps I need to set the audio at some lower quality setting or something but haven't a clue where to start.

If anyone has any suggestions regarding a solution I would be very grateful for advice.

---

