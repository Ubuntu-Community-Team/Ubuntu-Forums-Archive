---
title: "Sound device not recognized by Alsa"
date: 2013-04-23
forum: Multimedia Software
---

### Post by ftella on 2013-04-23
Hi,

I'm having an odd problem with my sound card. When I start the laptop I usually don't have sound. It sometimes comes back after some reboots. This is not happening in windows in which it always works fine.

I run the Alsainfo thing when sound was not recognized and got this:

[http://www.alsa-project.org/db/?f=8db3fb890218ce20737cf48cf88f8cfc793b1d10](http://www.alsa-project.org/db/?f=8db3fb890218ce20737cf48cf88f8cfc793b1d10)

Does anybody know what's happening here and how to solve it?

Many thanks.

---

### Post by slickymaster on 2013-04-23
Take a look at this: [Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit#")
It can be of some help solving your problem.

---

### Post by ftella on 2013-04-23
Thanks Slicky,

I'll try that guide.

Meanwhile, here's the Alsainfo when the sound is working:

[http://www.alsa-project.org/db/?f=61a3b7ae2999acc22f988aca12dbef27a5c2e3aa](http://www.alsa-project.org/db/?f=61a3b7ae2999acc22f988aca12dbef27a5c2e3aa)

---

### Post by slickymaster on 2013-04-23
ftella, see this thread: [No sound, ALSA problems, ac'97 not recognized]("http://ubuntuforums.org/showthread.php?t=2050646")

It's a similar issue with a similar AC'97 Sound Controller.

---

### Post by ftella on 2013-04-28
Hi again,

I was following some steps mentioned in your last post and I think I left Pulseaudio misconfigured.

Particulary after typing this, I think:

```


echo "load-module module-alsa-sink device=hw:[SiS SI7012],[SiS SI7012]" | sudo tee -a /etc/pulse/default.pa


```

Later I noticed that maybe I should have typed 0,0 instead of [SiS SI7012],[SiS SI7012] :confused:

The sound was working at that moment and suddenly it stopped. When I right click at the sound icon and click on "Volume Control" settings I get a message like this:

> Connection to PulseAudio failedAutomatic retry in 5s.
In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server in client.conf is misconfigured.
This situation can also arrise when PulseAudio crashed and left stale details in the X11 Root Window. If this is the case, then PulseAudio should autospawn again, or if this is not configured you should run start-pulseaudio-x11 manually.

What can I do now? Thanks

---

### Post by Yellow Pasque on 2013-04-28
It should have been 0,0, so get rid of or edit the line you added (it's at the end of the file):
```
gksu leafpad /etc/pulse/default.pa
```
When you're done, restart pulse:
```
rm -r ~/.pulse*; pulseaudio -k
```

---

### Post by ftella on 2013-04-29
Today, after booting, the sound icon in the toolbar is gone (the "volume control" item is in the list though).

After that I changed that line and did what you said:

```
rm -r ~/.pulse*; pulseaudio -k
E: [pulseaudio] main.c: Failed to kill daemon: No such process


```


Restarting didn't change anything.

Also tried this:

```
lspci | grep audio
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)


```

Also this:

```
echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done
Sound cards recognized by the system:
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller [1039:7012] (rev a0)
Sound cards recognized by ALSA:
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller [1039:7012] (rev a0)
Sound cards recognized by ALSA, and activated:
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller [1039:7012] (rev a0)


```

And this:

```
aplay -l
aplay: device_list:252: no soundcards found...


```

---

### Post by ftella on 2013-04-29
I tried this after:

```

sudo apt-get install --reinstall libasound2 
sudo dpkg-reconfigure pulseaudio 
sudo dpkg-reconfigure alsa-base

rm -rf ~/.pulse
```

Restarted and now the icon is back, but it's still giving the same error message:

> Connection to PulseAudio failedAutomatic retry in 5s...

---

### Post by ftella on 2013-04-29
Ok, I deleted the line from "/etc/pulse/default.pa" instead of editing it and got sound after rebooting.

Let's test some more. At least it's like at the beggining. :P

---

### Post by ftella on 2013-05-24
So let's resume this troubleshooting.

When audio is not working I tried this:

```
aplay -l | grep card
aplay: device_list:252: no soundcards found...
 lspci | grep audio
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)

```

So it looks like it has an audio controller but no sound card found. Maybe this doesn't have to do with sound drivers. (It could also be that I don't know what I'm looking at).

---

### Post by ftella on 2013-05-24
Also tried this:

```
sudo lshw -C multimedia

  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: SiS7012 AC'97 Sound Controller
       vendor: Silicon Integrated Systems [SiS]
       physical id: 2.7
       bus info: pci@0000:00:02.7
       version: a0
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=173 maxlatency=11 mingnt=52
       resources: ioport:1400(size=256) ioport:1080(size=128)
```

This seems to do nothing:
```
aplay
```
I hit enter, the cursor goes to the next line and that's all.

---

### Post by ftella on 2013-05-24
Then this:

```
echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done
Sound cards recognized by the system:
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller [1039:7012] (rev a0)
Sound cards recognized by ALSA:
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller [1039:7012] (rev a0)
Sound cards recognized by ALSA, and activated:
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller [1039:7012] (rev a0)
```

---

### Post by Yellow Pasque on 2013-05-25
> **ftella said:**
> So it looks like it has an audio controller but no sound card found.

aplay reporting no cards means the driver didn't load. When this happens, check:
```
dmesg | grep -i alsa
```

---

### Post by ftella on 2013-05-28
Terminal answers this to that command:

```
[   23.067419] init: alsa-restore main process (1191) terminated with status 19

```

---

### Post by Yellow Pasque on 2013-05-28
^Yeah, that's what I thought. I haven't figured out a surefire way to work around that yet. These commands may help you to get sound without rebooting:
```
sudo alsa force-reload
sudo alsactl init
```

---

### Post by ftella on 2013-05-29
I get this:

```
sudo alsa force-reload

Unloading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.


```

and the more discouraging:

```
sudo alsactl init
alsactl: init:1743: No soundcards found...


```

Argg, why "No soundcard found" You have to look harder mr.lubuntu. It's there!  :confused:

---

### Post by ftella on 2013-05-29
Wait! On a second try it found something and the sound works!

```
sudo alsactl init
Found hardware: "ICH" "Cirrus Logic CS4299 rev 4" "AC97a:43525934" "0x17c0" "0x2000"
Hardware is initialized using a generic method


```

It sounds a bit ridiculous to me but it's like when it gets some temperature it starts working. This doesn't happen in windows though in which sound always works.

---

### Post by ftella on 2013-05-29
As a workaround, is there a way I could make those commands keep repeating on startup till they find something?

Thanks a lot Temüjin!

---

