---
title: "enable 4 channel output with jack"
date: 2007-06-15
forum: Multimedia Production
---

### Post by keithacole on 2007-06-15
please help.

jack doesnt show channel_3. channel_4, i have enabled surround sound via ubuntuguide, but when i use jack with mixxx or ANY app, i cannot use the other 2 channels on the card. i have been searching and tweaking for several weeks now, PLEASE help

---

### Post by paulg on 2007-06-15
What soundcard are you using? How are you starting JACK (jackd from terminal or qjackctl)? What programs are you trying to play sounds with?

Edit:
sorry, missed that you stated you are using 'mixx' in your first post.

~pAul.

---

### Post by keithacole on 2007-06-15
im using a soundblaster audigy pci 5.1 card, the main program im trying to use is 'mixxx', i am starting jack through qjackctl

---

### Post by paulg on 2007-06-15
I'm by no means an expert, but I'll take a shot. I apologize if I'm boring you with minor problems that someone experienced with JACK wouldn't have as I am kind of assuming you are new to the program. These are just some of the pitfalls I had when first starting to use JACK.

Are you able to get 5.1 sound using a program that does not use JACK? If it doesn't work on it's own with ALSA, it won't work with JACK. Try a DVD if you are able to?

Are you pressing the start button in qjackctl (triangle 'play' button) after opening qjackctl? It's the larger one on the left hand side. The smaller button is for the transport.

Have you tried looking at the messages window (press the messages button) to see if you are getting any errors?

Have you looked at the connections window to see if you have multiple outputs showing up in your card? You may need to 'patch' the program into your soundcard outputs (probably something like PCM_3 and PCM_4). You can also try the program Patchage which does the same thing but is a little more visually pleasing.

That's all I have. The wealth of my knowledge. Hope it helps you out.

~pAul.

---

### Post by keithacole on 2007-06-15
i get surround sound with alsa, i actually have the volume on the keyboard control the rear output, which goes to my amp in my rack, and then the front output goes to my headphones,

i start jack control, then i start the server, then i start mixxx, and inthe mixxx preferences i choose to use jack as the sound output,

then i look at the connections window from jack to get everything running right, but nomatter what i do i cannot route any sounds to channel_3 or channel_4, i do not even have the options, the ONLY options i have to output sound is to channel_1 and channel_2

its not a mixxx issue becuase jack-patch itself is not showing the other outputs.

---

### Post by paulg on 2007-06-15
If you do not have routing to the channels available in JACK then your card may not support it. However, it does not make sense to me since ALSA will playback through the channels unless it's a limitation of the hardware design... I do not know and am only speculating??!

Sorry, I am at the limit of my knowledge... I was not kidding before =)

Good luck!

---

### Post by keithacole on 2007-06-15
im gonna rule out hardware limitations.. since i get surround sound with alsa.

i think something in my ~/.asoundrc needs to modified for this to happen

---

### Post by kayosiii on 2007-06-17
Have a look at the settings panel of qjackctl you should be able to change the number of input and output channels, settings are right near the bottom right... I am not sure that jack intrinsically understands things like surround sound the way that alsa does though.

---

### Post by keithacole on 2007-06-17
ive tried that, and it doesnt help, it actually makes functioning without xruns virtually impossible with a decent latency setting

---

### Post by stueyboy on 2007-06-22
Sorry if you have done this already but I am also trying to do this but I have an audigy2 card which won't support this sort of thing so I have bought a cheap 5.1 urround card. In Jack prefs, have you enabled multichannel input and outputs instead of the defaults? That should alloow you to get the additional outputs.

---

### Post by keithacole on 2007-08-02
yes i have allowed the miulti channel in/out.

im gonna chaulk it up as hardware issue, which doesnt make sense to me since i get all outputs working with alsa, not with jack.




i guess i need to buy external. maybe m-audio

---

### Post by fredj on 2007-08-03
I don't completely understand your problem. Jack is an audio server and is 
typically meant to stand between a sound card and a multitrack recorder.
Unless your sound card has four inputs there is no need for jack to have
four outputs. 

In a multi track recorder it is usual for all tracks to be recorded as mono.
They may be mixed down to stereo or surround sound but this has nothing to 
do with Jack.

If you just want to play back surround sound then there is no reason to use
jack.

---

### Post by keithacole on 2007-08-03
im trying to use front channels for the monitors, and rear channels for my headphones, for live performance

---

