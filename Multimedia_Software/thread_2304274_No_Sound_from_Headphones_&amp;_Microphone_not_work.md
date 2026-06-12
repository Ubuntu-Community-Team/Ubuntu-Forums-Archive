---
title: "No Sound from Headphones &amp; Microphone not working"
date: 2015-11-25
forum: Multimedia Software
---

### Post by aem0512 on 2015-11-25
Still having trouble getting everything to work properly on my ASUS F555U. I've resolved most of my issues but the system microphone isn't working and there is no sound from the headphones. Both work on the Windows partition.

Anyway, I've determined that I have Realtek ALC256 and Intel Skylake HDMI from the command:
cat /proc/asound/card0/codec* | grep Codec

On my Windows partition it's referred to as the Realtek HD Audio Codecs. 

I am getting some errors at startup time as shown in the photo below:
[ATTACH=CONFIG]265771[/ATTACH]

---

### Post by Yellow Pasque on 2015-11-25
What version of Ubuntu are you running? Since you have very recent hardware, you might want to try the latest sound drivers: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by aem0512 on 2015-11-25
I am running Ubuntu 15.10 with kernel 4.3 so as to have the most recent possible drivers. I already tried upgrading alsa as suggested in that link but it didn't work. Any other suggestions?

---

### Post by Yellow Pasque on 2015-11-25
The error messages in your screenshot could be related to this bug: [https://bugs.freedesktop.org/show_bug.cgi?id=92685](https://bugs.freedesktop.org/show_bug.cgi?id=92685)

That doesn't explain loss of sound though. See if you can get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by aem0512 on 2015-11-25
"Your ALSA information is located at [http://www.alsa-project.org/db/?f=20a5b8e70e1338113539ab56578dcb7b078c1382](http://www.alsa-project.org/db/?f=20a5b8e70e1338113539ab56578dcb7b078c1382)


Please inform the person helping you."

Thanks for your help so far!

---

### Post by Yellow Pasque on 2015-11-27
Have you tried adjusting headphone volume in alsamixer?:
```
alsamixer
```

```
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 0 [0%] [-65.25dB] [off]
  Front Right: Playback 0 [0%] [-65.25dB] [off]
```

As for the microphone, it is not even exposing a control and it is not connected to other pins:
```
Node 0x1a [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x90a70130: [Fixed] Mic at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
```

It's a long shot, but hdajackretask utility may be able to help you if you set that pin (0x1a) to microphone.
```
sudo apt-get install alsa-tools-gui
echo autospawn = no >> ~/.config/pulse/client.conf
killall pulseaudio
hdajackretask
pulseaudio -D
```

More likely, you will have to file a bug to get your sound fixed: [https://bugzilla.kernel.org/buglist.cgi?component=Sound%28ALSA%29&list_id=672181&product=Drivers&resolution=---](https://bugzilla.kernel.org/buglist.cgi?component=Sound%28ALSA%29&list_id=672181&product=Drivers&resolution=---)

---

### Post by aem0512 on 2015-11-27
I'm trying to install the Realtek driver for HD audio, downloaded directly from realtek. I have the build-essential package installed and I have patch installed (now).

Following their instructions, I extracted the driver files, entered the appropriate directory, typed:

sudo ./configure --with-cards=hda-intel
sudo make

But then I got some errors:
/home/me/Installs/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/info.c: In function &#8216;snd_info_version_read&#8217;:
/home/me/Installs/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/info.c:1065:22: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
       "Compiled on " __DATE__ " for kernel %s"
                      ^
cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/home/me/Installs/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/info.o' failed
make[3]: *** [/home/me/Installs/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/info.o] Error 1
scripts/Makefile.build:403: recipe for target '/home/me/Installs/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore' failed
make[2]: *** [/home/me/Installs/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore] Error 2
Makefile:1378: recipe for target '_module_/home/me/Installs/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa' failed
make[1]: *** [_module_/home/me/Installs/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.3.0-040300-generic'
Makefile:167: recipe for target 'compile' failed
make: *** [compile] Error 2

In the REAME file it says "If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux." But...I'm not sure what that means. Am I supposed to rename my system's directory? That seems like a bad idea, but what do I know.

---

### Post by Yellow Pasque on 2015-11-27
I would not bother with the Realtek Linux driver. It often lags behind the kernel to the point where it won't build, and it usually makes things worse if it changes anything.

---

### Post by aem0512 on 2015-12-20
Ok, well I have a few updates on this. I decided to give Ubuntu Mate 15.10 a try and I am glad I did. I have the same issues with the Mate edition that I did with the Unity edition, however, I have an option in the sound settings to set my output connector from "speakers" to "headphones". That is the only way I have been able to get my headphones to work properly thus far, however it is a bit annoying. Is there any way around doing this manually? 

Also, I've tried most of the sound profiles including "Analog Stereo Duplex" and "Analog Stereo Output" with similar results.

Still no luck with the microphone...

---

### Post by Yellow Pasque on 2015-12-21
REmove the alsa-dkms package and reinstall kernel image for good measure:
```
sudo apt-get remove alsa-dkms  #I think that's the name of the package, but don't quote me on that and I'm about to leave for work
sudo apt-get install --reinstall linux-image-`uname -r`
```

---

### Post by aem0512 on 2015-12-21
I apologize for making things confusing. I actually edited my above reply because I had new information. Thanks again for your help. Do you have any suggestions regarding the above?

---

### Post by vincenzo.coco on 2016-05-14
Hi, i have the same problem on ASUS F555U.
If I want sound from headphones I have to open alsamixer and manually change the sound from it everytime that i reboot the laptop.
In normal way I hear the sound from speakers even with headphone's jack plugs in.
Can I change that? Thanks

---

