---
title: "Strange click sounds being heard with Skype and Sound Recorder"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by Handssolow on 2007-11-23
I want to set up Skype Beta now that there's a webcam function. I'm getting interference noise of strange clicking sounds variable in timing but about one a second when I use either the webcam's microphone and I think also if I use a separate microphone. It's my wife's PC with an Asus A7V880 mobo, on-board VT8233/A/8235/8237 AC97 Audio Controller plus Logitech Quickcam Pro 4000 webcam.
Under Skype or Sounder Recorder I'm hearing rather loud clicks at a frequency of about one a second. It's not a Skype issue because it's there with Sound Recorder. Apart from this I can year my own recorded voice clearly with a Skype test call or using the Sound Recorder Application but the extra click sounds need eliminating.

This is a dual boot PC with Xp on the other hard drive and no extra clicks occur using the webcam with Skype.

Where are these one second clicks coming from?

---

### Post by Handssolow on 2007-11-25
I have been unable to use the webcam's microphone in a Logitech Quickcam Pro 4000 with an Asus A7V880 mobo with VIA 8237 AD1888 audio chipset. As mentioned before I could record my voice with Skype and Sound recorder but not without the extra  interference sounds of random clicks occurring about every second. Perhaps the problem occurs with this mobo if the microphone is connected through a  USB port?

Instead I have been able to use a separate microphone with the following-
~$ asoundconf set-default-card V8237
In Skype I've selected VIA 8237 (hw:8237,0) for Sound in,Sound out and for Ringing. In System>Preferences>Sound I selected VIA for the Playbacks, Alsa Mixer for Capture and for the default mixer the Via 8237 Alsa Mixer. I needed the Mic boost option selected and using the useful gamix package I could easily adjust the microphone Playback control to stop microphone sounds coming out of the speakers.

---

### Post by arpad9 on 2008-03-18
Did you ever solve this problem w/o a workaround?  I'm having the same problem with a webcam pro 9000 and an Asus A8NSLI mb.

---

### Post by Handssolow on 2008-03-18
arpad9,  the Asus A7V880 based PC was my wife's and I was unable to get the  Logitech  webcam's microphone to work without also getting regular loud click sounds so I had to use a separate microphone with Skype Beta. At least this combination did work. I was finally more successful with the webcam's microphone on my Asrock 939 Dual-VSTA  but only after several hours of Forum searches and experimenting with the configuration. It's been  my PC which we've been using for webcam chats with our son in Chicago.

With some PC problems after I'm unable to find a software solution I look to change the hardware for example,  I installing a wired link to my router after all the bother with my RT2500 based Wlan card. Perhaps things will be better with Hardy Heron.

---

