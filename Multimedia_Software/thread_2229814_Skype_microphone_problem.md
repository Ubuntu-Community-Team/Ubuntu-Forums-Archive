---
title: "Skype microphone problem"
date: 2014-06-15
forum: Multimedia Software
---

### Post by cetoka on 2014-06-15
[COLOR=#000000][FONT=verdana]This is really driving me crazy.I have been reading many posts but could not solve the problem.Yesterday while talking on skype, microphone stopped working.My daughter abroad could not hear my voice.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I am on Ubuntu 12.04LTS all the updates done.If I try the sound recorder on ubuntu the mic works fine.I have Logitech webcam C270 and also plugged in a seperate front mic it also works.I can record with the sound recorder.I installed pavucontrol checked the settings,opened the terminal and wrote gstreamer-properties and checked there and everything seems fine.Both mics work but not on skype.I purged skype deleted the hidden folders and reinstalled again,but no solution [/FONT][/COLOR][IMG]http://www.wilderssecurity.com/styles/default/xenforo/clear.png[/IMG]
[COLOR=#000000][FONT=verdana]these are my settings.Help please I need to use skype.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]While trying the skype test call I checked the recording menu and tried both microphones but still no solution.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Skype version 4.2.0.11 from the software center.My PC is 64 bit so I also installed ia32-libs.   The camera works fine.[/FONT][/COLOR]

---

### Post by cetoka on 2014-06-17
I hope someday this post helps to someone.After doing extensive reading I found and tried this on internet and the front mic started to work.

Start skype from the terminal:    [FONT=Ubuntu Mono]PULSE_SERVER=127.0.0.1 skype          [/FONT]:):lolflag:

---

### Post by Bucky Ball on 2014-06-17
When you're running Skype, open Pulseaudio Volume Control. You should see the stream in Playback and Recording when you speak. You have found a fix, which is great, but a bit clumsy. Skype should 'just work'. As the mic was working fine when it suddenly died half way through a conversation and not after updating or tweaking it is hard to figure what might have happened there.

Anyhow, please mark your thread as solved if you wish for others to benefit from your discovery. ;) (Thread Tools at top right.)

PS: Did you install Skype from the repositories or manually using a PPA?

---

### Post by lidex on 2014-07-01
It looks to me like the mic was muted in pavucontrol. (The speaker icon)

---

### Post by cetoka on 2014-07-13
Bucky Ball  Just saw your reply,I will mark it as solved thank you. Skype was installed from the Ubuntu Software Center.

> [COLOR=#000000]It looks to me like the mic was muted in pavucontrol. (The speaker icon)[/COLOR] I had checked it with pavucontrol and it was not muted.

---

