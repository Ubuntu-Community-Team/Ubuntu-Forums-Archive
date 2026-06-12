---
title: "I've lost all sound"
date: 2008-08-13
forum: Multimedia Software
---

### Post by anathema415 on 2008-08-13
Ubuntu Hardy
Compaq Presario SR5130NX
Athlon 64X2 3800+
Ubuntu Hardy 32 bit
Nvidia GeForce 6150 SE 
1 gig of RAM
It's unchanged hardware wise since I bought it last year


Hi guys,

After months of no problems I've lost all sound. The only things I was doing today was upgrading nvidia driver via envyNG with no problems, removed eve-online and removed VirtualBox. After i removed eve and vb and restarted the sound disappeared. Help me please!

---

### Post by anathema415 on 2008-08-13
Any body please? I have work to do that requires sound.

---

### Post by loboc on 2008-08-13
Is pulseaudio part of your set up?

---

### Post by anathema415 on 2008-08-13
Yes

---

### Post by loboc on 2008-08-13
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

Mine wasnt starting automatically I added /usr/bin/pulseaudio to 
Preferences>Sessions

---

### Post by anathema415 on 2008-08-13
> **loboc said:**
> [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

Mine wasnt starting automatically I added /usr/bin/pulseaudio to 
Preferences>Sessions

Didn't work. When I try to open the volume control here's what I get:

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Gstreamer is installed.

---

### Post by loboc on 2008-08-13
[http://ubuntuforums.org/showpost.php?p=5519401&postcount=7](http://ubuntuforums.org/showpost.php?p=5519401&postcount=7)

Has a list of the pulseaudio utilities

---

### Post by anathema415 on 2008-08-13
Ok here's an update. I've followed two tutorials:

[http://ph.ubuntuforums.com/showthread.php?t=205449]("http://ph.ubuntuforums.com/showthread.php?t=205449")

and 

[http://ph.ubuntuforums.com/showthread.php?t=843012&highlight=sound]("http://ph.ubuntuforums.com/showthread.php?t=843012&highlight=sound")

I've gotten the volume indicator to go from the red x to green bars, however there is still no sound:(

When I run the command aplay I get 

> james@ubuntu:~$ aplay -l
aplay: device_list:205: no soundcards found...


and when I run cat /proc/asound/cards I get

> cat: /proc/asound/cards: No such file or directory 

So for whatever reason ubuntu is not seeing the card.

I can feel there's a solution but with my limited linux experience I'm stumped. I hope someone else can help. I really don't want to re-install

---

### Post by loboc on 2008-08-13
can you post the result of 
```
lspci
``` 
and
```
lsmod | grep snd
```

---

### Post by anathema415 on 2008-08-13
Sure!

lspci:

> 00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem


lsmod | grep snd:

> james@ubuntu:~$ lsmod | grep snd
james@ubuntu:~$ 


I get nothing on that

---

### Post by anathema415 on 2008-08-13
just so you know i am now in the gutsy livecd i have and sound works in here, so the soundcard is not dead:)

---

### Post by loboc on 2008-08-13
whats the alsa driver that gets loaded off the live cd 

check the live cd lsmod | grep snd

---

### Post by anathema415 on 2008-08-13
> ubuntu@ubuntu:~$ lsmod | grep snd
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm


i installed the hda intel yesterday to no effect though

---

### Post by loboc on 2008-08-13
did you 

```

sudo modprobe snd-hda-intel

```

what errors if any does that return

---

### Post by anathema415 on 2008-08-13
Nada

> james@ubuntu:~$ sudo modprobe snd-hda-intel
[sudo] password for james: 
james@ubuntu:~$ 


---

### Post by loboc on 2008-08-13
does the lsmod so it got loaded

---

### Post by loboc on 2008-08-13
if the the module insertion completed succesfully then the output of aplay -L should change to show the device

---

### Post by anathema415 on 2008-08-13
still aplay: device_list:205: no soundcards found...

---

### Post by loboc on 2008-08-13
at boot use the grub menu to go back a kernel version and see what happens,

---

### Post by anathema415 on 2008-08-13
Are there commands for that? How do I do it?

---

### Post by anathema415 on 2008-08-13
Ok I went into the .18 kernel. No sound. Low Graphics mode, etc.. While booting in I caught some of the messages and there was a fail, but it went to fast for me to see. So I did dmesg. I did another dmesg for the .19 kernel. I'm attaching both to see if those help.

---

### Post by loboc on 2008-08-13
well I am stumped, I dont see a reason the alsa drivers are loading off the cd but are not loading inyour current config you can try to force them by adding 

snd-hda-intel

to 

/etc/modules

---

### Post by anathema415 on 2008-08-13
Well that didn't work either :(

If anyone has any suggestions please add them otherwise it's re-install time.

---

### Post by anathema415 on 2008-08-13
I did lsmod | grep snd on my install and get:

> snd_hda_intel         344728  1 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  2 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  2 snd


Is that anything that can help me?

---

### Post by loboc on 2008-08-14
well now you have sound drivers if a device shows up in 

aplay -L

then you should be able to play sounds,

aplay /usr/share/sounds/alsa/Noise.wav

if that doesnt make noise check to see if things are muted using 

alsamixer

once alsa works its a mtter of getting gnome to play nice with alsa which is the job of pulseaudio or you can use alsa directly by selecting alsa in

System>Preferences>Sound>Devices

---

### Post by anathema415 on 2008-08-14
aplay -l still can't find the card

---

### Post by loboc on 2008-08-14
[http://ubuntuforums.org/showthread.php?t=205449&highlight=hardy+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=hardy+sound)

I dont know what else to tell you good luck

---

### Post by drawhole on 2008-08-14
hmmm this seems to be more complicated than what I did, but i have the same thing happen on hardy ... i just installed a restricted driver from Adept i was using kde at the time... but it mite work... not sure, but the problem you described in the first place sounded like what happened to me.

---

### Post by anathema415 on 2008-08-14
> **drawhole said:**
> hmmm this seems to be more complicated than what I did, but i have the same thing happen on hardy ... i just installed a restricted driver from Adept i was using kde at the time... but it mite work... not sure, but the problem you described in the first place sounded like what happened to me.

I don't understand. You installed a restricted driver then the sound stopped?

---

### Post by drawhole on 2008-08-14
No, sry i should have been more clear ....

i had this issuse happen a while ago i was using kde and after install my sound was not working ... not sure if it was a red x but not working ...


I installed the restricted drivers for it and it worked ....  hmmm i was using my old  Emachine at the time so 5 or 6 monthes ago.

---

### Post by anathema415 on 2008-08-14
Consider this matter closed. I did a clean install.

---

