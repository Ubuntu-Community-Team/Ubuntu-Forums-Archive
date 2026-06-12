---
title: "Unable to use Audio Recorder"
date: 2014-07-11
forum: Multimedia Software
---

### Post by GwibberFooey on 2014-07-11
I have 64 bit Kubuntu 14.04
I want to use Audio Recorder to record some sounds that I am streaming through my web-browser.
In the Audio Recorder application I click on Start recording and then after some time I click on Stop recording.  Therefore a mp3 or flac file is created. When I play this file in Minirok the file contains no sounds.  How can I fix this problem?

---

### Post by nknwn on 2014-07-11
Don't know 'Audio Recorder', but I've found in some programs when I want to capture sound I need to plug in headphones and direct the settings in the capture program to record from the headphones.

---

### Post by Dennis N on 2014-07-11
Empty recordings - check these settings:

Setting in Audio Recorder: 
Audio settings > Source: Built-in Audio Analog Stereo (Audio Output)

Setting in Pulse Audio Volume Control:
Open Pulse Audio Volume Control > Configuration tab > Built-in Audio - Profile: Analog Stereo Duplex

---

### Post by GwibberFooey on 2014-07-13
Thanks for the help so far.
How can I open Pulse Audio Volume Control?

---

### Post by Bucky Ball on 2014-07-13
Should be in your apps menus under 'Multimedia' or 'Sound & Video'. Not sure what it would be called in Kubuntu. You can also use a terminal, simply:

pavucontrol

---

### Post by GwibberFooey on 2014-07-13
The configuration tab in Pulse Audio Volume Control contains two dropdown lists with the title Built-in Audio. The first contains the options: Digital Stereo (HDMI) Output, and Off.  The second contains the options: Analog Stereo Duplex, Analog Stereo Output, Digital Stereo (IEC958) Output + Analog Stereo Input, Digital Stereo (IEC958) Output, Analog Stereo Input (unplugged), Off.  When I set the first one to Digital Stereo (HDMI) Output and set the second one to Analog Stereo Duplex then I continue to get empty recordings. Or if I set the first dropdown list to Off and the second one to Analog Stereo Duplex then I still continue to get empty recordings.

---

### Post by Bucky Ball on 2014-07-13
Don't bother about the configuration tab, you want the output, input, recording and playback tabs, primarily. Get a stream going (i.e. play something that you intend to record) open PAVControl and have a look at playback. The stream should be there labelled as coming from the software you're playing it with/through. Play an audio track, check 'Playback' to make sure there's a stream from the software, check 'Output and see which device it is being directed to. 

If you're not using the digital/HDMI, mute that in the input/output tabs for now to take that out of the equation.

---

### Post by Dennis N on 2014-07-13
Configuration tab: the OFF/Analog Stereo Duplex is my combination. See (image1.png) for my configuration tab.

When recording, you should see activity in the bar enclosed in the red box (image2.png). Otherwise, it's not working.

When recording, the recording tab on PA Vol Control should show Audio Recorder recording from Built-in Audio Analog Stereo (image3.png). This tab should show activity when recording. Be sure this is not muted as that would result in an empty recording as well.

I have Output devices tab on PA Vol Control as Analog Output. Input Devices is Line-In.

---

### Post by GwibberFooey on 2014-07-13
For me to record sounds being played in the web browser I have to first start recording on th Audio Recorder application, then I have to return to the Recording tab in the Pulse Audio Volume Control application and then on the drop-down list titled "Audio Recorder: Record Stream from" I must select the option "Monitor of Built-in Audio Analog Stereo".

It would be excellent if everytime I make a new recording it would not by default return to the other option, "Built-in Audio Analog Stereo".  If this were the case then making an audio recording would involve only the Audio Recorder application. Instead the procedure involves Audio Recorder and Pulse Audio Volume Control.

---

### Post by Dennis N on 2014-07-13
> **GwibberFooey said:**
> For me to record sounds being played in the web browser I have to first start recording on th Audio Recorder application, then I have to return to the Recording tab in the Pulse Audio Volume Control application and then on the drop-down list titled "Audio Recorder: Record Stream from" I must select the option "Monitor of Built-in Audio Analog Stereo".

It would be excellent if everytime I make a new recording it would not by default return to the other option, "Built-in Audio Analog Stereo".  If this were the case then making an audio recording would involve only the Audio Recorder application. Instead the procedure involves Audio Recorder and Pulse Audio Volume Control.

Since you marked this "solved", I see you have it working. The problem you mention about needing to open Pulse Audio Volume Control and reselect "Monitor of Built-In Audio Analog Stereo" I have never experienced in quite a few installations of Audio Recorder over the years. So I think something is not right with that.

---

