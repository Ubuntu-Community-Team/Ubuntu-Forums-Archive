---
title: "USB Wireless Audio"
date: 2009-01-02
forum: Multimedia Software
---

### Post by rcool on 2009-01-02
I apologize if this is not the correct place to post this, one of the mods has my permission to move it to a more appropriate area if needed.

I wanted to post this just in case someone else tries to Google it like I did;)

I have a JVC RX-D301 A/V Receiver that offers USB Wireless connectivity. It comes with a USB dongle that transmits to the receiver (it seems to broadcast in the 2.4GHz range as I get some interference with microwave ovens and 2.4GHz cordless phones). This will let you use the receiver as the speakers for your computer if it is not handy to string a wire between them. It works pretty well in Windows as I believe all I had to do was tell Windows to use the USB sound card. I had assumed that it would not work w/ Linux so I didn't try it until yesterday.

Right after plugging the wireless dongle into my USB port I was able to go to System -> Preferences -> Sound and choose "GENERIC USB Speaker USB Audio OSS" from the Sound Playback dropdowns (GENERIC USB Speaker USB Audio ALSA always gave me an error though). I could then click Test and I was able to hear the test tone from my home theater speakers. The problem was that I could never get any other sounds to play through those speakers.

I finally found a post online where someone was trying to get their USB speakers to work, and the same procedure has worked for me.
[LIST=1]
[*]Install PulseAudio Volume Control if not already installed```
sudo apt-get install pavumeter
```(Or find in Synaptic)
[*]Start audio that you want played on receiver speakers (youtube, VLC, etc...)
[*]Applications -> Sound & Video -> PulseAudio Volume Control
[*]From the Playback tab, click the down arrow on the right of (or right-click on) the audio source (ALSA Plug-in [Firefox]: ALSA Playback, etc...) 
[*]Choose Move Stream
[*]Select the USB Audio choice.
[/LIST]
You can also go to the Output Device tab of PulseAudio Volume Control and click the down arrow to the right of (or right-click on) the output device of your choice and set it as the default. I haven't actually tried making the USB Audio the default as most of the time we want the computer to use the speakers here at the computer, but I am assuming that making USB default would cause all audio to use the USB output unless manually changed as in step 4-6 above.

I hope this helps save someone some time!

---

### Post by markbuntu on 2009-01-02
You can also open the pulseaudio device chooser and go to Configure Local Sound Server/Simultaneous Output and check the box Add virtual device.......

This will add a device in the pulse audio volume control for simultaneous output on all the hardware devices so that you can have sound in both places if you want.

---

### Post by rcool on 2009-01-02
So it does. Very cool! :)

Thanks!

---

### Post by erikthedrink on 2009-09-08
It will use the USB speakers for all applications, unless you unplug them.:lolflag:  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

