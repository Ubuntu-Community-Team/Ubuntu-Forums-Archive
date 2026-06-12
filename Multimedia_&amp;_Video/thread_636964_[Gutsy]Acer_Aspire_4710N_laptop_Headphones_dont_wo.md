---
title: "[Gutsy]Acer Aspire 4710N laptop: Headphones dont work"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by ddrake on 2007-12-10
Hello,

 I have installed gutsy (Kubuntu 7.10) on a new acer ASPIRE 4710N laptop (Core2 duo -- see below for the hardware specs). 

I have browsed through the various posts -- tried the suggestions - none worked.
Otherwise, Gutsy is great!


a) I am UNABLE to use the headphones. Instead only the dolby speakers work. The 
builtin microphone too is not supported.

Here are some results:

 lspci -n | grep `lspci | grep -i audio | awk '{print $1}'`
gives:
00:1b.0 0403: 8086:27d8 (rev 02)

I have added the following line to the /etc/modules file for it to load the intel sound drivers.
snd-hda-intel model=laptop

The results after a reboot are negative - there is no auto muting and switch over to the headphones
when the headphones are plugged in. Infact, I doubt if it were activated at all.


Acer specs:Dolby5-certified surround sound system with two built-in stereo speakers
 MS-Sound compatible
 Built-in microphone

Headphone/speaker/line-out jack with S/PDIF support
 Microphone-in jack
 Line-in jack

The KMix utility has only the following:
OutPut Tab with Master & PCM sliders ( I have used Fiesty - the KMIX there had
tabs for input and several sliders include mono/stereo etc. Am I missing something
in Gutsy?)

b) I am UNABLE to use the webcam with attached microphone.
The lsusb command reveals that it is a SU-YIN webcam. I am trying to use
the UVCVIDEO source code --no luck for me --  has anybody succeeded in using the webcam on this Acer
laptop using Gutsy? Kindly share the experiences.

Acer Specs:
Acer Video Conference, featuring:
 Integrated Acer Crystal Eye webcam supporting enhanced Acer PrimaLite technology 
 Optional Acer Xpress VoIP phone 


Kindly share if you have been successful with this brand of acer laptop.

thanks in advance
DD

PS:  To get the sound off the speakers and on the headphones when they are plugged in, I did the following:
a) sudo apt-get install linux-backports-kernel-generic
  This was done to get the realtek sound drivers  to support 'headphone jacksense' 
b) edited the file /etc/modprobe.d/alsa-base  to add the line: 'options intel-hda-snd model=acer'

and rebooted the system.

PPS: The webcam (Acer crystel eye and its microphone) problem has not been solved. Still awaiting a solution
(after installing and trying UVCVideo, camorama, xawtv etc)

PPPS: STATUS on WEBCAM:   Kopete's configure tab and devices subtab is able to activate the webcam so I can view myself. However
there is no way to capture it. Camorama fails saying unable to connect to /dev/video0. The other utility xawtv's options (right click on 
the xawtv screen results in a bunch of options - record avi is one such. Click it to obtain a new menu. When you press start recording movie (avi)
the webcam gets activated (green led goes on) .... but nothing gets stored or can be replayed....

---

