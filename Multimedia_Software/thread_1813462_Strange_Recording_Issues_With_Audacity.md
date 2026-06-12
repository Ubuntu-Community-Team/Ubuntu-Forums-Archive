---
title: "Strange Recording Issues With Audacity"
date: 2011-07-27
forum: Multimedia Software
---

### Post by dniMretsaM on 2011-07-27
I listen to a lot of music and I often record it from Internet radio to put on my computer/iPod (a nice way to get free music legally). However, ever since switching to Linux, I've not been able to do that. For awhile it couldn't get it to record any streaming audio, but I finally got that worked out. Now when it records, the quality is absolutely horrible. What I hear on the speakers sounds fine, but what Audacity records is littered with hundreds of skips. See the attached picture for a comparison (Both were recorded with Audacity. The one on top was recorded on Windows, the one on the bottom was recorded just now.) Any ideas on how to resolve this?

---

### Post by dniMretsaM on 2011-07-28
Bump.

---

### Post by dniMretsaM on 2011-08-02
Bump again. Would really like to get this fixed. Or a suggestion for another program that I can record streaming audio with.

---

### Post by ankspo71 on 2011-08-03
Hi,
I think I can help. It took me about a year to figure out how to record audio in Linux, but I finally figured it out and this should help you too.

First, you need to install a package called "pavucontrol". When it is installed you will see an application in your menu called "Pulse Audio Volume Control".

Next, start playing some audio files or radio streams.

Now run audacity and press the record button.

Now start "Pulse Audio Volume Control".

When it opens click on the "Recording" tab.

You should see "Alsa Plugin [Audacity]: Alsa capture from:"

Now choose "_Monitor of_ your-audio-card-xx" from the dropdown menu.

You should instantly see some better results in the way Audacity is recording now in both Pulse Audio Volume Control and inside Audacity.

Close Pulse Audio Volume Control. It will automatically keep the settings. Now you can start recording in Audacity.

It works good for me except I have no control (at all) over the sound input volume... but that just might be because of my soundcard though.

Also, you might need to make some settings adjustments at Audacity > Preferences > Devices. (ex: choose between pulse and alsa, or audio ports etc) The default options work for me, except I changed it from mono to stereo.
Hope this helps.

---

### Post by dniMretsaM on 2011-08-03
Well, I can't tell if it works or not. When I record it's to quiet for me to hear anything... I have the same problem with the input volume. So I'll keep looking. Thanks for the help though.

---

