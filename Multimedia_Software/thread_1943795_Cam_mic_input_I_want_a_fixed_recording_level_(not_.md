---
title: "Cam mic input: I want a fixed recording level (not automatic gain). How do I do it?"
date: 2012-03-20
forum: Multimedia Software
---

### Post by FulciLives on 2012-03-20
Hello

Does anyone know if it is possible to fix the recording level of a mic input instead of the mic gain being automatic. In other words I don't want the mic input level to raise or lower with the loudness of my voice.

I have a Logitech c525 cam and using the built-in mic on it.

I'm also using Ubuntu 12.04 Beta 1

---

### Post by FulciLives on 2012-03-20
After some google searches I found a solution that worked for me.

Here is the link:

[http://groups.google.com/a/googleproductforums.com/forum/#!category-topic/chat/voice-and-video-chat/DWiv542wDw0](http://groups.google.com/a/googleproductforums.com/forum/#!category-topic/chat/voice-and-video-chat/DWiv542wDw0)

For those of you who are lazy here is what the link says:

> Thank you for reporting this issue. This issue is caused by the use of automatic gain control (AGC) on certain ASUS hardware. We are working to provide a checkbox for disabling AGC, but for now you can disable it via the following steps:

1) Open your favourite text editor (e.g., Applications -> Accessories -> gedit Text Editor)
2) Open the file at "/home/<your username>/.config/google-googletalkplugin/options" (create it if it does not exist)
3) Change the "audio-flags" line to "audio-flags=1" (or add it if it is not present)
4) Save the file and close it.
5) Close all Gmail/iGoogle/orkut tabs and then re-open Gmail.

In my case the Options file already existed and the "audio-flags" line was set to 3 so I changed it to 1 and that seems to have turned of AGC. I can now change the input volume via the "Sound Setting" and it stays (no longer auto adjusts).

I'm setting this as SOLVED now.

---

