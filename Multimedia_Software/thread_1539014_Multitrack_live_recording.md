---
title: "Multitrack live recording"
date: 2010-07-26
forum: Multimedia Software
---

### Post by lildigiman on 2010-07-26
Back when I was on windows I used FL studio with ASIO drivers. With that, I was able to do live recordings with multiple tracks at a time. I have two separate inputs on this computer (both standard 8th inch Mic jacks).

Is there any way I can record both those inputs at the same time, to separate tracks(with either Audacity, Ardour, or LMMS, etc...)?

I literally haven't found anything on the topic. Also, I should let you know, JACK only lets me use one at a time(unless I am doing it wrong?).

Thanks, any help is greatly appreciated.

---

### Post by aeiah on 2010-07-26
audacity is the simplest. if you cant do it in audacity then there's obviously something wrong with your setup. you shouldnt even need to use jack really. what does your audio properties look like? does it see both inputs?

---

### Post by lildigiman on 2010-07-26
I can see both inputs, but I can only select one at a time for capture from the Sound preferences window (under System->Preferences->Sound).

Any audio program I use, sees only that single input I have selected...

---

### Post by cchhrriiss121212 on 2010-07-26
Could you post the output of arecord -l?

---

### Post by VH-BIL on 2010-07-26
If both those inputs are available Jack should let you connect them to inputs in your recording application like Ardour.

I use Ardour for recording and audacity for just wave editing.

---

### Post by lildigiman on 2010-07-26
```
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: U0x46d0x8b2 [USB Device 0x46d:0x8b2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also, VH-BIL, jack only see's one device at a time as well (which is the one that I select in sound properties).

---

### Post by VH-BIL on 2010-07-26
> **lildigiman said:**
> ```
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: U0x46d0x8b2 [USB Device 0x46d:0x8b2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also, VH-BIL, jack only see's one device at a time as well (which is the one that I select in sound properties).

I thought it was 1 device with multiple inputs.

---

### Post by cchhrriiss121212 on 2010-07-26
> **VH-BIL said:**
> I thought it was 1 device with multiple inputs.
That's what the output above seems to indicate, so you should be able to see them both available under the connections window in jack.

---

### Post by lildigiman on 2010-07-26
I have an integrated sound card with two Mic inputs. Sorry If I was unclear.

They are Card 0's Device 0 and device 2

---

### Post by lildigiman on 2010-07-26
> **cchhrriiss121212 said:**
> That's what the output above seems to indicate, so you should be able to see them both available under the connections window in jack.

Can you give me some help on how to configure jack properly, So that it sees both devices?

---

### Post by cchhrriiss121212 on 2010-07-26
> **lildigiman said:**
> Can you give me some help on how to configure jack properly, So that it sees both devices?
OK, once you have opened jack are you pressing the start button? Once jack has been started you should be able to see all your available inputs and outputs in the connections window.

---

### Post by lildigiman on 2010-07-28
> **cchhrriiss121212 said:**
> OK, once you have opened jack are you pressing the start button? Once jack has been started you should be able to see all your available inputs and outputs in the connections window.


Haha I know how to use jack for the most part. The Connect window only shows TWO capture devices (AKA LEFT/RIGHT) to whatever my CAPTURE device is set to in the ALSA (System->Preferences->Sound) application. And yes, just for kicks, I did try it anyway, and got exactly that, LEFT/RIGHT for whichever capture device is set.


I still have yet to figure anything out.

More info: Both inputs are from the same card, card 0, and show up as HW:0,0 and HW:0,2

A bit of googling told me that the ALSA dsnoop plugin may do what I am looking for? I can't really tell...

Still looking for help... 

Thanks.

---

### Post by cchhrriiss121212 on 2010-07-28
I think you are getting jack mixed up with the settings for pulse audio. System>preferences>sound is a pulse audio control, not ALSA, so anything you select there has no effect to what happens with jack (as pulse is suspended when jack starts).
> 
The Connect window only shows TWO capture devices (AKA LEFT/RIGHT) to  whatever my CAPTURE device is set to in the ALSA  (System->Preferences->Sound) application. And yes, just for kicks,  I did try it anyway, and got exactly that, LEFT/RIGHT for whichever  capture device is set.
Your 2 capture devices are your line in and your mic in, so to record from them you just need to connect them to whatever recording program you like.
In the jack setup window: Try setting your interface as hw:0,0 and leave the other settings on the right hand side as default.

---

### Post by lildigiman on 2010-07-28
> **cchhrriiss121212 said:**
> I think you are getting jack mixed up with the settings for pulse audio. System>preferences>sound is a pulse audio control, not ALSA, so anything you select there has no effect to what happens with jack (as pulse is suspended when jack starts).

Your 2 capture devices are your line in and your mic in, so to record from them you just need to connect them to whatever recording program you like.
In the jack setup window: Try setting your interface as hw:0,0 and leave the other settings on the right hand side as default.

No, that is incorrect. I have a MIC input in the Front and in the Rear of my computer (The case I bought for my PC has the extra audio plugs in the front, which plug into the MOBO's).

(trust me on this, back when I used windows and ASIO things worked!!!)

And Okay, if that IS pulseaudio in the Preferences menu... then I'm really confused, because whatever device I select as the Capture device, is the one that shows up in  Jack - this is not a joke, and I DID actually TRY it, as in listened with my own two ears (just so ya know that I'm not talking crazy).

 Do you want me to do a screen capture of me trying it or something?

---

### Post by cchhrriiss121212 on 2010-07-28
> No, that is incorrect. I have a MIC input in the Front and in the Rear  of my computer (The case I bought for my PC has the extra audio plugs in  the front, which plug into the MOBO's).
My mistake, I had assumed your 2 inputs were a mic in and line in as they are on my PC. In any case I think I have gone off track a bit as I'm not sure I fully understand the problem.

Could you verify that this is what's going on: 
You have two inputs displayed in the jack connection window, but only the one selected in the preferences menu is functional, is that right? Sorry to ask, but I'm not sure what you mean when you talk of left and right in the previous post in relation to capture devices. Any capture port will only give a mono signal.

---

### Post by lildigiman on 2010-07-28
> **cchhrriiss121212 said:**
> 
Could you verify that this is what's going on: 
You have two inputs displayed in the jack connection window, but only the one selected in the preferences menu is functional, is that right? Sorry to ask, but I'm not sure what you mean when you talk of left and right in the previous post in relation to capture devices. Any capture port will only give a mono signal.

Two items show up in the Capture List for Jack. They are the left and right channel(of whichever MIC jack is selected from "System->Preferences->Sound"), "capture_1", "capture_2", respectively. So they are both coming from the SAME input jack... 

Which means, if Jack was really seeing both my mic inputs, there *should* be 4 items in that list, capture_1, capture_2, and probably capture_3, and capture_4.

There is not. That is my problem.

---

### Post by cchhrriiss121212 on 2010-07-29
> **lildigiman said:**
> Two items show up in the Capture List for Jack. They are the left and right channel(of whichever MIC jack is selected from "System->Preferences->Sound"), "capture_1", "capture_2", respectively. So they are both coming from the SAME input jack... 

Which means, if Jack was really seeing both my mic inputs, there *should* be 4 items in that list, capture_1, capture_2, and probably capture_3, and capture_4.

There is not. That is my problem.
Mic inputs do not have left and right channels, they are mono (ie one channel), so you will never get 4 channels showing up with only 2 inputs. Unless you have some kind of stereo mic setup that I have not heard of?
Are there any other options you get in the sound preferences menu?
What do you have for interface set as in jack?

---

### Post by lildigiman on 2010-07-29
Both of my MIC inputs (the physical jack itself) are stereo. (And the Microphone I happen to be using is Stereo as well, thats why I hear both channels, if I was using my guitar, which is mono, I would only get left or right)

There aren't any other options in my Sound preferences menu regarding capture.

My interface in jack is default, the other options also don't appear to support multiple inputs.

---

