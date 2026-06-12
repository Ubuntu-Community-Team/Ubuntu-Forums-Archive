---
title: "Low volume"
date: 2009-06-23
forum: Multimedia Software
---

### Post by SalsaShark on 2009-06-23
When going from Ubuntu Ibex to Jackalope, I switched from a 32-bit to a 64-bit and overall I'm very pleased.  But I'm having a bit of a sound issue that I can't figure out.  The maximum volume is really low, and at about 50% it's almost completely silent.  In Ibex I had this issue as well but it seems to be even more of a problem now.

There's a number of things I've tried, but the only thing that seems to work is running "paman" and changing the value on that volume slider, but to make any significant difference on the quiet parts of movies I need to turn it up so that during the louder parts the quality is aweful.  Moreover, any time I try and change the volume using the dial on my computer afterwards, it automatically goes back to 100% so I can't go from, say 150% to 120% unless I exit full screen and change the slider myself which is too much of a hassle when I want to just sit down and watch a movie.

I have not, on the other hand, tried anything beyond downloading and/or running packages that just let me manually change the value on a slider.  Is there a patch I can install or anything else that will actually solve this issue?

---

### Post by executorvs on 2009-06-24
the defaults on a few jaunty installs like in intrepid didn't set the sound correctly. have you checked this?

if so have you made sure your hardware doesn't have any known issues under jaunty?

that said what soundcard/chipset do you use?

---

### Post by SalsaShark on 2009-06-24
Hmmm, the only information I can find is "Realtek High Definition Audio"

---

### Post by executorvs on 2009-06-24
try 'sudo lshw' in terminal, it's the list hardware command.
if you run 'dmesg' from terminal it will list what hardware the kernel has found.

it's possible you need to add a line at the end of /etc/modprobe.d/alsa-base that looks something like 'options snd-hda-intel model=AUDIOCHIPSET' I can't seem to find the list of options at the moment, I may try again tomorrow.

---

### Post by executorvs on 2009-06-24
just checking, did you find a solution?

---

### Post by raboofje on 2009-06-24
> **SalsaShark said:**
> Hmmm, the only information I can find is "Realtek High Definition Audio"

Can you find your card with 'lspci'? 

Sounds a bit like an Intel HDA card - see [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by executorvs on 2009-06-24
/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
is the options file I was talking about, the link above this one reiterates what I was saying about identifying your Realtek audio.

also what I was talking about with the sound properties and making sure they are on (you might want to make sure the card is set properly in alsa-base as it changes the options you'll find under properties for your sound)

Right-click on the speaker in the uper right corner of your screen and select 'open volume control' under the device dropdown select the alsa mixer
at the bottom select the preference tab and make sure all of your speaker/audiochannels are checked return to the volume controll and make sure any of your sound-sliders are all the way up.

---

### Post by Chalfont on 2009-06-24
> **executorvs said:**
> /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
is the options file I was talking about, the link above this one reiterates what I was saying about identifying your Realtek audio.

also what I was talking about with the sound properties and making sure they are on (you might want to make sure the card is set properly in alsa-base as it changes the options you'll find under properties for your sound)

Right-click on the speaker in the uper right corner of your screen and select 'open volume control' under the device dropdown select the alsa mixer
at the bottom select the preference tab and make sure all of your speaker/audiochannels are checked return to the volume control and make sure any of your sound-sliders are all the way up.

Hi Exec, thanks for your help in the other thread.  In this post, I didn't begin to understand the first two paragraphs, but did the right clicking and found some of the sliders at about 60%.  Sound levels much better, similar to windows on the same machine.  **Thanks**

By the way, this netbook also has realtec sound card of some sort.

---

### Post by executorvs on 2009-06-24
we could try and get the sound a little better by double checking to make sure it's configured correctly. look at raboofje's post above mine and follow the link.
if your volume is doing what you need though there may not be much point.

*side note:* under the volume control window the preference button loads the preferences for which ever device is currently selected. so the alsa-mixer preferences will be different from capture:, capture monito:, or OSS-mixer preferences. keep this in mind when setting up skype or anything that uses a mic as it may come in handy.

---

### Post by SalsaShark on 2009-06-24
Thanks guys.  I went to that link and followed the steps, but there's no change, I can still barely hear the quieter parts of a movie on full blast.  The output of "cat /proc/asound/card0/codec#* | grep Codec" is:

Codec: Realtek ALC268
Codec: Conexant ID 2c06

I tried both "acer" and "acer-aspire" for the model and neither of them worked.  The preferences changed but the sound is still very low.

However, when I run "sudo lshw", under Audio device it says:

*-multimedia
          description: Audio device
          product: MCP67 High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

And I'm sorry but I just can't make sense of the "dmesg" output

---

### Post by executorvs on 2009-06-24
did you try these instructions as well?

> **executorvs said:**
> what I was talking about with the sound properties and making sure they are on (you might want to make sure the card is set properly in alsa-base as it changes the options you'll find under properties for your sound)

Right-click on the speaker in the uper right corner of your screen and select 'open volume control' under the device dropdown select the alsa mixer
at the bottom select the preference tab and make sure all of your speaker/audiochannels are checked return to the volume control and make sure any of your sound-sliders are all the way up.

frequently jaunty defaults some of the channels at about 40% volume for reasons unknown.

> **executorvs said:**
> *side note:* under the volume control window the preference button loads the preferences for which ever device is currently selected. so the alsa-mixer preferences will be different from capture:, capture monito:, or OSS-mixer preferences. keep this in mind when setting up skype or anything that uses a mic as it may come in handy.

---

### Post by SalsaShark on 2009-06-24
Yup, all checked and at 100%

---

### Post by executorvs on 2009-06-24
which model acer do you use? I have the aspire 6930G and had some issues with the Tuba system, but it used the ALC889 chipset.

---

### Post by SalsaShark on 2009-06-24
I've got an Acer Aspire 7520-5168

---

### Post by philcamlin on 2009-06-24
go to volume and set all bars to 100%

---

### Post by benerivo on 2009-06-24
I got louder top sound by using OSS4 rather than alsa/pulseaudio. Have a look at [this page]("https://help.ubuntu.com/community/OpenSound"). Also check [this search link]("http://www.google.co.uk/search?q=oss4+louder&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a").

---

### Post by executorvs on 2009-06-24
I followed some of the advice at [http://www.linlap.com/wiki/acer+aspire+6930](http://www.linlap.com/wiki/acer+aspire+6930) to get my HDaudio working. you may want to give it a try.

---

### Post by SalsaShark on 2009-06-24
I gave benerivo's method a shot, and there's not much of a change.  However I've been fiddling with it and I've noticed that the maximum volume is 25.0 dB.  That is, when I run: "ossmix vmix0_outvol" it returns "Value of mixer control vmix0-outvol is currently set to 25.0 (dB)".  Is there any way I can just increase the maximum value that vmix0-outvol can take?

---

### Post by SalsaShark on 2009-06-25
Damn, now there's no sound in flash...

---

