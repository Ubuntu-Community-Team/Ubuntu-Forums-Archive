---
title: "dual hdmi on ubuntu 16.04 sound on 1 tv only at a time"
date: 2017-03-19
forum: Multimedia Software
---

### Post by jimbean on 2017-03-19
i can turn on either hdmi cable {sound } by going into sound properties but there is no option for both hdmi ports  to put out sound simultaneously 
So my problem is: sound on 2 different tv`s hooked up via different hdmi cables at the same time  
the 2 hdmi ports come off of my htpc for my elderly mother :)
and the bios for the htpc is american megatrends

---

### Post by papibe on 2017-03-19
Hi jimbean.

You need a little trick in order to output the same audio out of different outputs.

General steps:
[LIST]
[*]install paprefs
[*]create a new virtual audio device for simultaneous output.
[*]then, select default output in 'Sound' to the new device.
[*]
[/LIST]
[Here]("http://askubuntu.com/questions/78174/play-sound-through-two-or-more-outputs-devices/839627") are the details.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by jimbean on 2017-03-19
installed paprefs
created a new virtual device 
ran pulseaudio -k in terminal
rebooted
(clicked on sound icon top right on menu) 
clicked on simultaneous output  
to built in audio digital stereo (hdmi) built in audio stereo digital stereo (iec958)


the simultaneous output did not mention both hdmi ports ???
 
still only 1 hdm port at a time being enabled

i also checked links in your very very very helpful post 

but im pretty old so it takes longer to sink in :)

i didnt find anything there

---

### Post by jimbean on 2017-03-19
in terminal
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
is there away to force paprefs to use both hdmi ports

---

### Post by papibe on 2017-03-19
Could you post the output of this command?
```
pacmd list-sources | grep -e device.string -e 'name:'
```
Another idea: it could be working but one of the levels is not high enough. If you install pavucontrol:
```
sudo apt-get install pavucontrol
```
Then you can use it to set the levels.

Regards.

---

### Post by jimbean on 2017-03-19
pacmd list-sources | grep -e device.string -e 'name:'
pacmd list-sources | grep -e device.string -e 'name:'
	name: <alsa_output.pci-0000_00_03.0.hdmi-stereo-extra1.monitor>
		device.string = "0"
	name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
		device.string = "1"
	name: <alsa_input.pci-0000_00_1b.0.analog-stereo>
		device.string = "front:1"
	name: <combined.monitor>

sudo apt-get install pavucontrol


sudo apt-get install pavucontrol
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pavucontrol is already the newest version (3.0-3build1).
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.

---

### Post by jimbean on 2017-03-19
pavucontrol
all sound devices are set to 100 percent
but while testing ports
the headphone jack and 1 of the hdmi ports are linked together
so if i could get rid of the headphone jack port driver and use the other hdmi port ????

---

### Post by walterav on 2017-03-19
Are you running mirrored screens or individual screens? Are you using onboard intel HD graphics or AMD/Nvidia please post the output of "lspci"?

---

### Post by jimbean on 2017-03-25
intel graphics if i run mirrored monitors it works 

if i run individual screens it wont  work

i try to run google chrome for my tvs

and google comes up on 1 tv and the sound comes up on the other 

if i run the tvs mirrored the tvs both show the same thing

and the sound comes up but only on 1 tv at a time on the  hdmi ports

sorry for late reply thanks again

---

