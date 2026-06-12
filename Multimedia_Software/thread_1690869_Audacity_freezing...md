---
title: "Audacity freezing.."
date: 2011-02-19
forum: Multimedia Software
---

### Post by Baldrick_NZ on 2011-02-19
Does any one know what might cause audacity to freeze while recording something from a line input? Sometimes it runs for a few seconds other times it'll run for a minute or two before freezing.

The app itself doesn't seem to freeze, just the recording.

It all works well under XP using Audacity, so it would seem like a problem peculiar with Ubuntu. Obviously I'd like to get to the bottom of this so I don't have to keep booting into Windows.

Thanks in advance,
Baldrick

---

### Post by pafufta503 on 2011-02-19
my advice is to ditch using audacity.  i've run across a number of bugs which have destroyed or altered my .aup projects.  random crashes and freezes.  audacity is not ideal for anyone to use, it is heavily unstable.  use ardour instead, for reasons of stability.

i cannot believe audacity has been in development for around 10 years, and is still as unstable as it is.

---

### Post by Baldrick_NZ on 2011-02-19
> **pafufta503 said:**
> my advice is to ditch using audacity.  i've run across a number of bugs which have destroyed or altered my .aup projects.  random crashes and freezes.  audacity is not ideal for anyone to use, it is heavily unstable.  use ardour instead, for reasons of stability.

i cannot believe audacity has been in development for around 10 years, and is still as unstable as it is.

I tried Ardour, but found that it didn't want to run on my set-up. It kept telling me there was a problem with JACK, but didn't tell me what the problem was or how I could go about fixing it. Odd how audacity works fine under XP, on the same machine though...

---

### Post by fallenstar on 2011-02-20
> **Baldrick_NZ said:**
> I tried Ardour, but found that it didn't want to run on my set-up. It kept telling me there was a problem with JACK, but didn't tell me what the problem was or how I could go about fixing it. 

Hi, do you have Jack running before you start up ardour?

I've found playing with the latency stops Audacity from freezing, and running it at 48000Hz seems to be the general consent. I've got my latency at 1000 and -500 but the whopping half a second latency is easily edited. Overdubbing can be touch and go.


I can't use ardour as my usb mic works as capture only, and i need to hear the last track to keep up, thus am continuing arguing with audacity. Grrr. :confused:

---

### Post by pafufta503 on 2011-02-21
do a search about starting and running jack, you'll find lots of into that will solve any problems you have.  i know that ardour is not as straightforward, but you can do monitoring/etc once you get it running.  jack can do anything that ALSA can do, and with much less latency and much more stability.  it does require some learning and getting used to of course, unlike audacity which is so obvious that beginners tend to use it.

maybe this will help you get the jack server running.  go to synaptic, install the package named Patchage.  now, open jack control, then open patchage, and then click the Start button.  Patchage will initialize your audio devices/software properly so that you can start the jack server without incident.  you can also patch the i/o's for all event, audio and midi connections, giving jack an unbeatable modular control of your audio server.

---

### Post by Baldrick_NZ on 2011-02-22
> **pafufta503 said:**
> do a search about starting and running jack, you'll find lots of into that will solve any problems you have.  i know that ardour is not as straightforward, but you can do monitoring/etc once you get it running.  jack can do anything that ALSA can do, and with much less latency and much more stability.  it does require some learning and getting used to of course, unlike audacity which is so obvious that beginners tend to use it.

maybe this will help you get the jack server running.  go to synaptic, install the package named Patchage.  now, open jack control, then open patchage, and then click the Start button.  Patchage will initialize your audio devices/software properly so that you can start the jack server without incident.  you can also patch the i/o's for all event, audio and midi connections, giving jack an unbeatable modular control of your audio server.

Thanks for that. So, would these issues be resolved if I install Ubuntu Studio, where both come pre-installed?

---

### Post by pafufta503 on 2011-02-22
> **Baldrick_NZ said:**
> Thanks for that. So, would these issues be resolved if I install Ubuntu Studio, where both come pre-installed?ubuntu studio doesn't come with anything that you can't install in the other ubuntu distributions, but it is packaged with everything you need to get started.  i would recommend using it if you are considering using ubuntu for sound production, otherwise just look at the packages it comes with and install them for your currently installed version of ubuntu.

i would recommend going to the jack webpage and reading what it's all about, this will help to wrap your brain around how to use jack.  good luck my friend, you are embarking on a wondrous journey ; )

---

