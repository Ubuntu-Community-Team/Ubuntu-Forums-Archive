---
title: "Issue with Input Device Selection in Ubuntu 22.04.02 LTS"
date: 2023-07-16
forum: Multimedia Software
---

### Post by johndoe2700 on 2023-07-16
[COLOR=#232629][FONT=-apple-system][FONT=inherit]I am a new Ubuntu user and have been using Ubuntu 22.04.02 LTS as my operating system. First and foremost, I would like to express my gratitude for the exceptional work you have done in creating such a powerful and user-friendly OS.[/FONT]
[FONT=inherit]However, I have encountered a particular issue regarding the selection of input devices in the sound settings. I have a pair of headphones with a broken microphone, and when I attempt to change the input device, the only option available is "Microphone-Built-in-audio." Unfortunately, this option only works when the headphones are connected.[/FONT]
[FONT=inherit]When I unplug the headphones, I am presented with the option "Internal Microphone-Built-in-audio," which works perfectly. However, it would be incredibly beneficial if I could have both options available simultaneously, regardless of whether the headphones are connected or not.[/FONT]
[FONT=inherit]I have tried various software solutions, including PulseAudio Volume Control, ALSA Mixer, and pavucontrol, in an attempt to address this issue. Unfortunately, despite my efforts, the problem persists.[/FONT]
[FONT=inherit]I kindly request your assistance in resolving this matter. It would be greatly appreciated if this issue could be addressed and resolved in the next Ubuntu update. Having the ability to select between the two options, even with the headphones connected, would significantly enhance the usability and flexibility of Ubuntu.[/FONT]
[FONT=inherit]Thank you for your attention to this matter, and for your dedication to improving Ubuntu. I look forward to your response and any guidance you can provide.[/FONT]


[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][FONT=inherit][FONT=inherit][/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by Holger_Gehrke on 2023-07-16
First off, welcome to the forum. Sadly, you seem to be labouring under the misconception that this is an official support forum. It isn't, not quite anyway. It's more along the lines of users helping each other. I've never heard of any representative of Canonical posting on this forum.

Sadly, there's probably not much that can be done about your problem. The kind of switching between audio outputs and inputs you're noticing is normally done in hardware. If an external device is connected, the internal one is switched off.

A workaround would be to use a cheap USB sound-dongle and connect your headset to that. Then there'd be nothing stopping the internal microphone from working. Another option might be an external display connected through HDMI. Your graphics card can act as a second sound card and quite a few displays have a headphone jack.

Holger

---

### Post by Skaperen on 2023-07-16
i have noticed, when browsing source code, that PA goes through some effort along these lines.  i don't know if it is controlling this input switch or is trying to choose how to identify what the hardware has chosen.

i'd look around for dirt-cheap USB microphone to plug in and see if anything will detect it while the headphones are plugged in (is it a 4-ring barrel connector?)

---

