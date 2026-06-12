---
title: "How do I make HDMI audio work on a nVidia Geforce 210 card?"
date: 2012-09-05
forum: Multimedia Software
---

### Post by bwallum on 2012-09-05
I am having problems getting HDMI audio to work through an Asus nVidia EN210 card. Graphics is fine and HDMI audio used to work fine before upgrade to 12.04 i386 Desktop.

There is a mine of misleading information and I dare say some of it works but I can't fathom which bits are the right bits.

Currently I can see that Alsa sees the hardware using command aplay - l . It reports 4 devices (as it did before):-
--------------------------
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
--------------------------

I have set my /etc/asound.conf file as this:-
---------------------------
pcm.!default {
type plughw
card 0
device 7
}
---------------------------

My /etc/modprobe.d/sound.conf file looks like this:-
---------------------------
#activate this line if card=0
options snd-hda-intel enable_msi=0 probe_mask=0xfff2
#activate this line if card=1
#options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
#activate this line if card=2
#options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xffff,0xfff2
---------------------------

and I have added the following line to the bottom of my /etc/pulse/default.pa file:-
---------------------------
:
:
load-module module-alsa-sink device=plughw:0,7
---------------------------

...all to no avail. Can a more expert soul guide me please and educate me in what each file does.

Thank you

---

### Post by BicyclerBoy on 2012-09-05
There is the nVidia HDMI audio readme.
[http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#](http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#)
Most of all the other info is out-dated or just plain wrong.

Remove the probemask value in the modprobe.d/*.conf file.

Your value is wrong (out of bounds).
Probemask is not necessary for the later alsa/pulse; it was a kludge to hide some devices because alsa could only handle 2 sub-devices & older pulse would only enumerate the first by default & 2 max.
I believe this has been fixed in pulse.

Your mask value is attempting to expose only codec 1.
Then the device numbers get re-arranged (old alsa) & hw:0,3 points to codec 1.

Remove enable_msi=0:
the alsa driver automatically does this for some chipsets (nVidia mobo chipsets).

Debugging:
Have you checked that codec 1 is the right output?
After removing the probemask & running
sudo update-initramfs -k all -u..

speaker-test -l 2 -c 2 -r 48000 -D hw:0,9
speaker-test -l 2 -c 2 -r 48000 -D hw:0,8
speaker-test -l 2 -c 2 -r 48000 -D hw:0,7
speaker-test -l 2 -c 2 -r 48000 -D hw:0,3

You can change 48000 -->44100 if your hdmi rx is an older TV.

dmesg | grep HDA
ls -F /proc/asound/card0

look for any "eld#x.y" files...check the contents.

Once you know the right codec:
/etc/pulse/default.pa should have used **one** of these:
load-module module-alsa-sink device=hw:0,7
load-module module-alsa-sink device=hw:0,8
load-module module-alsa-sink device=hw:0,9

I'm not sure if the newer pulse audio still needs this entry.
Note: it is "hw" not "plughw".

Install/run "pavucontrol" to configure pulse.

---

### Post by bwallum on 2012-09-06
Hole in One! Thank you very much for the insight.

This is what I found:-

There is NO need to modify these files:
/etc/modprobe.d/sound.conf
/etc/pulse/default.pa

There still remains a need for /etc/asound.conf and I found the following worked:-
```
pcm.!default { 
       type plug      
       slave.pcm {          
         type hw          
         card 0          
         device 7      
    }
 }
```Once I had sorted out the above files I ran 
```
sudo update-initramfs -k all -u
```...and joyous sound blasted out of the TV. THANK YOU!

---

### Post by BicyclerBoy on 2012-09-07
The edit in /etc/asound.conf is just over-writing the std default device definition.
There prob no harm in this but shouldn't be mandatory..

Any sound app using alsa device is able to be directly pointed at any of alsa devices. (XBMC, MythTV VLC etc)

But it could be the std version of pulseaudio in 12.04 still does not enumerate all the hdmi devices & over-writing default definition "fixes" that issue.

---

### Post by bwallum on 2012-09-08
Thanks again

It could well be that with a clean install pulseaudio may pick up hdmi devices without any intervention. The system I fixed had run successfully before 12.04 and so had edited files which are no longer needed to be modified.  It is difficult to retrace every change and understand the effect.

However I am much closer to understanding what is going on, thanks to you. I have seen your name in other threads and now know to pay closer attention to them.

I'll be back if all goes pear shaped again! :-)

---

