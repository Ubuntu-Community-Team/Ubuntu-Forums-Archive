---
title: "[SOLVED] USB MIDI--How Do I Speed It Up (lower the latency)???"
date: 2024-07-02
forum: Multimedia Software
---

### Post by 909mjolnir on 2024-07-02
UPDATE:  Solved even better by removing all pipewire and all pulseaudio, and then only reinstalling pipewire and pipewire-pulse without pulseaudio.  Then I just refixed the settings of my programs like audacious.  Now it's all working just fine.  Even my wine programs are working a little bit better.  I did have to select different driver parts in winecfg.  I use QasMixer (from repo, qastools) to set levels of audio and select devices.  This is a good combo.  Also, I updated the kernel and that helped too.  All these different things work together.  

I think my PulseAudio days are over, because I was tweaking it to be faster and better and then suddenly I had no audio at all and Pulse wouldn't start.  So it was finally the right thing to do to delete and remove PulseAudio.  Thankfully, it looks like pipewire is designed to be nicer:  

```

$ pacman -Ss pipewire-pulse pipewire-audio
extra/pipewire-pulse 1:1.0.7-2 [installed]
    Low-latency audio/video router and processor - PulseAudio replacement
extra/pipewire-audio 1:1.0.7-2 [installed]
    Low-latency audio/video router and processor - Audio support

```


OK, So I am successfully running and using Cockos Reaper in Linux and it's just barely useable in USB MIDI.  The WAV audio is fine, so I can actually get work done.  
However, in all my other Linux Audio Workstation programs, there's too much lag (slow responsiveness) in the USB MIDI.  What can I do to make it more playable?  

I'm using a KORG microKEY, without KORG Windows Drivers, no WINE, just USB Class Compliancy working for me.  
If the MIDI latency can be reduced a lot more, then I can get some progress with maybe LMMS or FL Studio or Energy XT.  

Hmm.  ?

UPDATE:  OK, so I think I maybe solved the problem.  

I did this:  

1) added to /etc/default/grub all of the MIDI kernel HZ parameters I could find online designed for MIDI to work better
2) reduced the polyphony of the VST instruments.  

Some of the droppouts (buffer underruns) were caused by too high synth polyphony.  
After I changed the grub kernel parameters, I updated grub and restarted.  

Now it seems to work OK.

My grub has this line:  

GRUB_CMDLINE_LINUX="CONFIG_HZ_1000=y CONFIG_HZ=1000 preempt=full threadirqs  tz=utc transparent_hugepages=0 transparent_hugepage=0 sysctl.vm.swappiness=10 nohz_full isolcpus=nohz CONFIG_USB_GADGET=y CONFIG_USB_CONFIGFS=y CONFIG_USB_CONFIGFS_F_MIDI2=y CONFIG_SND_UMP_LEGACY_RAWMIDI=y"

and I updated the grub.  
it might even work better on a new kernel, but I'm on my newest and only realtime kernel at the moment.

---

### Post by 909mjolnir on 2024-07-04
with the latency reduced, I can now play in to the DAW some musical notes without odd strange obnoxious delays and glitches.

---

