---
title: "sound options, recording and skype and I am confused"
date: 2010-12-08
forum: Multimedia Software
---

### Post by beew on 2010-12-08
I am a bit confused. There are two set of sound control, there is the pulse audio volume button and there is the alsa mixer. I am not sure which one controls what and how do they relate to each other.

I am trying to set up skype and using the gnome sound recorder to test the output. I am not sure how to configure the sound system so that sound recorder would record the mic's output, right now I think it is capturing output from the sound card. I play some music from the internet and it captures it flawlessly, but I can't make it record anything I say, so skype is not working either. This is in Lucid.

On the other hand I have a Maverick installation, sound recorder captures output from the mic and skype is working perfectly on that one, though pulse audio has been removed in that installation. The sound recorder also looks a bit different, it has an extra option of choosing input option. On the other hand I can't make it to record from the sound card.

There is a third Maverick install, it has pulse audio and it doesn't record sound from either the sound card or the mic. The uv meter is always feeble.

I am sorry if this is all a bit confusing because i am quite confused. I guess my question boils down to
1) How to configure the system's mic (for Skype)'

2) How to control what sound recorder records or captures.

3) Where do I find instructions or help menus for the options in alsa mixer and pulse audio. As I said I am not sure which does what and why there are two sets of control.

---

### Post by labinnsw on 2010-12-10
The best way to test Skype sound input is to "Make a test call" under Options>>Sound Devices

Attached is my config for pulse audio. Extract to see the config.

---

### Post by beew on 2010-12-12
Thanks.

The sound works in Skype (though not the video, I have started a thread on "absolute beginner talk"

What I want is actually a clarification of which does what as there are so many different sound modules it is rather confusing. (Pulse Audio volume control, alsa mixer, and then another sound button under System > Preference, how do they work together, is there any hierarchy?)

---

### Post by labinnsw on 2010-12-13
I couldn't answer all your questions so I tried to answer what I could. What I do know about the sound thing is that sometimes, depending on what other software you use, you need both alsa-mixer and pulse audio. e.g. I could not get any sound recorded through my headset with recordmydesktop until I installed gnome-alsamixer, but skype and audacity worked with pulse audio and alsa-utils alone installed.

---

