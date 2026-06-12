---
title: "Sound Juicer does not show custom extraction profiles"
date: 2008-06-16
forum: Multimedia Software
---

### Post by EnforcerMP on 2008-06-16
Sound Juicer does not seem to want to allow me to select the custom extraction profiles I create.

I want to rip CD tracks to 192 kbps CBR MP3. Here's what I did:
[LIST=1]
[*]Launched Sound Juicer and opened the Preferences window.
[*]Clicked on the Edit Profiles button.
[*]Created a new profile with the New button, named it "CD Quality, MP3, 192 kbps"
[*]Edited the new profile so that it has the following properties:
[LIST]
[*]Description: <no description>
[*]GStreamer pipeline: ```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=192 ! id3mux
```
[*]File extension: mp3
[/LIST]
I checked the box labelled "Active" and clicked the button labelled "Close". The new profile appeared in the window labelled "Edit GNOME Audio Profiles."
[/LIST]
However, the new profile did not appear in the choice box labelled "Output format" in the Preferences window of Sound Juicer. Restarting Sound Juicer did not work, and neither did rebooting my computer.

I'm running 32-bit Ubuntu 8.04 on my desktop, and 64-bit Ubuntu on my laptop. The problem occurs on both.

Has anyone run into the same problem? If so, have you managed to fix it? How have you done so?

Thanks!

---

### Post by juah on 2008-06-19
You need to have gstreamer0.10-plugins-ugly-multiverse installed before you get mp3 pipelines running (and visible). In Addition to that I think you should have

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3mux

Still have to restart Sound Juicer after editing profiles, but I think these will do it.

check 'gst-inspect-0.10 lame' for further information

---

