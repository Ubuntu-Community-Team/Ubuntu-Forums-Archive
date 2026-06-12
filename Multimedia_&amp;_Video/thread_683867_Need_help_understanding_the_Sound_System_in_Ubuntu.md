---
title: "Need help understanding the Sound System in Ubuntu to fix Recording"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by airbornespent on 2008-01-31
Update: I just need to change the system's default sound capture device to USB Audio or tell java specifically to use the USB device for recording.

I am working on a laptop that is used by some researchers here to 0record audio with a java app. The internal mic got broken somehow and has a ton of noise now so I advised them to buy a USB sound input device. The system detects the USB device fine and plays back to it when I select it in Sound Preferences and click Test. It is the Sound Capture option that is broken, when I test recording with any capture device I get the following error: ```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```

I installed Audacity to test recording and it records from the USB device and the mic input just fine when I select USB or ALSA from the dropdown options. So I know I can record from the USB device because **Audacity works**.

Next I tried Sound Recorder, when I select ALSA as the capture device in preferences, sound recorder records from the mic input. When I select USB Audio as the capture device Sound Recorder will not run and gives this error: ```
Your audio capture settings are invalid. Please correct them in the Multimedia settings.
```

I am worried that I won't be able to specify to the java app what capture device to use like I can with Audacity and it will use the operating system default and be plagued by Sound Recorder's problem when I select USB Audio for capture.

---

### Post by ptoye on 2008-02-13
I'm having the same problems. If there's someone here who knows how to record from USB sound, could they please put the answer up as a FAQ? Or add it to the community documentation, which only has sections for playback and sound editing.

Peter

---

