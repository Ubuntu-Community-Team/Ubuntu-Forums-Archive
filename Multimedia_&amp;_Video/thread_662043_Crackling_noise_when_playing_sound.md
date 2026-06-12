---
title: "Crackling noise when playing sound"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by stianalm on 2008-01-08
Hi!

I am trying to get a USB headset to work on my gutsy machine. Actually, it plays ok and the mic is also working ok. But, whenever my system plays any sound I get crackling static noise on top of it. The noise is louder when I increase volume and vice versa.

As you probably can guess I'm not a seasoned linux expert so I need help in troubleshooting the issue. I have searched both here and on google but haven't found a good solution. Does anyone have an idea where I start?

This is the output of aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

As you can see I also have an onboard sound card. Could that be the reason for the static? If so, how do I disable it?

Am grateful for any help...

---

### Post by stianalm on 2008-01-10
Since nobody else is answering my posts, I'll do it myself...

I have found out why I get the crackling sound. The default sample frequency that ALSA is using is 48000 Hz, but the sound card in my Logitech USB Headset is only supporting 44100 Hz. It might be supporting more frequencies, but at least not 48000 Hz.

I tested this with this command:

```
aplay -vv -fcd  somefile.wav
```

Where the -fcd says that aplay should be using CD quality, that is 44100 Hz. This works well with my Headset. The model number is A-0374A, by the way. I put that here  in case someone with the same problem should happen to search here.

Now, the question is, how do I set the default frequency to 44100 Hz? Probably it has something to do with the .asoundrc file...

---

### Post by amtur_poet on 2008-01-15
I have the exact same problem with my A-0374A headphones. I also can't control the volume of them, and it's too loud.

---

### Post by Michl on 2008-01-15
Ok, this is probably irrelevant, but I had a similar problem and it was solved by lowering the
master volume control for ALSA.
M

---

### Post by stianalm on 2008-01-16
amtur_poet : 

Have you tried to test with the command I wrote, aplay? Does that still give you the same crackling noise?

Also, how do you try to control the volume? For me it works fine. I can even use the remote control on my headset to control the volume in Ubuntu. That's actually really cool. It seems to be a bit buggy though, but I don't know if that's only my headset.

---

### Post by amtur_poet on 2008-01-16
I use every possible method to control the volume. None work.

---

### Post by stianalm on 2008-01-22
I'm sorry. I'm not a linux expers so I don't know how to help you. I need something to search for to come with any suggestions. You just have to keep at it. Search these forums and of course google. Probably there are someone out there that have gone through the same as you.

---

### Post by Elevator_Hazard on 2008-02-09
Did anyone figure out how to set default frequency yet? I have logitech usb headset 250 or 350 and this is probably my problem...

---

### Post by stianalm on 2008-02-11
Hi, elevator_hazard!

I used the .asoundrc file. I'm don't have access to my linux machine right now so I can check, but just google for .asoundrc and you will probably find out how to do it. I mean, I figured it out so you should also be able to... :)

---

### Post by Elevator_Hazard on 2008-02-17
> **stianalm said:**
> Hi, elevator_hazard!

I used the .asoundrc file. I'm don't have access to my linux machine right now so I can check, but just google for .asoundrc and you will probably find out how to do it. I mean, I figured it out so you should also be able to... :)

I didn't figure it out :(

---

### Post by stianalm on 2008-02-18
I looked at this site : [http://alsa.opensrc.org/TroubleShooting#Sound_can_be_heard_but_it_is_distorted](http://alsa.opensrc.org/TroubleShooting#Sound_can_be_heard_but_it_is_distorted)

Here it says:

Some cards, especially recent ones, can only handle a fixed set of frequencies. Some can only handle a single frequency, usually 48000Hz. try to use the plug: plugin prefix when playing. If your card can only play a single fixed frequency you must ensure that the driver is told that (by the use of driver-specific option parameters), and the ALSA library is setup up to output sample only at that frequency. Usually this will involve using the plug plugin in /etc/asound.conf.

So I ran the asoundconf tool to get .asoundrc and .asoundrc.asoundconf set up in my home directory. Then I set the parameter defaults.pcm.dmix.rate to 44100. This is not the recommended way to do this. If you run asoundconf again, the change will be undone. But I am new to linux and I haven't found a better way to do this yet. If you find it, tell me!

---

### Post by wired00 on 2008-04-17
did anyone find a solution to this? Here is a stop gap fix...

i have the same problem when playing via USB connection to my external iBasso Headphone amp/DAC. I've found that the sound crackles especially when the CPU is being used... ie, if you click the Maximise/unmaximise button over and over quickly the sound crackling occurs. When i was doing this i realised the wobbly windows compiz effect might be causing some issue because the window is wobbling around when maximise/unmaximise occurs. So i tried going System > Appearance > Visual Effects and changed it to "None" low and behold the problem is fixed.

So... when your playing music (which i do all day at work!) you have to disable all compiz effects.

In short, to reproduce this bug, you must have sound (music) playing through a USB device... turn on Extra setting via System > Appearance > Visual Effects so that Wobbly windows is enabled then drag a window so its filling the screen and click between Maximise/Unmaximise. It will cause the window to wobble and so create crackling in your sound output.

---

