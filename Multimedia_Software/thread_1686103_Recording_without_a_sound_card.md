---
title: "Recording without a sound card"
date: 2011-02-11
forum: Multimedia Software
---

### Post by chidat on 2011-02-11
Hi, I have a Sony VAIO VGN-FW200 laptop and I wanted to use Audacity or some other application to record sound. However, since there is no sound card, the only option is to use the microphone to record. Is there any way to get a free virtual sound card, or record without using one (and without using the microphone)?

Thanks!

---

### Post by desnaike on 2011-02-11
I looked up the model number you posted and the specs say you have built in sound card " dolby surround sound".

---

### Post by chidat on 2011-02-11
Is "Dolby Sound Room" really a sound card? In any case, I'm still unable to record using Audacity.. the only options there are in the preferences are "HDA Intel: ALC262 Analog (hw:0,0), "pulse", and default. The first and third record from the microphone, and the second doesn't record anything at all.

---

### Post by markthekdeguy on 2011-02-12
'Dolby Sound Room' isn't a soundcard. its just an 'enhancement' 
that is installed with the drivers - in Windows. you DO have a soundcard, all modern laptops do.
the jacks on the side of the laptop are connected inside to the built in soundcard.
your laptop will have speakers built in somewhere too.

so you are as well set up to record anything as anyone else is really.
there is nothing wrong or missing in your laptop.

It depends *what* you want to record. your working microphone is obvious,
but if you want to record something that you're listening to on the internet,
there are different ways, it depends on what  you're listening to.

Mark

---

### Post by chidat on 2011-02-12
Ok, thanks for the clarification! I'm thinking of recording streaming audio; I've managed to accomplished this on my old desktop using the "stereo mix" option as the recording device, but there is no such option on my laptop. Thanks again!

---

### Post by b0b138 on 2011-02-12
[http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html](http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html)

---

### Post by chidat on 2011-02-12
Thanks, but even after following those steps, it still does not capture any of the audio. The playback after recording is empty. I'm not sure what could be wrong. Thanks again.

---

### Post by moma on 2011-02-12
Hello,
Start gnome-volume-control and check the settings under the [Input] tab. Please read [this...]("http://www.futuredesktop.org/#step7c") and follow the link to picture 7c.

Install also this [audio-recorder]("https://launchpad.net/~osmoma/+archive/audio-recorder").
It may help you to set the device and you can see if the level-meter moves during recording.

As said:
1) Check [[Input]]("http://www.futuredesktop.org/maverick/images/picture-7c.png") options.
2) Install [audio-recorder]("http://i1.no/0cd0/").

---

