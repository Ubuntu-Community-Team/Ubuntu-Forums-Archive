---
title: "Zoom web app: no microphone in Firefox, no camera in Chromium"
date: 2020-03-24
forum: Multimedia Software
---

### Post by jmnorvell on 2020-03-24
Firefox never asks for microphone permission for the Zoom web app but allows the webcam camera. Since it never asks, I can't authorize this website. Chromium does the same thing for the camera but allows the microphone. I don't use the Zoom app because my screen resolution is high and the controls are almost invisible on the screen.  Any advice?

---

### Post by TheFu on 2020-03-25
> **jmnorvell said:**
> Firefox never asks for microphone permission for the Zoom web app but allows the webcam camera. Since it never asks, I can't authorize this website. Chromium does the same thing for the camera but allows the microphone. I don't use the Zoom app because my screen resolution is high and the controls are almost invisible on the screen.  Any advice?

I've never used zoom, but for the few other virtual meeting sites, here's my steps.

Assuming pulseaudio hasn't crashed. The camera is completely separate. The browsers need to have webRTC enabled and allowed. Finding all the little settings to make this possible if you've previously disabled it can be a hassle.  For myself, I find it is usually just easier to run the browser inside a **firejail** with a --private sandbox so none of the prior settings can be seen, accesses, stored.

[LIST]
[*]Shutdown chromium.
[*]Shutdown Firefox.
[*]Open pavcontrol.
[*]On the far right tab, it lists all the different devices the system has. You want exactly 1 microphone enabled and exactly 1 output (speaker or headset) enabled.  All the other devices need to be "_off_".  If you use a headset, there might be only 1 device and the selected mode needs to be "duplex" so it gets used for both the microphone and the speaker output.
[*]Check that the Playback and Input tabs have the correct device selected and enabled. You should be able to see the mic monitor move as you speak.
[*]Close pavcontrol.
[*]Open chromium, browse to the website, join the meeting.  When joining, you should see either 1 or 2 popups asking for permission to use the webcam and/or the microphone.  Some webRTC meeting places haven't gotten their Firefox javascript stuff perfect, so best to use a Chromium-based browser for now. There are a bunch of those.
[/LIST]

If you don't see the pavcontrol tabs and all the devices, then pulseaudio has probably crashed.  You can run **pulseaudio -k** to really kill it, wait a few seconds, it should respawn automatically.  If it doesn't, then you can run the daemon manually.  Do not use sudo. Open a terminal, make it small, run **pulseaudio -D** give it 10 seconds to start, don't know why it takes so long. Then start over at the top with my list of steps.

PulseAudio prefers to automatically select the most recent audio devices connected.  For headsets, that means that unplugging them and reconnecting them to the system, slowly, wait 5+ seconds between removal and insertion to give udev time to see the changes.  I've also needed to unplug my 2.5mm headphone jack for PulseAudio to notice that speakers were connected.

For my setup, there can be 1 camera, 3 different microphones, and 2 different speaker/output devices.  It becomes complicated quickly.

And if you want to change the output device, don't forget that you've turned it off in pavcontrol previously, so it will need to be enabled with the correct settings later. Start in the far right tab.

Anyways, that's what I do for the audio side of things.  After you get a config working a few times, you'll learn to get the devices on/off that you need, have them in the correct input (digital vs analog) and correct output (too many possible output configs to even list here) that work on your equipment.

---

### Post by jmnorvell on 2020-03-26
Thanks for the detailed response! It's now working in Chromium, so I'm good. I found a control within the Chromium setting I was missing. Still no joy with Firefox, but oh well...

pavcontrol: This is system settings module, right? I couldn't find it from the command line. Pulseaudio was running fine.

---

### Post by TheFu on 2020-04-30
> **jmnorvell said:**
>  
pavcontrol: This is system settings module, right? I couldn't find it from the command line. Pulseaudio was running fine.

For weeks here, I've been calling it pavcontrol when the correct program name is **pavucontrol**.
I always use tab-completion, so type **pav{tab}** and that fills in the correct program.

Sorry for the confusion.

---

### Post by SeijiSensei on 2020-05-01
I always think of pavucontrol in terms of a VU meter.

---

### Post by TheFu on 2020-05-01
> **SeijiSensei said:**
> I always think of pavucontrol in terms of a VU meter.

"VU" means "Vehicle Utility" to me. It is a subsystem in some avionics software. ;)  Think I found a CLI way to reconfigure Pulse Audio going forward, which means I can automate it all for my needs!  ;)

---

