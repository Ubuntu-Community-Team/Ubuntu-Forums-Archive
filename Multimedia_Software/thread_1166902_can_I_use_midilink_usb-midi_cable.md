---
title: "can I use midilink usb-midi cable"
date: 2009-05-22
forum: Multimedia Software
---

### Post by ilantal on 2009-05-22
I would like to use Ardor with Jack in place of ugly Microsoft Windows.
I have a usb-midi cable which works with Windows, but it doesn't seem to work with Ubuntu.
If I do lsusb I get:
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1acc:0009  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0db0:a97a Micro Star International Bluetooth EDR Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The entry with 1acc:0009 is apparently the cable, especially as it goes away when I remove the cable. The fact that it isn't identifying itself isn't a good sign (at least I would think so), but is this cable dead in the water for Ubuntu?
Not too surprisingly, Jack doesn't see any usb devices for midi input.
Again, my question is: can I use this cable or is it dead in the water and will only work in Windows?

Thanks,
Ilan

---

### Post by sedawk on 2009-05-22
First clear the message buffer (before plugging in the cable)
```

sudo dmesg -c

```
Plug in the cable, wait 10 seconds and do
```

dmesg

```
What is the output?

(I'm using a "logilink" usb midi cable which works fine. 
 Which version of Ubuntu are you using?)

---

### Post by ilantal on 2009-05-22
sedawk THANK YOU!!!!!
I was TOTALLY lost and had given up all hope.
I even doubted anyone would answer.
Then I turn on my mail and see an answer from you, 
and WHAT AN ANSWER!!
What I get looks good.
ilan@ilan-laptop:~$ dmesg
[  116.692118] usb 6-1: new full speed USB device using uhci_hcd and address 2
[  121.865539] usb 6-1: configuration #1 chosen from 1 choice
[  131.946679] usbcore: registered new interface driver snd-usb-audio

I'm still doing something wrong because JACK still doesn't see it (and the lsusb is still the same - not that I really care about lsusb).
dmesg sees something VERY interesting, so it probably will fly!
The thought of having to use Windows was DEPRESSING.

Can you give me a hint as to what I'm missing? I'm using Ubuntu 9.04 with all the updates to this day.
I anxiously await to hear from you.

Thanks,
Ilan

---

### Post by markbuntu on 2009-05-22
This may be a problem with alsa not seeing the device and so the driver is not getting loaded.

What does aplay -l tell you?
Is the device listed?

---

### Post by ilantal on 2009-05-23
I thought maybe I was missing a restricted driver, so I tried to see if it would detect something. Nothing beyond the nvidia.
Then I looked into the package manager to see if there was anything to snd-usb and again found nothing.
I unplugged it and plugged it in again and got a new address 3, but that probably has no special significance.
What I get is
ilan@ilan-laptop:~$ dmesg
[  503.056107] usb 6-1: new full speed USB device using uhci_hcd and address 3
[  508.233778] usb 6-1: configuration #1 chosen from 1 choice
ilan@ilan-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I don't see it listed in my playback devices.
Any suggestions on what could be the next step?

Thanks,
Ilan

---

### Post by ilantal on 2009-05-23
I've made some progress. Instead of finding the usb under midi, it is under alsa, where I didn't expect to find it.
Now I've got to figure out how to get Ardour to use the midi input. The tutorial I have seems to be somewhat out of date as I need to use the Jack Connect button and not the Setup button as written. I still can't seem to figure out what I need to press in order to take input from the Roland keyboard, via the Midilink usb interface and have Ardour use it.
See the 3 attached images.

---

### Post by markbuntu on 2009-05-24
Unless you have compiled the latest version of Ardour you will not have any midi support. Rosegarden has excellent midi support and you can connect it to Ardour.
There is a really good turorial about that here:

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

---

### Post by sedawk on 2009-05-25
Hello!

The only thing I remember is that I needed to use the alsa
command "aconnect" to connect the cable "sender" to the
midi software "receiver". 
The software I used (for testing) was timidity (so I can hear
the music I play on a midi keyboard from the PC).
I also use Rosegarden (to get "melody" tracks from *.mid files
and view them in the music score view) but I'm not sure I
ever used my keyboard as input or output for Rosegarden.

To test basic functionality you can try to play midi files
to your midi device using amidi or aplaymidi.

---

### Post by markbuntu on 2009-05-26
I use patchage for connecting everything up, ardour,rosegarden, hydrogen, midi keyboards and controllers, Zynaddsubfx. qsynth, timidity. Patchage just makes life so much easier.

I just plug everything in and start up jack and all the apps and start patchage and point and click to connect everything the way I want.

midi keyboard-rosegarden-qsynth-ardour-jack
midi controller-hydrogen-ardour-jack ( I am still trying to figure out some of the controller part of this one)
midi-controller-zynaddsubfx-ardour-jack (for live play along)

Make some tracks in rosegarden and hydrogen and link them into ardour tracks and use the jack transport controls to play/record them together in sync with audio tracks in ardour. It just makes it so easy to edit the midi tracks in their own environemnt since they stay in rosegarden and hydrogen where they are easy to mess around with and then you just hit the play button in jack and you hear what you just did or you can just record it all in ardour live as you go along. Then you can save the tracks and move rosegarden and hydrogen to new tracks and add a few more samples into some new audio tracks........add effects.....sing along...drag out the saxophone...blast it all out the PA....

So much fun.....and so easy....
And its all freee.....

---

### Post by ilantal on 2009-06-01
Thanks for all the help. I am finally starting to see results. The crucial step was to draw a connection between my Midilink usb output to the green "record in" of rosegarden. After that I could play notes on the Roland and Rosegarden would record them. Whew!

Now I've got the problem that Rosegarden has no audio output (which I can hear). Ardour plays its audio output fine, so I know my hardware is OK.

Rosegarden complains about not finding sox, which you can see is installed. I don't care about saving the projects, so kdialog is not interesting. Perhaps the fact that it doesn't find sox is the reason I hear no audio? If it is installed, why doesn't it find it?

Thanks,
Ilan

---

### Post by tikue on 2010-02-14
Hello,
I am an absolute ubuntu beginner and tried to connect the mentioned Logilink USB MIDI cable but I failed. I tried the commands given by sedawk but I got a different error message.

I must say I am running the easypeasy ubuntu version on an eee PC, but for midi recording only this should work.

My Fame MIDI controller was immediately detected by Muse, but the Logilink cable connected to my E-Piano does not work.

Does anyone have an onother idea?

Thanks for your help
Tim

---

### Post by ilantal on 2010-02-15
Hi Tim,
Everything has been running so smoothly for such a long time that I've managed to forget the problem.
I think the critical step is to start Patchage and see if your controller appears. If you see it, you can start to use it. If you don't see it, then you have to figure out why the operating system isn't picking it up.

Let me know if I can help.

Ilan

---

### Post by tikue on 2010-02-15
Hi Ilan,

thanks for your quick reply. As I am not familiar with Ubuntu I do not know how to install the midi adapter. I followed the instructions by sedawk (sudo dmesg -c  ; dmesg) and that's what I get

[  222.463394] usb 2-2: new full speed USB device using uhci_hcd and address 6
[  222.580056] usb 2-2: device descriptor read/64, error -71
[  222.800072] usb 2-2: device descriptor read/64, error -71
[  223.010069] usb 2-2: new full speed USB device using uhci_hcd and address 7
[  223.126733] usb 2-2: device descriptor read/64, error -71
[  223.346756] usb 2-2: device descriptor read/64, error -71
[  223.556833] usb 2-2: new full speed USB device using uhci_hcd and address 8
[  223.970063] usb 2-2: device not accepting address 8, error -71
[  224.076819] usb 2-2: new full speed USB device using uhci_hcd and address 9
[  224.490040] usb 2-2: device not accepting address 9, error -71
[  224.490100] hub 2-0:1.0: unable to enumerate USB device on port 2

A lot of errors...

Any idea what I can do?

Thanks
Tim

---

### Post by ilantal on 2010-02-16
Hi Tim,
When you get it going, the best program I found to actually use it is Rosegarden. It is much better than anything I found in Windows.

Clearly I can't be sure, but it looks to me from your error messages that the problem isn't Ubuntu, it is your hardware. The first error in the list says you are using a hub 2-0:1.0 and that it can't read the device on port 2. From there on, it is error after error.
My guess is that your hub won't support a usb 2.2 device. In any case I would try to go direct without the hub.

Let me know what you find.
Ilan

---

### Post by tikue on 2010-02-19
Problem solved!

I bought a new USB MIDI cable, a Roland UM G -1. It was detected immediately on Ubuntu and Mac, and shows no latency.

The logilink is scrap, but for 10 Euros you probably can not expect more.

Thanks!

---

