---
title: "hda-intel iec958 multiplex solution"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by mooter on 2007-02-09
Hi!

For casual use of sound and video, I'm using the SPDIF COAX out of my ICH7 HDA Intel Stac92xx card.
Now, I tinkered with a lot of .asoundrc configurations and of course came up with many different things.  After getting it almost just right, I still had a problem of not being able to multiplex (play souds from multiple sources)

Example:  The GTK Login window sound would play, but not the System Sound Log in sound after that
(1st there is the GTK Login sound which you can choose in Admin->Login Window->Accessibility, 2nd is the next Login sound which is in Preferences->Sounds)

I actually got both to play in one config but the 1st login sound had to finish before moving onto the next one.

Another Example would be The GTK Login sound would play, not the System sounds, but still be able to play a Dolby digital movie in surround using AC3 pass through.

So, I struggled to get all of these to play together seamlessly, and I think I've found it combining a couple settings from a couple different places, which, I got from rereading the Comprehensive Sound Solutions guide again (which I avoided because I did not feel like reading through 49 pages to try a bunch of different things.

So, here, if you are having problems, either erase everything on your .asoundrc and /etc/asound.conf files or comment what you have in them out.  (I've kept my asound.conf file empty and only used the .asoundrc)

If this is what you get when you type "aplay -l":

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

then this might help:


#########################################################
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

#pcm.!default {
#        type plug
#        slave.pcm "surround51"
#        slave.channels 6
#        route_policy duplicate
#}
########################################################
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
}

#######################################################
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the #analog output, this is the option you want. 


#pcm.analog {
#    type plug
#    slave analog_slave;
#}

#pcm_slave.analog_slave {
#        pcm surround51;
#        format S32_LE;
#}

#_____________________________________________________________________________________
# The top level shared pseudo device, with both PCM and CTL interfaces
# The device names "default", "dsp0", "mixer0" have conventional meanings.

# The top level shared pseudo device, with both PCM and CTL interfaces
# The ALSA default is "!default", but many programs like XMMS and aoss
# assume "dsp0" as default name for PCM and "mixer0" for CTL.

# Amazingly, XMMS has problems if one defines 'pcm.dsp0' to be
# 'plug' for 'pcm.asym0' and not directly as 'asym0'.

pcm.!default            { type                  plug;
                          slave.pcm             "dmix0"; }
ctl.!default            { type hw; card 0; }

pcm.dsp0                { type                  plug;
                          slave.pcm             "dmix0"; } 
ctl.dsp0                { type hw; card 0; }
ctl.mixer0              { type hw; card 0; }

########################################################################

# Buffering (period time defaults to 125000 usecs).

# Size of period, expressed either in usec or byte units:
#   period_time USECS
#   period_size BYTES

# Size of buffers, expressed either in period, usec, or byte units:
#   periods     PERIODS
#   buffer_time USECS
#   buffer_size BYTES

# The ALSA docs have examples with 'period_time' set to 0,
# when 'period_size' and 'buffer_size' are used instead,
# but this can cause trouble in later releases of ALSA.

# For OSS compatibility, 'period_size' and 'buffer_size'
# should be powers of 2. Also, many cards cannot accept
# a 'period_size' much greater than 4096, so 4096 is safe.
# On my VIA 8233A, any value for 'period_time' greater than
# 85333 usecs (precisely!) causes hiccups in sound output.
# Why? At 48kHz, 85333 usec are are just over 4096 bytes/channel.

pcm.dmix0               { type                  dmix;
                          ipc_key               13759;

                          slave.pcm             "hw:0,0";
                          slave.channels        2;

                          slave.rate            48000;
                          slave.period_size     4096;
                          slave.buffer_size     16384;

                          slave.period_time     84000;
                          slave.buffer_time     340000;

                          # Map only the first two channels
                          bindings.0            0;
                          bindings.1            1; }






So that's working for me.  I only use my Coax , my analog out is coming out of ym Emu1820m which isn't supported yet but I only use it professionally so I need windows to do that anyway.

So now you should be able to multiplex with thexception of not being able to have 2 dolby digital sources playing at the same time.  That may be a technical thing, it may be ab;le to be fixed with a config, I don't care.  I mean, I don't need to listen to music while I'm watching a movie, you know?

I hope that helps anyone else.

---

