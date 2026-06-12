---
title: "rhytmbox, banshee and gstreamer-&gt;jack"
date: 2015-07-08
forum: Multimedia Software
---

### Post by intera91 on 2015-07-08
have got jack all setup and working, pulseaudio re-directed to jack and gstreamer 0.10 directed to jack.
gstreamer-properties test tone working in jack and creating an instance in Catia, all non apps working (non-mixer etc...)

Now am getting confused when it comes to so called "gstreamer apps" cause none of them will play ball. all of them (rhytmbox, banshee ...) route their audio stream to pulse and not gstreamer i.e they will not create a client in jack ...

However vlc will use jack without a problem. question is how to route  gstreamer apps (banshee, rhythmbox ... ) through gstreamer so that they create their own stream in jack???

I must be mising something ... but what???

Thanks for your help

---

### Post by dino99 on 2015-07-09
since a couple months, pulseaudio is now very sensitive to hardware: jacks have to be plugged as attended (same colors) and bios/uefi set to 'hda' only

---

### Post by intera91 on 2015-07-10
Thanks for your answer but I am not talking hardware here am talking jackd software ;-)

---

### Post by dawiba2 on 2015-07-10
You don't say if you have, but you need to have pulseaudio-module-jack installed.

This will create a pulseaudio client whenever you start jack (which you can find in the qjackctl connections window.). This way, any application that outputs audio to PulseAudio, will by default have it's output routed to jack courtesy of the Pulse to Jack connection

In qjackctl, under Setup -> Misc, you will need to have checked 'Enable D-bus interface'

You don't say what interface you're using, but perhaps trying the different output options from the drop down menu in the qjackctl Setup -> Settings tab might get your sound working

The only other thing you might need to do, would be to open Sound Settings window and under the Output tab, make sure that 'Jack sink (PulseAudio JACK Sink)' is selected.

Rhythmbox, Firefox et al are all able to route sound through jack on my laptops using this setup. I've never tinkered with any g-streamer configs and I'm running a pretty much default 15.04/Unity

[This page]("https://help.ubuntu.com/community/UbuntuStudioPreparation#Pulse_Audio") might be better at explaining it than me.

Hope this helps

---

### Post by Yellow Pasque on 2015-07-11
> gstreamer 0.10 directed to jack.

Modern gstreamer apps are going to be using gstreamer**1.0**. I don't think there's a way to set the system-wide gstreamer1.0 sink like one easily could with gstreamer0.10 (using gstreamer-properties or gconf/dconf editor). You have to do it per-application, if the application is nice enough to give you that option.

---

### Post by intera91 on 2015-07-30
Indeed and rhythmbox and banshee do not offer that option!!!! damn!!!!

---

