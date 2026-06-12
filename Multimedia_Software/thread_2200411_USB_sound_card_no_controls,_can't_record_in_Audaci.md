---
title: "USB sound card: no controls, can't record in Audacity"
date: 2014-01-19
forum: Multimedia Software
---

### Post by Bucky Ball on 2014-01-19
Hi all,

I have been testing 14.04 and trying to get a Digidesign MBox 2 Mini, working to no avail. The progress of that can be viewed  [here]("http://ubuntuforums.org/showthread.php?t=2199061&page=2&p=12904347#post12904347").

Back in Xubuntu 12.04 again and giving it another go. I've been trying on and off to get this working for two or three years following the instructions [here.]("http://www.zamaudio.com/?p=97&cpage=4")

Following this:

```
git clone https://github.com/zamaudio/alsa-driver.git
cd alsa-driver
git checkout mbox2
cd alsa
./gitcompile
sudo make install
```

... the Mini lights up and I can plug guitar and headphones into it and get crystal clear audio. This is what I get from dmesg after plugging in the MBox 2 Mini:

```
[22803.570371]
[22827.054546] usb 2-1.2: new full-speed USB device number 8 using ehci_hcd
[22827.179891] usb 2-1.2: config 1 interface 2 has no altsetting 1
[22827.179902] usb 2-1.2: config 1 interface 3 has no altsetting 1
[22827.179911] usb 2-1.2: config 1 interface 4 has no altsetting 1
[22827.179920] usb 2-1.2: config 1 interface 5 has no altsetting 1
[22827.185632] ALSA quirks.c:573 usb-audio: Sending Digidesign Mbox 2 boot sequence...
[22827.686547] ALSA quirks.c:584 usb-audio: device not ready, resending boot sequence...
[22828.190331] ALSA quirks.c:584 usb-audio: device not ready, resending boot sequence...
[22828.694092] ALSA quirks.c:584 usb-audio: device not ready, resending boot sequence...
[22829.197947] ALSA quirks.c:584 usb-audio: device not ready, resending boot sequence...
[22829.701755] ALSA quirks.c:584 usb-audio: device not ready, resending boot sequence...
[22830.205456] ALSA quirks.c:584 usb-audio: device not ready, resending boot sequence...
[22831.710795] ALSA quirks.c:609 >usb-audio: Digidesign Mbox 2: 24bit 48kHz
```

... but when I open alsamixer and choose that device I have no controls (see first attached pic, and yes, device and sample rate appear to be correct in Audacity, although I think it's the device that it can't communicate with rather than the frequency being wrong, even though Audacity recognises the MBox and it can be assigned). This confirms the lack of controls, from my alsa info:

```
!!-------Mixer controls for card 2 [M2]

Card hw:2 'M2'/'Digidesign Mbox 2 at usb-0000:00:1d.0-1.2, full speed'
  Mixer name	: ''
  Components	: 'USB0dba:3000'
  Controls      : 0
  Simple ctrls  : 0
```

All software can see it - pulseaudio volume control, alsamixer, Audacity, jack - but nothing seems to be able to use it. 

In Audacity I have 'Audio host' as 'alsa', output and input devices set to 'MBox 2: USB audio (hw:2,0)'. When I hit record in Audacity, I get the error shown in the second attached pic: 'Error while opening sound device. Please check the input device settings and the project sample rate.'

'MBox 2: USB audio (hw:2,0)' is how it's known in Audacity. Qtjackctl has two entries for it in input and output device; hw:2=MBox 2, and hw:2,0=USB Audio. I've tried them both, but neither work. PAVControl sees it as MBox 2, it has adjustable controls, but nothing plays through it. 

I have experimented a little with /etc/modprobe.d/alsa-base.conf, but to no avail. See the 14.04 thread for a full description of those shenanigans. For now, I am running no tweaks in there, except having commented out any of the 'options snd-usb-audio index=-2' lines as apparently they can prevent usb audio devices from using any index. In this variation on 12.04 I have only tried:

```
options snd-usb-audio index=2
```

Works fine, but makes no difference. My feeling is that the solution may be somewhere in a combination of the right option and alias lines. During the 14.04 experiments I tried:

```
alias snd-card-2 snd-usb-audio
options snd-usb-audio index=2
```

Did nothing, but wondering if that is because I was using the wrong details? 'aplay -l' reports:

```
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: M2 [Mbox 2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

From alsamixer:

```

2 [M2             ]: USB-Audio - Mbox 2                                   &#9474; >
&#9474;&#9474;                      Digidesign Mbox 2 at usb-0000:00:1d.0-1.2, full speed&#9474; 
```

From 'lsusb':

```
Bus 002 Device 007: ID 0dba:3000  
```

I find this output a little odd as it doesn't name the device, only gives the pid and vid.


So what gives? It's like the lights are on, but no-one's home. After installing something for it, can't remember what, the final message at the end of the install was along the lines of 'The MBox will be muted by alsa by default!!! You need to adjust this with alsamixer or OSS'. Problem is, it gives me the 'no controls' message in alsamixer. Alsamixer also shows S/PDIF as unmuted but at '00' and there is no way to change it. Don't know if that is relevant. 

If anyone has ANY clues about this please don't hesitate to chime in. To record in Linux using the MBox with Audacity on the laptop would be a dream come true and loosen the grip of Win (although Protools, Sibelius and Cubase will NEVER be native to Linux in my lifetime and I refuse to use Wine ;))

PS: The third pic is of PAVContol. TIA

PPS: I have fiddled around with jack and its been great learning a bit more about it, but I figure not too much point spending any more time on that until I can get Audacity communicating and recording directly using the MBox I figure.

PPPS: alsa info is [HERE]("http://www.alsa-project.org/db/?f=c30ede26d89843048947e95486e832c8dad9d039").

---

### Post by Bucky Ball on 2014-01-19
Well, this is something. I think I figured out one of the reasons the Mini is not communicating. This:

```
[22827.179891] usb 2-1.2: config 1 interface 2 has no altsetting 1
[22827.179902] usb 2-1.2: config 1 interface 3 has no altsetting 1
[22827.179911] usb 2-1.2: config 1 interface 4 has no altsetting 1
[22827.179920] usb 2-1.2: config 1 interface 5 has no altsetting 1

```
Is explained by this:

```
Each interface has 5 altsettings (AltSet 1,2,3,4,5) except:
337	 * Interface 3 (Digital Out) has an extra Alset nb.6 
338	 * Interface 5 (Digital In) does not have Alset nb.3 and 5 
339	
340	Here is a short description of the AltSettings capabilities:
341	 * AltSettings 1 corresponds to
342	  - 24-bit depth, 48.1-96kHz sample mode
```

... from [HERE]("http://www.spinics.net/lists/alsa-devel/msg27074.html"). There is a list of available options for the altsetting, but this is the one that applies as I think the driver is locked at 48kHz/24bit. I think. For some reason the MBox is not being given altsetting 1. :-k

Anyone know where I can find that setting and perhaps tweak it?

---

### Post by Yellow Pasque on 2014-01-20
It looks like it should work without fuss on kernel 3.8 or later: [https://github.com/torvalds/linux/commit/cb99864d40e46dea9c2aa3eaa97517b776f91024](https://github.com/torvalds/linux/commit/cb99864d40e46dea9c2aa3eaa97517b776f91024)

You should install lts-raring (or lts-saucy) kernel if you want the best chance of it working.

As for why it only shows the USB ID and no name, you have to update the USB IDS since Precise is relatively old.
```
sudo update-usbids
```

Make sure you have the card plugged into a USB port that lsusb lists as 2.0 compliant.

---

### Post by Bucky Ball on 2014-01-20
Thanks for your input. I think this is the issue:

```
config 1 interface 2 has no altsetting 1

```
... and found this:

```
/proc/asound$ cat /proc/asound/M2/stream0
Digidesign Mbox 2 at usb-0000:00:1d.0-1.2, full speed : USB Audio

Playback:
  Status: Stop
  Interface 2
    Altset 2
    Format: S24_3BE
    Channels: 2
    Endpoint: 3 OUT (ASYNC)
    Rates: 48000

Capture:
  Status: Stop
  Interface 4
    Altset 2
    Format: S24_3BE
    Channels: 2
    Endpoint: 5 IN (SYNC)
    Rates: 48000

```
Which confirms the MBox is being set to altset 2 and not 1 (it needs to be set to 1 for 48kHz, which is why I'm getting this when I hit record in Audacity: 'Please check input device settings and sample rate,' I think). I have tried opening that file as root and changing altset to 1, but it doesn't save changes and auto-sets itself back to 2 when I re-open the file.

Yep, tried your suggestion over a year ago now (full explanation about using newer kernels and other things on this page: [http://www.zamaudio.com/?p=97](http://www.zamaudio.com/?p=97)). I have tried on 3.9, 3.11, and tested in Trusty kernel (I have been fiddling with this for a couple of years at least, as I say). They don't work 'ootb' or after hours of tweaking and if the driver is now part of alsa in these kernels there appears to be a problem. 

As far as I can see, the MBox is working fine now as far as being recognised; it appears to be one of the settings, and my vote is that it is the wrong altset that is the problem. I have no idea how to change this. It works, just won't record in Audacity, even though it is recognised without issue, because of the error shown in my first post.

Like I said, using the method I describe in my first post:

```
git clone https://github.com/zamaudio/alsa-driver.git
cd alsa-driver
git checkout mbox2
cd alsa
./gitcompile
sudo make install
```

... is the ONLY way this driver has ever worked, at least for me. I don't doubt that if I ran this in the other kernels I'd get this same result (am about to try that later today). I get perfect audio with a guitar and headphones plugged into the MBox and the system sees it fine. Just won't give it any controls and I think this is due to confusion about the sample rate due to the altset number.

The burning question for me is: how do I change the altset of the MBox to 1 so I can confirm my suspicions?

Any and all suggestions/ideas/further clues welcome. ;)

PS: Tried this, no change.

---

### Post by Bucky Ball on 2014-01-20
As I just solved this in 14.04 this thread has become somewhat redundant. So rather than solved, it's been obsoleted! For those attempting to get the MBox working in anything other than 14.04, see page 3, post 22 here for some clues:

[http://ubuntuforums.org/showthread.php?t=2199061&page=2&p=12904347#post12904347](http://ubuntuforums.org/showthread.php?t=2199061&page=2&p=12904347#post12904347)

You will get an idea of what should be happening and what you should be seeing, regardless of the release you're using. I thought I'd be using 12.04 as a working comparison to get the 14.04 setup working but it's turned out the other way around. I have used exactly the same setting for jack and Audacity in 12.04 as in the working 14.04 to no effect. Same as it has been. 

One clue I can give is I couldn't get it working without QJackctl and the Jack Audio Connection Kit. See the link for the set up and full instructions. The only thing I don't cover is the installation of the driver itself and that can be found on the Zamaudio link I provided earlier. 

As this is not solved and people may want to chat about it, I'll leave it awhile before marking it anything. I'm happy to help in whatever way I can if anyone else is having troubles in any release other than 14.04 (just post on this thread, no PMs, and about the MBox ONLY please), but I'm testing 14.04 the majority of the time now so I have no reason to get it working in 12.04 anymore (although that would be nice to). ;)

Good luck future travellers.

PS: If anyone does get the MBox working in anything other than 14.04 I'd be extremely interested to find out how they did it. :-k

PPS: This 'config 1 interface 2 has no altsetting 1' doesn't appear to be the problem, as I suspected in my last post. I still get that in the dmesg in the working setup in 14.04.

---

