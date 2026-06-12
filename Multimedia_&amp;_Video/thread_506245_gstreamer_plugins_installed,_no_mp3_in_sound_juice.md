---
title: "gstreamer plugins installed, no mp3 in sound juicer"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by hkb11001 on 2007-07-21
Hi,
I know there are a number of similar threads on this subject, but none that I could find that quite fit my situation, so I thank you for your patience.
This pertains to a new install of 7.04.
I've installed all Gstreamer packages from Applications > Add-Remove > Sound & Video. Those include "GStreamer extra plugins" (from the "ugly" set),  "GStreamer ffmpeg video plugin", "GStreamer plugins for aac, xvid, mpeg2, faad" (from the "bad" set--multiverse variant), and "Gstreamer plugins for mms, wavpack, quicktime, musepak" (also from the "bad" set).
However, under Sound Juicer > Edit > Preferences, I still have no option for mp3 under "Output Format".  There is the option for MPEG-4, but not mp3. 
What have I done wrong or what still needs to be installed? Supposedly the extra plugins (from the "ugly" set) provided for mp3 support.

Thanks!!

---

### Post by martin6 on 2007-07-22
I had the exact same problem. I fixed it by installing additional "gstreamer" packages.

Go to "Synaptic" and search "gstreamer", choose the most of gstreamer-0.10 version packages (as of this date July 22, 2007), especially fluendo-mp3 one, and install them, restart "Sound Juicer" then the MP3 package should be there.

Cheers

---

### Post by RomeReactor on 2007-07-22
Hi. For that, in SoundJuicer you'll need to go to **Help->Contents->Preferences** and scroll the page to the bottom, where it explains how to enable ripping in MP3. It goes like this:

Click on "Edit->Preferences->Edit Profiles->New", name the profile **mp3**, highlight the newly created profile, press "Edit" and set the **Gstreamer Pipeline** to read:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3v2mux
```
Set the **File Extension** to **mp3** and select the Active check box. Make sure you have the **Gstreamer Lame** plugin installed:
```
sudo apt-get install gstreamer0.8-lame
```
Restart SoundJuicer.

---

### Post by hkb11001 on 2007-07-23
Thank-you for your timely response.
Unfortunately, I still don't see the option for ripping to MP3 in Sound Juicer; likewise with Banshee
Any other ideas?

Thanks again.

---

### Post by hkb11001 on 2007-07-23
Same thing--still no option for ripping to MP3s in Sound Juicer or Banshee, even though the profile is listed when I go to edit it, and it is active.

Any other ideas???
Is it possible to have too many plugins installed? I don't like having more than what's necessary. That said, I did originally install all the grstreamer plugins indicated under Applications > Add-Remove > Sound & Video.

Thanks again!!

---

### Post by RomeReactor on 2007-07-23
Open SoundJuicer (or load an audio CD, so SoundJuicer opens), go to Preferences, and change the Output Format--the option at the bottom--to **CD Quality, MP3 (MP3 audio)**.

---

### Post by hkb11001 on 2007-07-24
Thanks again, but that didn't work either.
Anyhow, after doing some more digging around, I found someone with what read like virtually the same problem. I tried their solution and it worked! That was to install ***gstreamer0.10-plugins-ugly-multiverse***.

The whole thing seems odd to me that there are no clear instructions as to exactly what plugins are required; moreover after installation of all the gstreamer plugins as listed under Applications >Add-Remove > Sound & Video were not sufficient! Quite a surprise and disappointment!

Anyhow, a related question:
Regarding Sound Juicer, do you know what the significance is of the differing GStreamer pipelines for "MP3" (as instructed in the Sound Juicer Help, and you quoted to me in the previous post) and that of "CD Quality, MP3"?
For the "MP3" as indicated in Sound Juicer Help, it is:
**audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3v2mux**

For "CD Quality, MP3" it is:
**audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux**

Thanks!!

---

### Post by RomeReactor on 2007-07-25
One string seems to be encoding in constant bitrate:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc **vbr=0 bitrate=192** ! id3v2mux
```
while the other is encoding in variable:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 **vbr-quality=6** ! id3v2mux
```

---

### Post by hkb11001 on 2007-07-25
Yeh, so what's the significance of this?

---

### Post by RomeReactor on 2007-07-25
Variable bitrate usually results in better quality than constant. Let's say you encode X song at 192 constant; it means that, if you take a sample 1 second where there is great a variety of instruments playing, it will measure Y amount of Kb.. If you take another sample 1 second (this time of pure silence) it will still measure that same Y amount of Kb.

In variable. the encoder is smart enough to allocate more space (and therefore more quality) to segments where there is a wider range of sounds playing, and reduce the space allocated where less diversity of sounds are (or even silence).

This [Wikipedia article]("http://en.wikipedia.org/wiki/Variable_bitrate") explains it better.

If this is not the answer you were expecting, please explain what you mean by "significance".

---

### Post by hkb11001 on 2007-07-26
A better word than "significance" may have been "consequence". Your explanation was helpful and I can read more about it at the link you provided and elsewhere.

Thanks for all your help!!

---

