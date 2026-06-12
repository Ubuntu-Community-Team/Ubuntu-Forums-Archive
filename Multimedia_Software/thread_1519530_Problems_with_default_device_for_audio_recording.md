---
title: "Problems with default device for audio recording"
date: 2010-06-28
forum: Multimedia Software
---

### Post by pjvv1 on 2010-06-28
Dear friends,

I have detected some problems when I try to record  sound in my Kubuntu 10.04 system.

The problem is that the  "default" device for audio recording does not work but I have to select  another device to do so. I always selected the "default" device for  audio recoding but currently I  have to select hw:0,2 device. 

Another odd thing is that  different programs show me different device. For example, Audacity shows  me that I have the following audio recording devices:

- HDA  Intel: ALC888 Digital (hw:0,1)
- HDA Intel: ALC888 Analog (hw:0,2)
- spdif
- default

The  only one that works is hw:0,2.

But arecord shows me (when I  execute "arecord -L") the following:

null
    Discard all  samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC888 Analog
    Default Audio  Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
     Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888  Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
     HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and  Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel,  ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
     HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center,  Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front,  Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
     HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output

Finally,  in KDE system preferences for audio I get that I have 2 different audio  devices for audio recording:

- HDA Intel (ALC888 Analog): it is said that it will try first  x-phonon (CARD=0, DEV=0) and, if the latter does not work, it will try  plughw (CARD=0, DEV=0)
- HDA Intel (ALC888 Digital): it is said that  it will try first x-phonon (CARD=0, DEV=1) and, if the  latter does not work, it will try plughw (CARD=0, DEV=1)

Where is  the hw:0,2?? and how can I set the alsa system to use hw:0,2 as the  default device for audio recording??

All of that would not be a  problem but I also  have an ubuntu 9.04 installed on a  virtual machine (by using virtualbox) and audio recording doesn't work  there. I suppose that it is becase of the virtual sound card is using  default devices for playing and recording audio.

I must say that  audio playback works fine in both host and guest systems. It is just  audio recording.

Thanks in advance.

---

### Post by cchhrriiss121212 on 2010-06-28
The command to use to show recording devices is arecord -l (small "l" is important). You can see what it will be called by this example using my card:
```
chris@chris-desktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: M44 [M Audio Delta 44], device **0**: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #**0**: subdevice #0
```
The name will be "hw:Device#,Subdevice#", so in my case the recording device is hw:0,0.

I don't really understand what the problem is here, is it causing problems to set the recording device to hw:0,2 instead of default? Once you set it up once, Audacity should remember your settings and you can forget about it.

---

### Post by pjvv1 on 2010-06-29
Thanks for your answer.

My problem is that I have a virtual machine with ubuntu 9.04 as guest and sound recording does not work. 

I suppose that it is due to the virtual sound card for the guest system uses "default" alsa device. As the "default" device for audio recording does not work in the host system, the guest can't record sound.

Is there any way to change default device for audio recording in ALSA?

---

### Post by cchhrriiss121212 on 2010-06-29
I understand now. Found a promising fix [here]("http://www.linuxquestions.org/questions/ubuntu-63/how-do-you-change-the-default-sound-card-in-k-ubuntu-499520/"), it is an old one but it should still be applicable.

---

### Post by pjvv1 on 2010-06-29
I couldn't make it work.

I tried to create a .asoundrc file in my $HOME directory with the following content:

pcm.!default {
  type hw
  card 0
  device 2
}

And it seems to work a little bit better but when I start the virtual machine I get a message that says that sound is not working fine.

I don't know what to try next. I really need to capture sound in my virtual linux machine (I didn't have troubles before).

Anyway, thanks for your help. Any more ideas?

---

### Post by cchhrriiss121212 on 2010-06-29
So the default card is not the issue then?
What is it you are doing/using with your VB Ubuntu sound?
What message are you getting?

---

### Post by pjvv1 on 2010-06-29
I get the following VirtualBox message when I start my virtual linux:

 p, li { white-space: pre-wrap; }  Some audio devices (PCM_out) could not be opened. Guest applications generating audio output or depending on audio input may hang. Make sure your host audio device is working properly. Check the logfile for error messages of the audio subsystem.

---

