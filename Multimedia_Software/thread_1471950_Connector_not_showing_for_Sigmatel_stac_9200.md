---
title: "Connector not showing for Sigmatel stac 9200"
date: 2010-05-03
forum: Multimedia Software
---

### Post by Graemej on 2010-05-03
Hi all,
I am a new user having moved from Windows about a week ago. I have tried to ask this question before but was not posting in the right place due to my newness. I have looked hard for a solution and learned a lot over the last week. In fact enough to understand how much I don't know.

I do not have a connector available to switch between line and mic inputs and would like help to set them up please.

I installed 10.04 RC to try Ubuntu and had a separate control for line and mic but now only as the screenshot. The first picture is of how I remembered my RC install and is not my original screenshot. The second is how my system is now.



My computer is a Dell Inspiron E1505
My sound card a Sigmatel stac 9200
My operating system Ubuntu Lucid 10.04 LTS

Here are some data from my system:
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9200
Codec: Conexant ID 2bfa

I have added this line to /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=dell-m25

Off topic but if someone could mention it. What is the difference between "capture" and "line & mic" controls.
also How can I insert code into those scrollable boxes titled Code: (I'll ask this in beginners if not appropriate here)

I would really appreciate help with this as I use the card for software defined radio and it just won't work without line access.

---

### Post by Rumpty on 2010-05-19
The Sound Preferences may have changed slightly going from 9.10 to 10.04? If you go to the Hardware tab, select Analog Stereo Duplex instead of Analog Stereo Output, options change in the Input tab.

Select Input tab. In the box Choose a Device for Sound Input, select Internal Audio Analog Stereo, and click on the button at the left of this selection. Connector facility should now appear just above.

---

### Post by Graemej on 2010-05-26
Thanks Rumpty for your response. Afraid that did not work either. I think I will have to live with this one.

Cheers.

---

