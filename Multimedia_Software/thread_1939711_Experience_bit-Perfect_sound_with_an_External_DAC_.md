---
title: "Experience: bit-Perfect sound with an External DAC - (K)ubuntu"
date: 2012-03-12
forum: Multimedia Software
---

### Post by undecidable on 2012-03-12
Below is my experience getting 44.1KHz, 96KHz and 192KHz sound using K(u)buntu. Hopefully it will save someone else some time.

I have a USB DAC (digital to analogue converter) connected, taking input from my Kubuntu 11.04 machine and sending output to pre-amp/amp/speakers.    
I have music (flac) at 44.1KHz/16 bits, 96KHz/24 bits and 192KHz/24 bits.

For the first few days I could only get 44.1KHz from all files. 
Could not work out why.  I tested all usb possibilities, thought the device might be faulty, etc etc. But my old (2006) windows partition (god bless its unrecanting demon heart) behaved correctly without requiring the usual threats.  Also, on various forums I saw others with thesame problem, and some using other distributions (VoyagerMPD) without it.

Eventually discovered Pulseaudio automatically converts all frequencies to some default set in a config file
and this behavior cannot be turned off by man or beast. 

Finally found 2 solutions:

**Method 1 - change Pulseaudio config file default:**

I added a file ~/.pulse/daemon.conf
with the lines
```
	resample-method= speex-float-10
	flat-volumes= no

	default-sample-format = s16be
	; default-sample-format = s24be

	default-sample-rate = 44100
	; default-sample-rate = 96000
	; default-sample-rate = 192000
```
I could then change the default sample rate and bits by a simple edit of this config file.

Note you cannot just leave it at (say) 192KHz or it upsamples all files to this, 
which even on my (admittedly dusty) quad-xeon caused severe stutter
when using the 'good' algorithms, 
.    resample-method= src-sinc-best-quality or
.    resample-method= speex-float-10.

The advantage of this method is I get to still use pulseaudio, with its nice padevchooser.
The disadvantage is every time I change the frequency of the music I have to :
```
a.  edit ~/.pulse/daemon.conf
b.  pulseaudio --kill
c. pulseaudio --start
```


**Method 2 - Use Alsa**

In most music players in the preferences 
you can change the default sink from Pulseaudio to Alsa.
and to change the output device to hw:2,0.

I use the wonderful, nostalgic, Clementine
and there the two changes are made in Tools/Preferences/Playback.

The big advantage of this method is that 
it does not resample the output 
and so I can see the DAC automatically change freqencies when the source sound file changes.

The disadvantage is that as I have 3 'sound cards' 
(onboard sound, Creative Xifi and the USB Dac)
after booting the USB DAC may show up as card1 or card2, depending on the daily karma of the kernel.
To see which it is, do:
```
aplay -l
```

if it is card 1, the output device must be set to 
```
hw:1,0
```
and if it is card 2, the output device must be set to 
```
hw:2,0
```
So I have to remember to check    
and if necessary change the preferences.    

The ony difference I can see between the two methods is the when I do a 
```
cat /proc/asound/card2/stream0
```
pulseaudio has a line:
[INDENT]URBs = 3 [ 64 64 64 ][/INDENT]
and with Alsa the line is
[INDENT]URBs = 2 [ 46 46 ][/INDENT]
Google does not know what an URB is here
(my theory is Unexplained Remote Bottleneck).
If anyone does know I would be interested. 

Note that some disgruntled anarchists on various forums have advocated uninstalling pulseaudio, but this seems unnecessary.

The sound is similar,
with perhaps a slight advantage to direct alsa.
____________________________________________

Setup:
Dell quad Xeon Workstation 670 
connected via high-speed USB bus to Ayre QB-9 DAC,
connected via XLR (balanced) cables to an ARC LS-27 amp,
to PassLabs X250.5 amp, to Paradign Signature S6 speakers.
Finally, magic sound from my music files.

---

### Post by undecidable on 2012-03-13
I discovered URB is:
"The basic idea of the new driver is message passing, the message itself is  called USB Request Block, or URB for short. 	
An URB consists of all relevant information to execute any USB transaction and deliver the data and status back."
from  [http://www.mjmwired.net/kernel/Documentation/usb/URB.txt](http://www.mjmwired.net/kernel/Documentation/usb/URB.txt)

Doesn't tell me why they are different,
but tells me it is probably unimportant.
mc

---

