---
title: "[SOLVED] Controlling a DCT700 cable box"
date: 2008-03-02
forum: Mythbuntu
---

### Post by purplerhino on 2008-03-02
My mythtv computer has been out of service for almost 3 weeks now, and I just have no other trouble shooting ideas, I'm completely stuck.  All the searching I've done, I only seem to find people having problems with the 0 key.  I am having problems with every key.

I bought a dual headed serial IR blaster from irblaster.info.  I'm just trying to get one box working before I try tackling two.

I am using mythbuntu.  I followed these documents

[https://help.ubuntu.com/community/InstallLirc/Gutsy](https://help.ubuntu.com/community/InstallLirc/Gutsy)
[https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script](https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script)

I've run setserial /dev/ttyS0 uart none, loaded lirc_serial module , lircd is running, and when I try and

irsend SEND_ONCE DCT700 info

or power, or numbers, or any key at all, with the irsend command or the perl or python change channel scripts, I get no errors, but the box does not respond.  I have both blasters taped right above the eye, and I've repositioned them a thousand times.  I've tried it on two seperate DCT700 boxes.  I did the camera trick where I watch the blasters when I send an irsend command, and I saw the purple light.  So the blasters work, something is sending, but it's not have any effect.

I live in Chicago and have RCN cable.  Usually these DCT700 howtos are associated with Comcast.  Could the boxes be different?  They don't look special.  I really am out of ideas and pleading for new ideas to try.

here are my config files:


lircd.conf


```
# this config file was originally generated
# using lirc-0.6.6(serial) on Fri Mar 28 22:46:44 2003
# modified by hand on Sunday Jul 17 00:12:00 2005
#
# contributed by rob scullion
# based on the DCT2000 file contrib'd by shane bradley
#
# brand:                       Motorola
# model no. of remote control: ? - Comcast badged
# devices being controlled by this remote: DCT2524/1612
#
# Note: The "ON DEMAND" button on the Comcast
# badged remote just sends a "1" followed by
# an "ok/select" and is thus not included in
# this config file.
                                                                                  
begin remote
 name  DCT700
  bits             16
  flags SPACE_ENC|CONST_LENGTH
  eps              30
  aeps            100

  header         9036  4424
  one             556  2185
  zero            556  4424
  ptrail          556
  gap          100025
  toggle_bit        0
 

      begin codes
          power                    0x000000000000AFF9
          rew                      0x00000000000087F7
          play                     0x00000000000027FD
          ffwd                     0x00000000000047FB
          stop                     0x000000000000C7F3
          pause                    0x00000000000007FF
          rec                      0x00000000000073FC
          skipback                 0x000000000000C3F7
          mydvr                    0x00000000000043FF
          live                     0x00000000000083F0
          pageup                   0x000000000000A3F3
          pagedown                 0x00000000000023FB
          a_lock                   0x00000000000097F6
          b_day-                   0x00000000000063FD
          c_day+                   0x000000000000E3F5
          up                       0x000000000000D3F6
          down                     0x00000000000053FE
          left                     0x00000000000093F1
          right                    0x00000000000013F9
          ok/select                0x00000000000077F8
          guide                    0x000000000000F3F4
          info                     0x00000000000033FA
          menu                     0x00000000000067F9
          exit                     0x000000000000B7F4
          help                     0x000000000000B3F2
          last                     0x00000000000037FC
          vol+                     0x0000000000004FF3
          vol-                     0x0000000000008FFB
          mute                     0x0000000000000FF7
          fav                      0x00000000000057FA
          ch+                      0x0000000000002FF5
          ch-                      0x000000000000CFFD
          1                        0x0000000000007FF0
          2                        0x000000000000BFF8
          3                        0x0000000000003FF4
          4                        0x000000000000DFFC
          5                        0x0000000000005FF2
          6                        0x0000000000009FFA
          7                        0x0000000000001FF6
          8                        0x000000000000EFFE
          9                        0x0000000000006FF1
          0                        0x000000000000FFFF
          tv/vcr_input             0x000000000000D7F2
          hdzoom_enter             0x000000000000FDFC
          pnp-swap                 0x0000000000003BF2
      end codes
 
end remote
```


hardware.conf:


```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Home-brew (16x50 UART compatible serial port)"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_dev lirc_serial"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
```


/etc/modules.d/lirc:

```
#COM1 equivalent, /dev/ttyS0
options lirc_serial irq=4 io=0x3f8
#COM2 equivalent, /dev/ttyS1
#options lirc_serial irq=3 io=0x2f8
```

---

### Post by purplerhino on 2008-03-04
A got a solution from the mythtv users mailing list.  

> My first attempt
left me with a lircd that accepted commands but would not communicate
with the STB (I couldn't verify if there was a signal present or not).
 I compiled lirc again, changed the build option 'software carrier' to
on, which fixed my problem.

So I recompiled lirc from source and installed it over mythbuntu's, and it worked fine... Considering how integral Lirc is with mythtv, I assumed that it would be a bit fairly well tested and reliable... You know what happens when you assume!

---

### Post by majoridiot on 2008-03-04
> **purplerhino said:**
> or power, or numbers, or any key at all, with the irsend command or the perl or python change channel scripts, I get no errors, but the box does not respond.  I have both blasters taped right above the eye, and I've repositioned them a thousand times.  I've tried it on two seperate DCT700 boxes.  I did the camera trick where I watch the blasters when I send an irsend command, and I saw the purple light.  So the blasters work, something is sending, but it's not have any effect.

if you are getting the transmitter to flash, then it sounds like things are working... i know it sounds very
basic, but in my experience set top boxes can be *extremely* picky about the placement of the
transmitter in relation to the sensor window.

in these situations, i've found it best to write a simple script to cycle the power on and off and let it
run while i moved the transmitter around by hand.  this script should work for you to try that:

```
#!/bin/bash
while [ 1 ]
do
    irsend SEND_ONCE DCT700 power
    sleep 1
done
```

save it as "powertest".  then make it executable:

```
$ chmod +x powertest
```

and execute it with:

```
$ ./powertest
```

this will send a power command once a second, allowing you to hopefully find the sweet spot
for the transmitter.

---

### Post by bthoward on 2008-05-13
So for anyone else who has solved this I have another question...  I've got the thing working now so that I can change channels with my script and it works in myth but when I'm using the scan channels feature it doesn't use the external script to change channels.  Anyone have any ideas here?  If it works perfectly when I use the front end why would the backend config tool not be able to do it?  Right now I have the other tuners all disabled so it shouldn't be using the tuner in the card at all and should be going 100% off the composite input.

---

### Post by majoridiot on 2008-05-13
> **bthoward said:**
> So for anyone else who has solved this I have another question...  I've got the thing working now so that I can change channels with my script and it works in myth but when I'm using the scan channels feature it doesn't use the external script to change channels.  Anyone have any ideas here?  If it works perfectly when I use the front end why would the backend config tool not be able to do it?  Right now I have the other tuners all disabled so it shouldn't be using the tuner in the card at all and should be going 100% off the composite input.

i may be wrong, so please verify this... but i do not believe the scan function is intended to work the way
you are trying to use it.  i think it is intended for dvb cards, etc. and not for use with pvr-style cards
or firewire tuners, etc.

instead of using the scan function, set up a schedules direct account, configure your line-up there,
and then config the channels and bind them to the tuner in steps 3 and 4 of backend setup.

once you have run mythfilldatabase, you should have good channel info in your db to tune and record with.

---

