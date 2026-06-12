---
title: "new setup questions"
date: 2011-11-27
forum: Mythbuntu
---

### Post by dkag7 on 2011-11-27
Hi All,

I am going to setup a new system for Mythbuntu and have a couple of questions.
I am 100% new to this, so sorry if i ask a bone-headed question..

I have 3 main concerns when building the system;
1. commercial detection speed. id like to be able to watch a recording and have the commercial detection working good while watching the recording. Is this related to CPU speed, Mpeg decoding, or RAM? My guess is CPU... if so, what is a good speed CPU for this? (Also is intel chipsets and cpu the way to go for this)?
2. id like to be able to play many conversions that i have made, mostly ffmpeg/Divx/H264.
Is this just a matter of installing the right codecs for the OS (if needed)?
3. The video feed coming into the system will be from a dish network receiver. So my guess is that i do not need a tuner card, but just a way to get video into the system. I looked online all over the place but am not finding any answers about this. Is it true that i just need a to get the video into the system (because dish is the tuner)? If so, can someone give me a recommendation on a card (or maybe a USB device) to get the video into the system. Composite (RCA) input is fine for now.. If it has svideo or RGB all the better... As long as the video is as clear as possible (with composite)
Also this setup will have the front and backend on the same system

Thanks !

Kurt

---

### Post by nickrout on 2011-11-28
> **dkag7 said:**
> Hi All,

I am going to setup a new system for Mythbuntu and have a couple of questions.
I am 100% new to this, so sorry if i ask a bone-headed question..

I have 3 main concerns when building the system;
1. commercial detection speed. id like to be able to watch a recording and have the commercial detection working good while watching the recording. Is this related to CPU speed, Mpeg decoding, or RAM? My guess is CPU... if so, what is a good speed CPU for this? (Also is intel chipsets and cpu the way to go for this)? primarily CPU, as many cores as possible and as fast as possible. Also there is an experimental setting to speed up commercial detection, ot does something like work with a quarter sized frame. It reportedly works very fast. Don't ask me where the setting is...> 
2. id like to be able to play many conversions that i have made, mostly ffmpeg/Divx/H264.
Is this just a matter of installing the right codecs for the OS (if needed)? the mythtv internal player handles all those, no need to install anything else, the codecs are built in. Having said that, nothing is perfect and you may occasionally need an external player for the odd file, particularly if it has unusual coding parameters. > 
3. The video feed coming into the system will be from a dish network receiver. So my guess is that i do not need a tuner card, but just a way to get video into the system. I looked online all over the place but am not finding any answers about this. Is it true that i just need a to get the video into the system (because dish is the tuner)? If so, can someone give me a recommendation on a card (or maybe a USB device) to get the video into the system. Composite (RCA) input is fine for now.. If it has svideo or RGB all the better... As long as the video is as clear as possible (with composite)
Also this setup will have the front and backend on the same system

Thanks ! the hdpvr is best as it is the only solution that will give you HD. But any analogue capture card will give you SD, recommended though that you get one with an inbuilt encoder like the PVR150/250/350 (which are not made any more) or their up to date equivalents. I don't do analogue capture so I cannot comment further.

You will also need a way to change channels on the Dish machine, usually an "IR Blaster" is the trick. It plugs into (usually) the USB port on the reciver and sends infrared signals to the dish device to simulate a remote control. You set a script in the backend to send a channel change remote command to the dish receiver.

Are your transmissions encrypted? If they are not, you can get a DVB-S tuner card and get a pure digital signal, and much better quality.

---

### Post by dkag7 on 2011-11-28
Hi Nickrout.. thanks for the reply...

Some stations are and some are not encrypted..
the ones i pay for are not (if this is what you mean)...
I will not use any OTA stations (i live in the middle of no-where so i cant get any stations) just what comes through dish network receiver (vip 211)

The dish receiver has the R/F (i think its called.. the cable screws into it) out (to tv) connection and the composite and component. So i have those choices to connect into the tuner card that i will eventually get. I do have a ADS Tech Pyro a/v link I use for video editing. On my MacPro, it just works and no drivers are needed... I am not counting on it working on the mythbuntu setup however.. It has the standard analog in and out puts and connects to the computer by IEEE Fire wire. If it works all the better, but i doubt it.

I have 2 beasts of computers that i will try out first. A HP workstation xw8200 and another one i put together (forget the MB now..) Problem is that they are very loud, especially the HP.
My work computer is a macpro but i've seen some horror stories on line where the mac os will not boot after mythbuntu is installed on and external USB HDD (which is what i was thinking on doing originally). 

I was looking at the Asus Pundit P1 but not sure what tuner card to get that would fit into the case.. it looks quite small.

One other question... It looks like most the tuner cards also have video out (to tv).
Is this the way to get video to the TV or should I get a video card with TV out ?

I am looking in the 'working/not working' hardware setups people have on this forum to get some ideas of what works the simplest way. until i get use to the mythbuntu OS, i will need to do the best i can to get it to 'work out of the box'...   

For now, is it possible to just change the stations with the dish remote and leave the mythbuntu on one station to record?.. so whatever station dish remote is on, it will just feed into the tv tuner card on the system.

thanks again for your help !

Kurt

---

### Post by nickrout on 2011-11-28
I assume from the name that "dish" is a satellite provider. If the channels are unencrypted then get a DVB-S card. However if it is a pay provider, I think they will be encrypted.

So, assuming the signal is encrypted, do you get HD via dish? If you want to record HD you will need an HD-PVR.

R/F is the worst possible way to get a signal from your receiver. Component best and composite inbetween the two.

Yes you can use a tuner card to record whatever channel you have the receiver tuned to, but that's hardly a PVR.

---

### Post by RideMan on 2011-11-28
DishTV is a DBS provider, and I would assume that all of their channels are encrypted.  Otherwise, what's to stop me from popping a dish onto the roof and receiving their service with a tuner card and no subscription. They have to have some way to stop the freeloaders and shut off subscribers who don't pay their bills.  8-)

--Dave Althoff, Jr.

---

### Post by nickrout on 2011-11-29
Not all satellite providers charge, and not all are encrypted. I am on freeview in NZ and get free channels unencrypted. Sky broadcasts  from the same satellite, but it's signals are encrypted.

The OP said some of his channels were unencrypted, but he may or may not be right ;-)

---

### Post by dkag7 on 2011-11-30
Thanks for all your help..

Because my tv has no hdmi input, and because all converters i can find do not work with my tv (mitsubishi 1080i), i decided to go with just a SD setup for now.

I bought a pundit P1-PH1 ($130.00) and a pvr 150 ($30.00).

I am just hoping i can get decent commercial skip function with this P4 3ghz single core cpu
and i can set up the remote too...

hopefully i can set this all up without pulling out too much hair!

thanks
Kurt

---

