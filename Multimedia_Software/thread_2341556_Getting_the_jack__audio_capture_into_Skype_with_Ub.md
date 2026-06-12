---
title: "Getting the jack  audio capture into Skype with Ubuntu 16.04"
date: 2016-10-29
forum: Multimedia Software
---

### Post by Boorhin on 2016-10-29
I have been trying to get my Jack audio capture (a microphone through my USB sound interface) into Skype so I can call from my computer but without success.

In the tested solutions, I tried this:
[https://ubuntuforums.org/showthread.php?t=1553534](https://ubuntuforums.org/showthread.php?t=1553534)
But Pulse audio device chooser is not available for 16.04

I tried to get rid of the ALSA bridge but that was without impact.

My current setup which is the only one working for recording/playing sounds at the moment is:
Cadence + jack 
with Jack bridge ALSA -> pulse audio -> Jack,
 and Pulse audio bridged to Jack
In Skype, in the setting I can see that it is managed by pulse audio so I cannot choose my source.
In Pulse Audio, there is no input listed because I use the Jack sink.
I cannot see Skype in Jack connections (unlike Mac OS apparently). Is that normal? I manually installed Skype before upgrading from 12.04 to 16.04 is that the reason? I have Skype 4.3.0.37 so it is the latest but it does not appear installed on the Software manager.

I have read that you can manually add the microphone of your webcam into pulse audio but that does not sound 'clean' to me.

Any advice or direction of research are most welcomed

Boorhin

---

### Post by lammert-nijhof on 2016-11-02
I rely completely on pulse audio. For Skype you need to install "pulsaudio volume control". Start this program and Skype. Use the Skype test call. When the lady speaks you can select your output device in the tab "playback" from the "pulseaudio volume control". When you supposed to speak you can select the microphone in the tab "recording". That setting will be remembered and the coming months everything should be OK.

---

### Post by Bucky Ball on 2016-11-02
Welcome. Sheesh. You shouldn't need to do all that on a standard Ubuntu install and you definitely don't need Jack for this or in a standard install. This is a standard install?

Could you try this. Close everything, plug in your USB mic and reboot the computer. Open a terminal and run this command:

```
lsusb
```

Post the output here between code tags (see how in my signature below).

Install Pulseaudio Volume Control. Launch it. Open Skype and launch that. In 'Options', make sure it is set to Pulse. It shouldn't let you set it to anything else anyway. Start a test call.

It's best to open PAVControl before making the Skype test call so when you do you can check the 'Playback' tab. Do you see the Skype stream there? Check the 'output' and 'input' tabs. Do you see your input and output devices in the 'Port' window? If not, hit the drop down 'Port' list and see if they are on that list. If so, select. You may need to experiment.

Any luck?

Any audio stream you play from any source/app is going to be routed to and handled by Pulse. You should be able to see it and control it right there in the 'Playback' tab and the 'Output' tab. Anything you input should be visible in PAVControl in the 'Input' tab. You select the input and output devices there. 

By routing Pulseaudio to Jack you are going one redundant step beyond. Skype is already routed to PulseAudio. You possibly can't route Skype directly because it is already going to Pulse, as it should be on a standard install. :)

It would get you help faster if you could more specific about what exactly you are trying to do. Use the mic from a USB video camera???

(You installed Skype from the Ubuntu repositories? It's generally as easy as install> launch> make a call with perhaps a little tweak with PAVControl ...)

---

