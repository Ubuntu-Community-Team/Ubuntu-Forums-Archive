---
title: "No sound recording using ALSA while connected to PulseAudio"
date: 2021-05-29
forum: Multimedia Software
---

### Post by meghdad149 on 2021-05-29
[COLOR=#000000][FONT=&amp]Hello.[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]I've had various sorts of issues with PulseAudio ever since I started running Ubuntu since almost one year ago. I tend to try DIY instead of asking and so I've had most of the issues resolved. But this one that appeared today is a bitch. I considered replacing PulseAudio with vanilla ALSA but most applicaitons failed to work afterwards. So here I am asking for your kind help.[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]So as the title says, I cannot record sound while the PulseAudio daemon is running. I use arecord and the result is just silence. Without pulse running, arecord works perfectly. [/FONT][/COLOR]

[IMG]https://imgur.com/z3JkpJb.png[/IMG]

[IMG]https://imgur.com/DxBIgfQ.png[/IMG]


[COLOR=#000000][FONT=&amp]Here's some possibly useful info:[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][HTML] meghdad@meghdad-pc:~$ cat /proc/asound/cards 
0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe9f4000 irq 16[/HTML]


```

[COLOR=#000000][FONT=&amp]meghdad@meghdad-pc:~$ cat /proc/asound/card0/codec#0 | head[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Codec: VIA VT1705[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Address: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]AFG Function Id: 0x1 (unsol 0)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Vendor Id: 0x11064397[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Subsystem Id: 0x101905b3[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Revision Id: 0x100000[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]No Modem Function Group found[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Default PCM:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    rates [0x0]:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    bits [0x0]:[/FONT][/COLOR]

```[COLOR=#000000][FONT=&amp]

```


```[/FONT][/COLOR]```
meghdad@meghdad-pc:~$ pactl list sources
Source #0
    State: RUNNING
    Name: alsa_output.pci-0000_00_14.2.analog-stereo.monitor
    Description: Monitor of Built-in Audio Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 48000Hz
    Channel Map: front-left,front-right
    Owner Module: 7
    Mute: yes
    Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor of Sink: alsa_output.pci-0000_00_14.2.analog-stereo
    Latency: 0 usec, configured 40000 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Monitor of Built-in Audio Analog Stereo"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA ATI SB"
        alsa.long_card_name = "HDA ATI SB at 0xfe9f4000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "4383"
        device.product.name = "SBx00 Azalia (Intel HDA)"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Formats:
        pcm


Source #1
    State: RUNNING
    Name: alsa_input.pci-0000_00_14.2.analog-stereo
    Description: Built-in Audio Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 7
    Mute: no
    Volume: front-left: 44225 /  67% / -10.25 dB,   front-right: 44225 /  67% / -10.25 dB
            balance 0.00
    Base Volume: 6368 /  10% / -60.75 dB
    Monitor of Sink: n/a
    Latency: 403 usec, configured 40000 usec
    Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "VT1705 Analog"
        alsa.id = "VT1705 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA ATI SB"
        alsa.long_card_name = "HDA ATI SB at 0xfe9f4000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "4383"
        device.product.name = "SBx00 Azalia (Intel HDA)"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "352768"
        device.buffering.fragment_size = "176384"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        analog-input-front-mic: Front Microphone (type: Mic, priority: 8500, availability group: Legacy 1, not available)
        analog-input-rear-mic: Rear Microphone (type: Mic, priority: 8200, availability group: Legacy 2, not available)
        analog-input-linein: Line In (type: Line, priority: 8100, availability group: Legacy 3, not available)
    Active Port: analog-input-front-mic
    Formats:
        pcm



```[COLOR=#000000][FONT=&amp]

```

meghdad@meghdad-pc:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1705 Analog [VT1705 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```






[/FONT][/COLOR]

---

### Post by TheFu on 2021-05-29
I completely understand.  Had the same issues myself. Then someone showed me how to give up total control and relax, use **pavucontrol** to control the different sinks and sources.  Pulse is like the VoIP tool Asterisk.  Both are setup to access inputs, do something with those, then send the modified (or unmodified) output somewhere.

Assuming you have a stock install without any customization at all, run pavucontrol.  Start with the tab on the far right, Configuration.  Enable/disable the devices you want for right now.  Later, when more understand happens, you'll be able to have all of them enabled, but for right now, you probably want 1 output and 1 input. 
The 2 options I have now are the motherboard audio controller and the nvidia GPU audio controller.  I don't ever use the nvidia, since it only supports HDMI audio and my monitors don't support audio.  So that is using the Profile: "Off".
The other option is the MB audio controller, "Family 17h (Models 00h-ofh) HD Audio Controller Analog Stereo", which has lots and lots of options.  Because it has multiple microphone and speaker jacks, I need one of the analog "duplex" modes.  Gotta love the name of the controller - NOT!

Moving to the left 1 tab, we have "Input Devices".  There are 3 icons that make little sense to me, one is an on-off for the device, the next is a L/R lock and the last is listed as "fallback" ... whatever that means to the pulseaudio people.   
This can be confusing, since modern PCs often have audio inputs from the motherboard and the GPU, but I've disabled the GPU already so it won't show up in the Input tab at all.  The Family 17h .... controller has a pulldown option with Front/Rear and line-in options.  I'm using a $9 lapel mic on the front panel. It shows as "plugged in".  If I left the webcam or Samson Mics plugged in all the time those would show up in the Configuration tab and for "Input" and "Recording" tab.  But those are easy to figure out because they have the common courtesy to list the vendor name in the list.  "Logitech C920" or "Samson GoMic" are pretty clear! Anyways, if I want to use those, I just disable (the speaker icon) all the other inputs and leave only the microphone I want enabled.

Moving on to the "Output Devices" tab.  I use the old-old-school 3.5mm jack on the front panel for one of my systems - 2 speakers. It is analog, so I'm looking for the "headphones" option.  It is listed as "Headphones" but there is an option for "line-out" too.  So, I select the "Headphones" for the output and get to see a level control slider.  100% is what I typically use - it can be slid to 150% or muted. We can always adjust the volume on the speakers.

Pulse likes to reconfigure to use whatever audio device was last connected.  In other distros, this requires a module to happen. In Ubuntu, or at least some Ubuntus, that auto-switch seems to be automatic.  Which can be useful to us.  To get an audio device made primary, unplug and re-plug it. Wait a few seconds for udev to notice both of those events.  

That's all the step up for devices.  Until we have actual sound playing or a microphone being recorded/monitored, the "Playback" and "Recording" tabs won't be much use.  Those don't list anything until a program has connected to an audio device for use.  IME, that sometimes happens at program start, so if we touch the far right tabs, we may need to restart a program (looking at you Chromium-browser!) to get any audio working.  Many other programs do not behave that way and will dynamically see audio device changes/updates.

All of this stuff and I didn't have to touch alsamixer.

About once a week, the pulseaudio daemon will crash, so, if you plan to use it for anything important, killing it and restarting it could be a good idea.  That daemon can run in 2 modes - system mode and individual userid mode.  The Pulse guys recommend against system mode. They provide many caveats.  Basically, it means that we don't want/need to use sudo for any of these controls when we have a GUI session.
To kill the daemon:
```
$ pulseaudio -k
```
To start the daemon:
```
$ pulseaudio -D
```
The pulseaudio seems to be set to autostart on my system. I don't recall if that is standard or not. The startup does take some time - say 5-10 seconds, so don't expect to run pactl/pacmd without a small delay after a restart.

If you don't want to use the GUI pavcontrol, then these settings can be controlled using pactl or pacmd.
To get a list of sinks (speakers), 
```
$ pactl list short sinks
4       [COLOR="#FF0000"]alsa_output.pci-0000_0a_00.3.analog-stereo[/COLOR]      module-alsa-card.cs16le 2ch 44100Hz       IDLE
```
or, for a longer list with more details, use:
```
$ pacmd list-sinks|egrep '\.name|name:|port|state'
        name: <[COLOR="#FF0000"]alsa_output.pci-0000_0a_00.3.analog-stereo[/COLOR]>
        state: IDLE
                alsa.name = "ALC1220 Analog"
                device.vendor.name = "Advanced Micro Devices, Inc. [AMD]"
                device.product.name = "Family 17h (Models 00h-0fh) HD Audio Controller"
                device.profile.name = "analog-stereo"
        ports:
        active port: <analog-output-headphones>
```

To get a list of sources (microphones), 
```
$ pactl list short sources
1       alsa_[COLOR="#FF0000"]input[/COLOR].pci-0000_0a_00.3.analog-stereo       module-alsa-card.cs16le 2ch 44100Hz       RUNNING
8       alsa_output.pci-0000_0a_00.3.analog-stereo.monitor      module-alsa-card.c        s16le 2ch 44100Hz       RUNNING
9       alsa_[COLOR="#FF0000"]input.usb[/COLOR]-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo module-alsa-card.c       s16le 2ch 32000Hz       RUNNING

```
or for longer information 
```
$ pacmd list-sources | egrep '\.name|name:|port|state'

```
let's just say, the output is much longer. We want to choose the device name inside the <**choose-this**>.

Next, we need to set the default sink and source.
```
$ pactl set-default-sink alsa_output.pci-0000_0a_00.3.analog-stereo
$ pacmd set-default-source alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo
```

I'm showing pactl and pacmd. All these work, as shown on my system.

> # ###############[ Pulse tip ]###################
The pulse audio module 'module-switch-on-connect' is responsible for setting newly connected audio devices as the default device. To (temporarily) inhibit this behavior you can remove this module with '**pacmd unload-module** module-switch-on-connect' before connecting the controller and re-enable it with '**pacmd load-module module-switch-on-connect**'.

Musicians probably have very different audio needs than I. They might want to look at jack audio server or there's a new-fangled replacement coming that the kewl-kids seem to be all excited about. It is possible to remove pulse and install other of those, but that isn't something I've done.

I don't really know much more than what is said above. Since switching and screwing around to get things working, they mostly "just work", which is very different from what happened a year ago as we all got webcams and microphones working for our remote working needs.

Anyways, hope this has shed a light on PulseAudio. Since these revelations were provided to me, I haven't looked at alsa again.

---

### Post by TheFu on 2021-05-29
Oh - I should say that recording over an analog microphone using CLI tools has never worked for me. Not once.  Doing exactly the same commands using either of my USB microphones always works.  But recording analog microphones using GUI tools **has** worked.  I suspect it is because I don't get the detailed recording settings correct, but the GUIs handle that for me.

When I say they don't work, I mean the recordings are just screeches.

---

### Post by meghdad149 on 2021-05-29
Well thanks for taking your time to post a reply. However that seemed like a bot reply to be honest because respectfully, it's just irrelevant to my problem.

---

### Post by TheFu on 2021-05-29
> **meghdad149 said:**
> Well thanks for taking your time to post a reply. However that seemed like a bot reply to be honest because respectfully, it's just irrelevant to my problem.

The problem I saw was arecord doesn't work.
The solution is to not use arecord and use a pulse-aware recording tool instead.
For your setup, I'd guess 
```
$ **parec** -d  alsa_input.pci-0000_00_14.2.analog-stereo | oggenc -b 192 -o foo.ogg --raw -
```
or
```
$ **parecord** -d  alsa_input.pci-0000_00_14.2.analog-stereo -r somefile.wav 
```

Those should work, in theory. I'm not all that happy with the background noise, but didn't spend much time trying to clean my environment up first.

---

### Post by meghdad149 on 2021-05-30
No! Please! That's not THE problem, that's a manifestation of the problem that's so obvious in that PulseAudio screenshot.

---

### Post by Holger_Gehrke on 2021-05-30
You can suspend PulseAudio for the runtime of one command using 'pasuspender', something like 'pasuspender -- arecord *<options+arguments>*' should allow arecord to do it's thing without PA getting in the way.

Holger

---

### Post by meghdad149 on 2021-06-03
I've been following up this issue using various IRC channels and here is the #pulseaudio conversation:

> **Conversation with #pulseaudio**

[COLOR=#000000][FONT=&amp][SIZE=2](10:29:20 AM) [/SIZE][/FONT][/COLOR][B][SIZE=3]The topic for #pulseaudio is: You must be registered to talk | Stable release: 14.2, Release candidate: 14.99.1 | Troubleshooting: [https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/Users/Troubleshooting/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/Users/Troubleshooting/)[/SIZE]
[SIZE=2](10:29:20 AM) [/SIZE][B]Topic for #pulseaudio set by Ford_Prefect!sid478174@id-478174.highgate.irccloud.com at 05:17:12 AM on 05/27/2021
[SIZE=2][COLOR=#204a87](10:29:34 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]hello everyone :-)
[SIZE=2][COLOR=#204a87](10:30:16 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR][https://ubuntuforums.org/showthread.php?t=2462882](https://ubuntuforums.org/showthread.php?t=2462882)
[SIZE=2][COLOR=#204a87](10:30:27 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]^ Could you please take a look at this issue?
[SIZE=2][COLOR=#204a87](10:31:03 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]I've asked about it on Ubuntu and Arch channels and they directed me here.
[SIZE=2][COLOR=#af7f00](10:44:32 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: pulseaudio needs exclusive access to hardware, pasuspender allows temporarily suspending pulseaudio while you use alsa hardware directly
[SIZE=2][COLOR=#204a87](10:47:58 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]well that does solve my issue.
[SIZE=2][COLOR=#204a87](10:48:04 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]*doesnt
[SIZE=2][COLOR=#204a87](10:48:32 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]I used to be able to record via various applications e.g skype. I can't anymore.
[SIZE=2][COLOR=#204a87](10:49:17 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]basically the issue is that the stereo duplex profile is unavilable, as seen in the first screenshot.
[SIZE=2][COLOR=#af7f00](10:54:19 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: I see, would you mind pastebin your pa-info output?
[SIZE=2][COLOR=#204a87](11:00:34 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR][https://gist.github.com/no149/8d538e4dbc9c7568cc021c50379af0ec](https://gist.github.com/no149/8d538e4dbc9c7568cc021c50379af0ec)
[SIZE=2][COLOR=#af7f00](11:08:35 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: please run it as normal user or it won't be able to access pulseaudio daemon (see pactl info section is empty)
[SIZE=2][COLOR=#af7f00](11:09:04 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: you are running 13.99.2 do you have an option to upgrade?
[SIZE=2][COLOR=#204a87](11:24:25 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR][https://gist.github.com/no149/ec149c363649e44727a5f40297a92b18](https://gist.github.com/no149/ec149c363649e44727a5f40297a92b18)
[SIZE=2][COLOR=#204a87](11:24:41 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]I can upgrade to the next Ubuntu release yes.
[SIZE=2][COLOR=#204a87](11:25:54 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]though I'm not sure if PA is upgraded in that release. I need to make sure.
[SIZE=2][COLOR=#204a87](11:27:48 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]yes pulseaudio is upgraded in the next release.
[SIZE=2][COLOR=#77b2e0](11:28:06 AM) [/COLOR][/SIZE][COLOR=#77B2E0]Nei: [/COLOR](maybe you could make a local install of a newer PA version only, for testing purpose)
[SIZE=2][COLOR=#af7f00](11:28:08 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: 14.2 has a few fixes for duplex profiles, hirsute or later has it and maybe you can also some 14.2 build for your current ubuntu
[SIZE=2][COLOR=#204a87](11:29:24 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]yeah i'm lookin for a backport now
[SIZE=2][COLOR=#204a87](11:29:48 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]then I will let you know if the issue persists...
[SIZE=2][COLOR=#204a87](11:29:50 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]thanks :)
[SIZE=2][COLOR=#af7f00](11:31:10 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: looking at your pa-info latest, which input of Card #0 you expect to be available for duplex profile, any mic or analog-input-linein?
[SIZE=2][COLOR=#204a87](11:33:53 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]yeah, used to be alsa_input_...mic I believe. Now it's missing
[SIZE=2][COLOR=#204a87](11:34:43 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]OK changed the profile to that duplex one from output: analog-input-front-mic: Front Microphone (type: Mic, priority: 8500, availability group: Legacy 1, not available)
[SIZE=2][COLOR=#af7f00](11:35:08 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: do you have anything plugged into mic port?
[SIZE=2][COLOR=#204a87](11:35:11 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]I should re-port those painfo output using the new profile selected. Hang on please...
[SIZE=2][COLOR=#204a87](11:36:06 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR][https://gist.github.com/no149/5c239626048a860a882f8d412013a4e6](https://gist.github.com/no149/5c239626048a860a882f8d412013a4e6)
[SIZE=2][COLOR=#204a87](11:36:22 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]yes I have a headset mic into that jack
[SIZE=2](11:37:44 AM) [/SIZE][B]ryzokuken[m]1 [*~ryzokuken@2001:470:1af1:101::8552*] entered the room.
[SIZE=2][COLOR=#af7f00](11:38:07 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: let's see if alsa layer does not report plugged jack state correctly
[SIZE=2][COLOR=#204a87](11:38:07 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]a few hints that might help:
[SIZE=2][COLOR=#204a87](11:38:07 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]arecord works as long as PA is down.
[SIZE=2][COLOR=#204a87](11:38:07 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]PA vol control shows the mic vol meter moving when I talk into the mic.
[SIZE=2][COLOR=#af7f00](11:38:53 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: you need to compare pa-info output with mic jack plugged in and plugged out; check 'jacks_do' section
[SIZE=2][COLOR=#204a87](11:39:13 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]sentiment: yeah I suspect that
[SIZE=2][COLOR=#204a87](11:39:23 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]ok I'll do that now
[SIZE=2][COLOR=#af7f00](11:40:19 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: in your latest pa-info both mic jacks are reported 'off' which makes pa believe mics are not available so there is no duplex profile enabled
[SIZE=2][COLOR=#af7f00](11:41:03 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: you can probably use mic anyway if you select it manually in pavucontrol 'Inputs' tab - even if it is listed unavailable there, just make it current
[SIZE=2][COLOR=#204a87](11:41:40 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]no I can't
[SIZE=2][COLOR=#204a87](11:42:01 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]it's already selected and the meter moves but I can't actually use it.
[SIZE=2][COLOR=#204a87](11:42:11 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]let me do that comparison
[SIZE=2][COLOR=#204a87](11:49:39 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]this is interesting.
[SIZE=2][COLOR=#204a87](11:50:16 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]both outputs show the result result as far as jacks_do is concerned i.e values=off for both states.
[SIZE=2][COLOR=#204a87](11:50:41 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]now, the front headphone jack is always on regardless of any headphone connection.
[SIZE=2][COLOR=#204a87](11:50:53 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]but that's besides the point I think?
[SIZE=2][COLOR=#af7f00](11:52:32 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: if 'jacks_do' does not change this means jack detection does not work in your case, this explains what you see
[SIZE=2][COLOR=#204a87](11:54:25 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]but it never worked anyways. as long as I remember the mic port was always "unplugged" even though the mic actually worked.
[SIZE=2][COLOR=#204a87](11:54:35 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]does that make any sense?
[SIZE=2][COLOR=#af7f00](11:54:51 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: jack detection is handled by kernel alsa driver and by alsa lib itself; if you are able to verify this issue with more up-to-date kernel and alsa lib e.g. by testing latest ubuntu live image you can send a mail to alsa-devel list asking to fix it, this is considered as important bug by alsa-devel list
[SIZE=2][COLOR=#204a87](11:54:53 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]perhaps something changed with an update?
[SIZE=2](11:54:55 AM) [/SIZE][B]alpernebbi [*~quassel@178.233.26.119*] entered the room.
[SIZE=2][COLOR=#204a87](11:56:06 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]OK
[SIZE=2][COLOR=#af7f00](11:56:09 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: double-check you selected correct mic input in pavucontrol 'Input devices' tab
[SIZE=2][COLOR=#204a87](11:56:31 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]but can I make alsa to "see" the mic is always connected? like the headphone jack?
[SIZE=2][COLOR=#204a87](11:57:11 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR][https://imgur.com/RMMgYEb.png](https://imgur.com/RMMgYEb.png)
[SIZE=2][COLOR=#204a87](11:57:14 AM) [/COLOR][/SIZE][COLOR=#204A87]sentiment: [/COLOR]it is correct.
[SIZE=2][COLOR=#af7f00](11:57:17 AM) [/COLOR][/SIZE][COLOR=#AF7F00]i-garrison: [/COLOR]sentiment: apart from jack detection issue, if you are able to record via pure alsa but not via pulseaudio from the same mic it would be a bug in pulseaudio, but please test more recent pulseaudio/alsa/kernel combination first[/B][/B][/B][/B]

As I've upgraded to the latest LTS release and the issue persists, I'm going to take this to the ALSA developers.

---

### Post by meghdad149 on 2021-06-13
[https://askubuntu.com/q/1328217](https://askubuntu.com/q/1328217)

Got it *kind of *working after following that question and also by setting the following in the analog-input-front-mic.conf:

```

[Jack Front Mic]
required-any = any
state.plugged = yes
state.unplugged = unknown

```

Still, I can't use the duplex mode and I have to switch to the input profile in order to record. :-/

Edit - Ok, fully working now. Just needed to delete the .config/pulse directory.

---

