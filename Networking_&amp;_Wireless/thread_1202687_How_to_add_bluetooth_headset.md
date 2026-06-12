---
title: "How to add bluetooth headset"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by jerez76 on 2009-07-02
If you can get any sound of your headset is not working the newer version of pulseaudio and bluez does work which is on Fedora 11.

if you are using Jaunty or Gloria should should try this..

instead of using the bluez device set up the little bt icon on your panel...
(if you have it paired via bluez just delete the pair up.) 

do this first

$ hcitool scan
Scanning ...
        00:33:44:DD:EE:FF       BT81

$ gedit ~/.asoundrc

***add this to new file(file doesnt exist). Highlight and copy the MAC address of your headset. 

pcm.btheadset {
        type bluetooth
        device 00:33:44:DD:EE:FF
        profile &#8220;auto&#8221;
}

***now add device to bluez setup device

$ hciconfig hci0 voice 0x0060
$ pactl load-module module-alsa-sink device=btheadset
$ pactl load-module module-alsa-source device=btheadset

$ aplay -D btheadset -f s16_le /usr/share/sounds/ubuntu/stereo/dialog-question.wav

needed for PulseAudio
$ sudo apt-get install paprefs paman padevchooser

You should be able to select it on the pulse audio manager.
PulseAudio Sound & Video->PulseAudio Device.
left Click PulseAudio taskpanel incon...under menu, choose "Manager"
Under "Sinks" you should see an entry for "alsa_output.btheadset".
this worked with the older version on bluez 4.32 and pulseaudio so some steps can be skipped with fedora...

if you get a 
Connection failure: Connection terminated
Failure: Timeout
or any other error.

do 
$ pulseaudio --kill
$ pulseaudio --start

Audio works Skype but the mic with kills the pulseaudio connection. I am using the laptop mic since I am also using the webcam. 

this was done on Ubuntu 9.04 ad Linux Mint 7

ref. [http://forums.overclockers.com.au/showthread.php?t=780054](http://forums.overclockers.com.au/showthread.php?t=780054)

---

### Post by jerez76 on 2009-07-02
REQ: Jaunty BLUEZ 4.42 & PulseAudio update!

[http://www.bluez.org/download/](http://www.bluez.org/download/)
[http://www.pulseaudio.org/](http://www.pulseaudio.org/)

---

### Post by jerez76 on 2009-07-03
I updated bluez to 4.43 along with the other tars available on their url. There is no change with audio loading or mic improvements.

PulseAudio 0.9.14 needs to be updated to 15 which will automatically pick up bt device.(seen on FC11) will check later lol happy my ps3 keyboard is working :P

---

### Post by siraf on 2009-07-03
hey man! Great tutorial.

I was just wondering if you could get more in-depth on compiling pulse in Jaunty? 
I tried to get it working, but I can't seem to get the bluetooth headset to connect properly when I do.

Thanks

---

### Post by jerez76 on 2009-07-08
there are a few libs that are required to compile against jaunty but a quick and dirty fix for me was to add
deb [http://*cz.archive.ubuntu.com/ubuntu](http://*cz.archive.ubuntu.com/ubuntu)* karmic main 
to 
/etc/apt/sources.list

Opened Synaptic PackMan searched for pulseaudio updates

lol

here is the how to add and remove just in case you start seeing all these updates

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

here is the ref. for the deb packages

[http://packages.ubuntu.com/karmic/sound/pulseaudio](http://packages.ubuntu.com/karmic/sound/pulseaudio)

click on Download pulseaudio link and you'll see the mirror.

---

