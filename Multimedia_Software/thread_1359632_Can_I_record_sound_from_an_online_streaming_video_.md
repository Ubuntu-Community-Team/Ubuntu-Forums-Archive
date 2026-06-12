---
title: "Can I record sound from an online streaming video with Audacity?"
date: 2009-12-19
forum: Multimedia Software
---

### Post by kwabena39 on 2009-12-19
Can I record sound from an online streaming video with Audacity?

I heard in one Youtube video that you can, but they showed a dropdown box where you change from Microphone to Stereo Mix

My audacity has NO such drop-down window to set the input (i.e., Microphone, Stereo Mix, and so on)

When I press record, all I get is a flatline.  Is it possible, in Ubuntu, to record audio from an un-savable flv video?

(I'm trying to record a cbsnews video using Xvidcap to capture the vid, and Audacity to capture the audio, and then reassemble them)

---

### Post by lessmemorelove on 2010-01-02
I just posted this in another thread today:

> I just got this to work yesterday. I found the fix in another spot on the forum but I don't remember where. This is all assuming you have karmic.

1. Edit Audacity pref. under "Devices" and change everything to pulse. My host choices were only oss and alsa so i left it alone but make sure you change everything else to pulse.

2. Install pavucontrol in Ubuntu. The first time you ever use a recording program you will have to use pavucontrol to edit the recording settings. It seems to remember your choices after reboots so that is good.

3. pavucontrol should be in your menu as PulseAudio Volume Control. Open it and under the recording tab you will not see anything. leave it open and open up audacity. hit record in audacity. while audacity is recording, check pavucontrol and under the recording tab you should see audacity now. It will say alsa capture from and then show a box. click on that box and select monitor of internal audio. check audacity. you should be recording now.

---

### Post by kwabena39 on 2010-01-06
1. I don't see Karmic in repository

2. I started Audacity with padsd audacity, or whatever, to start audacity with pulse.

I went into Pulse Preferences but it was all Greek to me.  I didn't understand a thing.  So I started playing around with sliders

Everything I tried so far turned up nothing.

I can't hear a record and I can't record a record.

Every tutorial i've read on Audacity and pulse and oss/dev and everything has neither made sense to me nor has it worked.

---

### Post by elvino on 2010-01-14
> **lessmemorelove said:**
> I just posted this in another thread today:
I just wanted you to know that after two weeks, yes, 14 days, your message finally turned on the light for me as to how Pulseradio is configured! I could not, until now, work out how to have different configurations for different applications and now I know!

Thanks a million!

---

### Post by alexthunder on 2010-01-15
Pulse works fine for me. Thank a lot

---

### Post by bobdobbs on 2010-03-10
Where does audacity store the recorded audio ?

---

### Post by mike.headon on 2010-03-24
Thanks! I have been searching for this solution for years!

---

