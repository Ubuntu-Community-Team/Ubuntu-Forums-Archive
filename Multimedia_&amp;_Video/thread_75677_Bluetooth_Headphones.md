---
title: "Bluetooth Headphones"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by webdwarf on 2005-10-14
I was recently given a pair of Blueant Bluetooth Stereo Headphones ([www.blueant.com.au](www.blueant.com.au)) which double as stereo headphones for the PC (basically its another soundcard, sortof) but I have no idea how to get it work. I am using Kubuntu but am willing to try Gnome if its going to have more luck.

Basically my question is, are bluetooth audio devices supported yet? and if so, how does one go about setting them up?

---

### Post by gcain on 2005-11-05
I have a very similar question....

Has anyone been able to get *any* bluetooth headphones/earphones/speakers to work with any Linux distrobution; preferably Ubuntu.
The once that use their own bluetooth dongle in the the audio jack obviously don't count.

I just want to know if it can be done before I shoot out and buy myself a pair since they are a little exe.

---

### Post by Stimpy on 2005-11-17
Yes, it's possible :)
All you need an alsa kernel driver which uses bluez to reach the headset.
The [Bluetooth-alsa Project]("http://bluetooth-alsa.sourceforge.net/") provides everything you need.

For Ubuntu Breezy you also need the following packages:

cvs
checkinstall
automake1.7
gcc-3.4 
libbluetooth1-dev
libasound2-dev
linux-headers-uname -r

follow the instructions on the Bluetooth-Alsa Website and make sure you use automake1.7 und gcc-3.4 (gcc-4.0 is usually installed, so you have to do: EXPORT CC="/usr/bin/gcc-3.4")

I also had to move the Kernel-Module (mv /home/name/tmp/src/btsco/kernel /lib/modules/2.6.12-9-686/) in order to load it with modprobe snd_bt_sco

Works great with both my Logitech and Nokia Bluetooth Headsets.

Stimpy

---

### Post by gcain on 2005-11-18
Hi Stimpy,

I actually found the bluetooth-alsa project a few hours after posting that message.

Everything seemed to install properly but when I tried to use it to connect to my headset it seemed to timeout trying to connect to SDP server. I can't remember the details now but am willing to try again if you think you could be able to help...

I'm pretty keen to get it working, bluetooth headphones are a great idea!

---

### Post by simbot on 2005-12-16
I too have a pair of said blueant headphones, and using the bluetooth-alsa project I have successfully played, and recorded audio using the sco capibility (8kHz), but i've been unable to make the A2DP capibility connect. I get something like:

len=2048
Header size=28
Sample Rate:44100
Channels:2
Using address: 00:0A:56:00:B5:91
Found A2DP Sink

Found A2DP Sink at the destination
Connected [imtu 672, omtu 672, flush_to 65535]

couldn't get avdtp_discover
Sent the Stream End Point Discovery Command

This is with the CVS of the alsa-bluetooth, Bluez 2.22 and Linux kernel 2.6.14.3

---

### Post by tubo on 2006-06-30
i pretty much followed the instructions on the bluetooth-alsa homepage and git the a2dp usermode driver working with XMMS with a Plantronics Pulsar 590a headset -- quality rocks.

Emanuel

---

### Post by Piposh on 2007-07-10
I followed the guide and it works for me too, very good quality!
(I'm using Inno BT3070)

---

### Post by thomas7.10 on 2008-03-01
I'm about to buy such a Plantronics Pulsar 590a and i'm wondering if it works with skype and Ekiga. Does anyone has experience with that?

Thomas

---

