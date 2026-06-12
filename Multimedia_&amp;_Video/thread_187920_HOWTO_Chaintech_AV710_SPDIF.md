---
title: "HOWTO: Chaintech AV710 SPDIF"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by electrosoccertux on 2006-06-03
For those of you with the best-bang-for-buck-SPDIF card, the Chaintech AV710 / AV-710 [redundancy added to help people searching for either], this post is to help you configure it. In Dapper Drake, the solution is quite simple.

Assuming you have alsa as your sound driver (default in Ubuntu6), you need to add an asound.conf to /etc. Alsa will check this before it does anything with the sound next time. Paste this into your asound.conf file (will probably have to create it) and then your SPDIF should work:

```
# copy this file in /etc/asound.conf (for all users) or $HOME/.asoundrc (just for you)
#
# this file map uses mixer as explained in
# http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php
# and explain what I discovered with trial and error
#
# I have Mandrake 9.2, Alsa 1.0.0.rc2, kernel 2.4.23,
# 6 channel amplifier connected to the card digital out (optical / red light)
# 2 channels connected to the analogic out
#
# run alsamixer from a terminal or konsol. Set everything to "PCM Out". 
# (but see below at KsCD)
#
# I have aRTs NOT enabled.
# If you want otherwise go to KDE Control Center, Sound Sytem, flag the field 
#       "Start aRTs soundserver on KDE startup".
# In the tab "Sound I/O" in the field 
#       " Use Custom Sound Device"
# insert /dev/sound/adsp to have output to the digital
# otherwise do not flag the field or use /dev/sound/dsp (without the 'a') 
# to use analog output
# use bottum "test" to test :)
#
# Also test sounds with KDE Control Center, LookNFeel, 
# System Notification, 
# Actions Play a Sound
# If you don't want to use aRTs but you do still want to have 
# KDE Sounds System Notification
# (I don't see any reason to do it) be sure to press "Player Settings..." 
# button and in the
# popup window use external player and type /usr/bin/aplay
# aRTs does not care about this configuration file
#
# in xmms 
#
#       press ctl+P, output plugin = Alsa 0.9, 
#       configure, user defined: default, 0, PCM.
#
# Output goes to Digital because of pcm.!default setting below.
# aRTs settings before explained do not affect xmms
#
# Totem Media Player: output goes to digital (because of pcm.!default setting below).
# aRTs setting before explained do not affect Totem
#
# my KsCD works if, within alsamixer, at least "IEC958" or "IEC958 1" is setted
# as "H/W in 0" or "H/W in 1". 
# You can even set both but in this case
# this setting (instead of "PCM out") void other digital sounds.
# aRTs setting before explained do not affect KsCD
# KsCD not care about this configuration file.
#
# mplayer (from terminal or konsole) works with: mplayer -ao alsa9:default avi1.avi
# if the option ao=alsa9:default is set in mplayer.conf it works 
# also with mplayer avi1.avi
# mplayer.conf is in /etc/mplayer/mplayer.conf (but read notes in the 
# files itself: there are other files as well)
#
# the gui version of mplayer (gmplayer) seeks the file /etc/mplayer/mplayer.conf 
# and then in your home .mplayer/config and then .mplayer/gui.conf.
# if the sound is not working verify ao option there.
# I did not understand everything here, but if you delete gui.conf 
# the file is recreated
# by gmplayer. In my experience it creates also an entry ao_driver = "alsa9" that must
# be corrected as ao_driver = "alsa9:default"
# if you launch via command line you can use gmplayer -ao alsa9:default avi1.avi
# or use MenuDrake to add the -ao option to the menu command.
# Running from a terminal or konsole I have several warning messages like:
# alsa-control: mixer attach default error: Invalid argumentA:   5,5 V:   5,5 A-V:
# or
# alsa-control: unable to find simple control 'PCM',0 3%  4%  0,9% 3 0 92%
# but the system seems to work fine
#
# A note about mixers.
# Mixer allow you to share the sound device between different applications 
# and have different
# sounds mixed toghether. aRTs is a mixer. This configuration file provide a 
# mixer as well.
# I don't have problems not using aRTs.
#
# Take care
# Alessandro Vallega

pcm.!default {
        type plug
        slave.pcm "dmixer"
}

pcm.dmixer  {
        type dmix
        ipc_key 1024
        slave {
                pcm "hw:0,1"
                format S32_LE
                period_time 0
                period_size 1024

# increased buffer_size because in my system 1024 cause bad
# audio performance (for totem media player and mplayer)
                buffer_size 8096

                rate 44100
        }
        bindings {
                0 0
                1 1
        }
}

ctl.dmixer {
        type hw
        card 0
        device 1
}

#

```

I haven't bothered trying to get the AC3 passthrough to work, I might try later. But for now, video and sound work so I'm happy. But please post if you do get Dolby Digital passthrough working.

I did not make this config file, Alessandro Vallega did. So kudos to him for making this work.

---

### Post by EnterDaMatrix on 2007-04-23
Thank you sooo much. In fact on my system the **only** thing that worked was passthrough, I couldn't get normal apps to have SPDIF out. Anyway heres how to do passthrough, only works in Xine. Set Xine to use "plug:iec958" as the output device and set it to passthrough. That should work.

The only thing this doesnt fix for me is Flash 9. How do I go about setting this up?

---

### Post by DealerMan on 2007-04-30
I've carefully read the notes provided by Mr. Vallega, but I'm still unclear when he tells me to to set everything to PCM Out.  Does this he means turn all other selections to off?  It's a bit confusing.  I also don't have KDE installed, but certainly can if it's necessary.  I appreciate any help.  Thanks in advance.

---

### Post by eqisow on 2007-07-22
I'm trying to get SPDIF working with my AV710, but changing my asound.conf gives me no sound, disabling both analog and SPDIF.
 
Admittedly, I'm not very clear on the instructions. How do you change your output to PCM with alsamixer? Everything is set to PCM under switches in KMix, if that's the same thing.

Edit: OK, I figured out alsamixer and I'm pretty sure everything that can be set to PCM is.

Edit again: I've tried using envy24control, but I get the error "No ICE1712 cards found." However, "lspci | grep Envy24" returns "00:0b.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)"

---

### Post by eqisow on 2007-07-22
OK, so I'm making progress, sort of.

The following, found on the  [Gentoo wiki]("http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#Sound_routed_to_spdif"), makes SPDIF work, but Analog stops working:

```
pcm.!default {
type plug
slave {
rate 48000
pcm "spdif"
}
}
```

Unfortunately, I need both. :(

Edit: Well, for now I have two *very* basic bash scripts to turn SPDIF on and off. If somebody could turn that into one script that turns it off if it's on and on if it's off I'd really appreciate it.

---

### Post by peterm1004 on 2007-08-12
equisow - I am very confused after spending about 3 hours getting this to work - found it confusing - when I play with settings now in alsamixer it doesn't seem to have much effect. 

Anyway the important thing is that your fix WORKED for me- so thanks!

---

### Post by peterm1004 on 2007-08-12
Ah - declared victory too  early - the previous fix only works for Gxine output - doesn't work for things like RealPlayer/Helix player - any tips on this welcome.

---

### Post by peterm1004 on 2007-08-12
I know suspect that my problem occurs becuase RealPlayer puts its output through the oss api rather than alsa. I have tried installing something called aoss but this doesn't seem to fix things. At this point, I am thinking of giving up for a while and waiting until RealPlayer supports alsa directly as their dev site seems to say it will. 
Peter

---

### Post by craigisaloser on 2007-08-31
That bit of code from eqisow worked once I put it in my /etc/asound.conf and restarted ALSA with sudo /etc/init.d/alsa-utils restart EXCEPT only one application can play audio at a time. Testing with Doom on DVD now...works in stereo only, with the optical spdif connection, but without dolby digital passthrough.

My system:
 AMD64 dual core 2.4 ghz | 4gb RAM
 ASUS A8V-Deluxe motherboard
 Chaintech AV 710 (both optical and analog connected)
 BFG 6800GT OC nvidia card
 Ubuntu Feisty Fawn 64-bit
 Using the system default "Movie Player" (totem)
 TV-Output using the nvidia linux driver

My amplifier is about 7 years old - a Yamaha RX-V495 - and I've read something in the past about old hardware not supporting modern passthrough formats, but I don't know.

Thanks to all for the help in this thread. I've used it often.

*UPDATE got the Dolby Digital working after reading this post
[http://www.phoronix.com/forums/archive/index.php/t-556.html](http://www.phoronix.com/forums/archive/index.php/t-556.html)

* UPDATE 2 since I have an on-board audio chip (which I'm either unable to disable or just haven't done so) and Ubuntu seems to switch back and forth with the hardware mapping -- long story short, on occasion the spdif passthrough fails entirely on reboot, and to fix it I must switch hw0,1 for hw1,1 or vice versa, then 'sudo /etc/init.d/alsa-utils restart' and everything is fine

---

### Post by brodiepearce on 2007-11-12
> **eqisow said:**
> Edit again: I've tried using envy24control, but I get the error "No ICE1712 cards found." However, "lspci | grep Envy24" returns "00:0b.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)"

Same thing here... I do know that AV-710 support is specifically included in the [ice1724](http://alsa.opensrc.org/Ice1724) driver.  Configuration is easy enough with asound.conf I suppose, still would be nice to have that GUI component though.

---

### Post by cracker on 2008-04-10
I got my optical out working on my envy24 sound card using the config file in the first post, but I have no way of adjusting the volume on it. Is it possible, and if so, how do I do it?

Also, is there any way to resample analog input and pump it out over the optical? I know you can't do that in windows with this card, but I was wondering if maybe there's a software layer capable of pulling it off. I have a TV tuner card that only outputs analog sound, and I'd like to feed it over my optical audio line.

---

### Post by ijustam on 2008-07-21
My card works every now and then so I spend a good deal of time figuring it out.  Finally today I got it so I can have multiple application access it, again since I upgraded to Hardy.

For future reference (be it mine or anyone else):
[LIST]
[*]**/etc/asound.conf** from [http://phoronix.com/forums/showthread.php?t=556](http://phoronix.com/forums/showthread.php?t=556)
[*]**/var/lib/alsa/asound.state** from [http://ubuntuforums.org/showthread.php?p=4359626#post4359626](http://ubuntuforums.org/showthread.php?p=4359626#post4359626)
[/LIST]

Using ALSA.

Both of these are available via Google search/etc, but finding the specific posts got tiresome (there are several AV710/AV-710 threads, but none have a single solution to the problems I had).

---

