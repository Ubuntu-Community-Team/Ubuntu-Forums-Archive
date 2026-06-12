---
title: "HOWTO: Adding a delay on microphone capture to sync with webcam capture"
date: 2008-10-31
forum: Multimedia Software
---

### Post by patrickballeux on 2008-10-31
**Microphone Delay**

When you are broadcasting with WebcamStudio for GNU/Linux, you video capture from
your webcam may be out of sync with out sound capture from your microphone.
Since there is some processing on the video, there can be a small delay of
1-2 seconds...

In the "microphone" folder (under /usr/lib/webcamstudio/microphone or ./webcamstudio/microphone), there is a small script that will "re-synchronise" your sound with your video
capture by addind a small delay on the microphone. Maximum delay is 5 seconds.

See [http://webcamstudio.wiki.sourceforge.net/Microphone+Delay](http://webcamstudio.wiki.sourceforge.net/Microphone+Delay) to download the files...


**How to install**

Actually, it is quite simple:

    * Run "gstreamer-properties" from a terminal and set your sound capture to pulseaudio and selecting the "ALSA sound card" and not the default.
    * Copy the "default.pa" file in your ~/.pulse folder.
    * Run "pulseaudio -k" in a terminal, then "pulseaudio -D" (or login/logout)
    * You are now ready to use the script...
    * Make sure that you have install "pavucontrol" as you may need to redirect some audio stream for the Flash plugin/or other applications
    * In a terminal, run the script microphone-delay (put it in your ~/bin folder for convenience. This will capture your *real* microphone and redirect the sound to a fifo file /tmp/music.input. This is a virtual input sound in pulseaudio.
    * In pavucontrol, you should see a new sound source "/tmp/music.input".
    * Start your Flash player on your site or your application. Redirect the capture stream to the Fifo file instead of the Alsa source.
    * You should now have a delay of 1 seconds on your sound capture from your microphone.



**Customizations**

Edit the script to set a different delay from 0 to 5. Also, since this is the gstreamer framework, you can add filter or equalizer to the pipe to have a better sound.


:guitar:

Have fun!

---

