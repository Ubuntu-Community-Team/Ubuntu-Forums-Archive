---
title: "Sound [Specifically Internal Microphone] Issues - Walkthrough Request"
date: 2013-10-06
forum: Multimedia Software
---

### Post by zia.newversion on 2013-10-06
Hi everybody,

This is a problem that has stayed with me throughout my experience with Linux. In earlier releases of Ubuntu, it was relatively easier to fix. But with the current release, this problem is solved as of yet. My knowledge of the Linux Sound Architecture is very limited. I am posting this thread so someone can (a) walk me through different troubleshooting steps to fix the problem I am having and (b) so I can learn some more about the Linux Sound Architecture in general.

[COLOR=#008000][SIZE=4]Background:[/SIZE][/COLOR]
I discovered Linux several years ago in a Computer Science convention which I was forced to go to. I found it interesting. I tried it out and quickly became a fan of it, especially the Ubuntu distribution. I have been an avid user ever since and also dual booted Ubuntu and Windows for quite some time. However, for around 10 months during this period, I completely shifted to Windows and didn't use Linux at all. I was under the (false) impression that setting up a workspace on Ubuntu would take a lot of time and there'd still be some things missing. I recently came back to Linux. I installed Ubuntu a month ago and found out that my concerns were grossly misplaced. So far, I am loving it. My workspace is nicely set up and frankly more productive than on Windows. I'm never going back to Windows after a taste of this.
However, there is an issue. My work involves a lot of Skype. My microphone doesn't work so I am handicapped. I have to make long-distance phone calls, so the sooner this problem is solved, the more money I will save. ;)

[COLOR=#008000][SIZE=4]Platform:[/SIZE][/COLOR]
I am using **Ubuntu 13.04 Raring Ringtail** on a **Dell Studio XPS 1645**. It's a couple of years old machine, but it just works for me. The sound card, according to alsamixer is: **HDA Intel MID** and the chip: **IDT 92HD73C1X5**. There is a stereo speaker system on board and also a microphone array.

[COLOR=#008000][SIZE=4]Problem:[/SIZE][/COLOR]
The **audio output works fine**. I get nice sound from onboard speakers as well as headphone connected to audio output jack. The problem is with audio input. **The internal microphone doesn't work**. I haven't tried an external microphone solely because I don't have one and finding a good one is very hard. I really just want the internal one to work because it offers better quality and more flexibility.

[COLOR=#008000][SIZE=4]Proposed Fix:[/SIZE][/COLOR]
In the earlier releases of Ubuntu, (I don't distinctly remember, but I think from Maverick to Precise) all I had to do to fix this was add: 
```
options snd-hda-intel model=dell-m6
```
to my *alsa-base.conf* (located in [FONT=lucida console]/etc/modprobe.d/[/FONT])

[COLOR=#008000][SIZE=4]Current Progress:[/SIZE][/COLOR]
When I installed Ubuntu and noticed my microphone ins't working, my first instinct was to try the already known fix, which I did. However, after reboot, when I opened sound settings, the microphone still didn't appear to work. I looked up the internet but did not find a solution. Instead, I learnt (from [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto")) why I need to add that extra line to *alsa-base.conf*. According to my recently acquired knowledge, alsa is responsible for recognizing sound hardware and providing a software interface to it (which pulseaudio uses to manage audio in user-space). But alsa does not recognize all hardware by default. Sometimes, extra modules needed to be loaded at boot time, especially for Intel HDA cards. Until these modules are loaded, the hardware, or a part of the hardware might not perform normally. These modules are documented [here]("https://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt").

I installed *gnome-sound-recorder* to test whether my mic was working, but it doesn't work. In the input option, there only one option: Master. And the select-box for format does not have an option at all. Pressing "record" button does nothing.

I removed and re-installed pulseaudio. I also installed pavucontrol. PulseAudio Audio Control does not show that microphone is working, either.

I installed audacity. Audacity gives me greater degree of control over what to use for input. There is this really long list of options I can choose from. Some of these result in absolutely no input, or just low-volume noise. Some of these work. But their status changes after each reboot. A particular input is working but after reboot, it stops working and another one, which wasn't working previously starts working. Here is a list of the input interfaces I have. (Side-note: can I get a list of these through command line?)

[FONT=lucida console]01- HDA Intel MID: STAC92xx Analog (hw:0,0): Mic:0 --------------- Flat Line
02- HDA Intel MID: STAC92xx Analog (hw:0,0): Internal Mic:0 ------ [/FONT][FONT=lucida console]Flat Line[/FONT][FONT=lucida console]
03- HDA Intel MID: STAC92xx Analog (hw:0,0): Internal Mic 1:0 ---- Works
04- HDA Intel MID: STAC92xx Analog (hw:0,0): Mic:1 --------------- Works
05- HDA Intel MID: STAC92xx Analog (hw:0,0): Internal Mic:1 ------ Works
06- HDA Intel MID: STAC92xx Analog (hw:0,0): Internal Mic 1:1 ---- Works
07- sysdefault --------------------------------------------------- Works
08- pulse: Mic:0 ------------------------------------------------- White Noise
09- pulse: Internal Mic:0 ---------------------------------------- Flat Line
10- pulse: Internal Mic 1:0 -------------------------------------- Works
11- pulse: Mic:1 ------------------------------------------------- Works
12- pulse: Internal Mic:1 ---------------------------------------- Works
13- pulse: Internal Mic 1:1 -------------------------------------- Works
14- default: Mic:0 ----------------------------------------------- White Noise
15- default: Internal Mic:0 -------------------------------------- Flat Line
16- default: Internal Mic 1:0 ------------------------------------ Works
17- default: Mic:1 ----------------------------------------------- Works
18- default: Internal Mic:1 -------------------------------------- Works
19- default: Internal Mic 1:1 ------------------------------------ Works

[/FONT]*[COLOR=#a52a2a]Ok, so I just made that list by manually checking all the inputs. Before making this list, when I was typing the text above it, mic according to Sound Settings wasn't working and neither was according to PulseAudio Control Utility. But now both are working. I didn't change a thing.[/COLOR]* Just opened Audacity to test all audio inputs so I can make the list. Audacity is now closed, and the mic is still working. My point is, it's unpredictable (at least to me). As I mentioned earlier, different input interfaces in audacity go from working to flat-line to white-noise after every reboot. [COLOR=#808080]*Also, while using Audacity, if I already have a sound track in the project, some of these inputs, when recorded from, return a "latency" error, but work fine when I delete all other audio tracks from the project. I don't know what's that about.*[/COLOR]

When I open Skype Audio Settings, it says that since PulseAudio is running, I should do all my settings in the PulseAudio Control Panel. When PulseAudio doesn't recognize or accept input from the internal microphone, there is just no way for me to make it work (apart from restarting and praying PulseAudio behaves this time). So I disabled PulseAudio respawning and now I do a [FONT=lucida console]pulseaudio --kill[/FONT] and then restart Skype. Now Skype doesn't see PulseAudio running so it lets me choose from a list of inputs almost the same as the one with Audacity and I try all of these and one of them (different every time) works (sometimes none of these work, and I have to use the phone). Then I do a [FONT=lucida console]pulseaudio --start[/FONT] and it works until I reboot.

What's going on here?
Can someone with knowledge of the Linux Sound Architecture explain how this could happen?
The hardware is fine. As I said, I've been using it with Windows and it works fine... Maybe there is something I am doing wrong here.
Your answer doesn't necessary have to be solution oriented. This is more like a discussion (although a solution will help me out).

---

### Post by zia.newversion on 2013-10-09
[COLOR=#008000][SIZE=4]Update:[/SIZE][/COLOR]
After I boot up, mic doesn't work.

In sound settings, I select "Input" and knock on the microphone. The bar stays. (It should jump if the microphone is working)

In PulseAudio Control Panel, I select "Input Devices" and select "Internal Microphone" then knock on the microphone. The bar stays.

In Audacity, I select the input source as "HDA Intel MID: STAC92xx Analog (hw:0,0): Internal Mic 1:0", press "record" and knock the microphone. I can see the output and when I play it, I can hear loud knocking, meaning this input source is working. I go back to sound settings and PulseAudio Control to test it, still doesn't work.

Come back to Audacity, select input source as "sysdefault", press "record" and knock the microphone. No output and when I play it, I hear only low-volume white noise. Meaning this input source doesn't work.

I keep selecting different inputs in audacity and coming back to sound settings and pavucontrol to test them out. When I select "default: Internal Mic 1:0", input works in Audacity. So I come back to sound settings and voila, now when I knock the mic, the bar jumps up and down, meaning the mic is working.

And now back in Audacity, when I select input source as "sysdefault", it works, too!

What sorcery is this?

---

### Post by Luis_Arjona on 2014-01-12
> **zia.newversion said:**
> [COLOR=#008000][SIZE=4]Update:[/SIZE][/COLOR]
After I boot up, mic doesn't work.

In sound settings, I select "Input" and knock on the microphone. The bar stays. (It should jump if the microphone is working)

In PulseAudio Control Panel, I select "Input Devices" and select "Internal Microphone" then knock on the microphone. The bar stays.

In Audacity, I select the input source as "HDA Intel MID: STAC92xx Analog (hw:0,0): Internal Mic 1:0", press "record" and knock the microphone. I can see the output and when I play it, I can hear loud knocking, meaning this input source is working. I go back to sound settings and PulseAudio Control to test it, still doesn't work.

Come back to Audacity, select input source as "sysdefault", press "record" and knock the microphone. No output and when I play it, I hear only low-volume white noise. Meaning this input source doesn't work.

I keep selecting different inputs in audacity and coming back to sound settings and pavucontrol to test them out. When I select "default: Internal Mic 1:0", input works in Audacity. So I come back to sound settings and voila, now when I knock the mic, the bar jumps up and down, meaning the mic is working.

And now back in Audacity, when I select input source as "sysdefault", it works, too!

What sorcery is this?


After installing Ubuntu 12.04 I have also been struggling with the audio and micro for several days. Finally I found a way through.
My hardware is a  Packard Bell netbook with a Realtek ALC269VB audio but the solution is not specific to it.
In my case the problem was a strong skweeeek in speakers and no internal microphone (headphones and external micro OK). I managed to recover audio but no microphone. Finally I managed to recover the microphone. I'll describe what I did and hopefully it will help you.
I shall mention that different control devices work quite differently and some times they provide different information and have different capabilities. That was the case for instance with alsamixer on terminal and with gnome-alsa-mixer GUI (In my case running alsamixer on terminal was of no use).

Here goes what finally solved my problem:
1. Edited /etc/modprobe.d/alsa-base.conf:
gksudo gedit /etc/modprobe.d/alsa-base.conf
to add at the end the following line:
options snd-hda-intel model=auto
Save and exiit
(You may not need this step I did it to change my audio configuration and may try to go back to the original one).

2. I entered Sound Configuration (I use cinnamon desktop so I use Cinnamon sound control either from menu or clicking the sound applet):
In hardware I choosed Stereo Analogic Duplex.
In my case the selection there had changed to Stereo Analogic Output. (I realized that this is what eliminanted the skweeek, but also eliminated the Internal Microphone).
To avoid the skweeek in input I set the switch of INPUT as ON but the volume at a the very minimum (Increasing volume generated the skeeeek.)
Exit

3. I entered gnome-alsa-mixer (I shall mention that attempts to solve the problem via adjustments through terminal 'alsamixer' were unsuccesfull.
In gnome I turned all devices on but with the last controls (both say INTERNAL) at cero.
Finally I increased the volume of the last INTERNAL but left the one before it at zero.
This is quite confusing because if you enter into the edition of the properties of the sound card devices the last control is seems to be Internal micro boost while the one before it is internal micro, but I think it is the other way arround.
Exit.
4. Afterwards I tried to check the settings through terminal vía 'alsamixer' but it provides no information about the internal micro boost, it does not distinguish between mic and internal mic. Anyway what I go there is that it was micro boost what was set to cero.

To summarize, in your case I think you should check if there is a program that changes either your audio hardware to Stereo Analogic Output instead of Stereo Analogic Duplex and should also check if your Input device es being set to off by that program. As I mentioned the programs that you can use to set them back at their correct configuration are "Sound Control" and "gnome-alsa-mixer".):P

---

