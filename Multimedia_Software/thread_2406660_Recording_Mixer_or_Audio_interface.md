---
title: "Recording: Mixer or Audio interface?"
date: 2018-11-23
forum: Multimedia Software
---

### Post by spencer2 on 2018-11-23
Hello: 
I'm looking for some general help & suggestions about Ubuntu recording software, the associated hardware, etc..

I'm doing some podcasting (just like everyone else) & am having some issues getting the quality & setup that I would like & that does the job.

Currently, I have a behringer q1202usb going into my ubuntu studio & am using Audacity.

I'm still doing some learning, but it seems as though with the mixer I currently have, I only have 2 bus usb channels. I have to pan stuff & mess with lots of post-recording editing -- plus all that doesn't really solve the challenge of having more than 2 people on. I want 4 usb channels. Beyond just the challenge of the mixer-usb issue; I also am not super clear on all the differences between ALSA/Jack & the compatibility with many of the software programs that seem intended to work with windows or mac.

I'm really looking for tips: methods that others use: some of the workarounds that others have done when in a similar situation to me. I know there are others out there who know this stuff better than me & I'm hoping some of them will be benevolent here.

Thank you very much for any help & tips & such.

---

### Post by Autodave on 2018-11-23
Not real familiar with podcasting, but I do use Audacity to record 18 channels from an Allen & Heath mixer board via USB cable.  I do NOT use Jack and hopefully will never have to.  I just prefer to open a program and figure out how to use it in a few minutes rather than spending an hour or more trying to get the basics figured out.

Are you saying that you can only get 2 channels from the mixer?

---

### Post by spencer2 on 2018-11-26
I think I'm only getting 2. To be honest; I'm still doing some learning. It seems as though I only have 1 set of L&R outputs to audacity. I'm trying to figure out how to do simultaneous multi-track recording without having to pan my behringer mic strips all the way L or R.
I need to be able to record 2 or more w/out having each person panned all the way to 1 side.

How are you getting simultaneous multi-track recording from Audacity?

---

### Post by Autodave on 2018-11-26
I am using a USB cable.  Does your mixer have a USB output?  If so, connect it to the PC, restart the PC, go into Audacity -> Edit -> Preferences -> Devices -> Recording.  There you should get a drop down showing the mixer.  It will probably also ask for how many channels you want.  Make sure what the mixer is capable of sending.

---

### Post by nik.charles on 2018-11-29
Agree that for podcasting need 4 channels of audio output

That behringer mixer will only have 2 channels in and out on USB
recording using audacity direct from hardware (ALSA) is limited to one audio device and number of channels available

There a lot of used 4+ channel pro-audio USB and PCI hardware at good prices that will work well at 48kHz
(PCI-e only if you got budget for Digigram or Audioscience)
Many devices may not have good preamps for plugging in microphones direct, 
but you can use mixer to preamplify microphones and use most multichannel devices at line level for recording 
Should be possible to record in just ALSA with Audacity

You may be able to use onboard analog audio device for 2 additional input and output channels
there is possibilty of ground loops (hum) connecting usb and analog cable, may need ground loop isolator
also have to be careful connecting mixer audio to pc, preferably use an attenuator so audio from mixer does not overload and damage pc line input

suggest you check out the [Ubuntu Studio Audio Handbook]("https://help.ubuntu.com/community/UbuntuStudio/AudioHandbook") for information about pro-audio using JACK for mutichannel recording
A lot of the content is for Musicians, but the sections "tools for DJs" "Internet DJ Console" "Audacity" and "Ardour" may help

I used Internet DJ Console running in JACK for a few years for live shoutcast/icecast broadcasting
more than enough features to record a podcast to stereo
Ardour if you really want a multitrack recording

JACK audio has flexibility for connecting, processing and recording multiple audio streams and devices
and can get as complex as wiring up a real-life recording studio

---

### Post by Autodave on 2018-11-29
I agree with nik.charles about Ardour and Jack.  However, beware that the learning curve is VERY steep: especially on Jack.  Audacity is about as simple as you can get.

---

