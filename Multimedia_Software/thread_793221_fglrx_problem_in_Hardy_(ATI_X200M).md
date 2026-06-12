---
title: "fglrx problem in Hardy (ATI X200M)"
date: 2008-05-13
forum: Multimedia Software
---

### Post by Veyron on 2008-05-13
I recently upgraded from Gutsy to Hardy (this never happened in gutsy:() and began to have problems with fglrx and my screen when using compiz/normal visual effects. What happens is, my screen will stop updating itself (if I'm watching a video, it stays on the same frame) and my windows appear to still be open but also on the bottom of the screen too. For example, if I move Firefox by dragging the title bar, it shows me moving it on the bottom of the screen. It's a little hard to describe. Usually, I have to restart X,(Ctrl-Alt-Backspace)and then I'm good to go until the problem manifests itself again. Also, if I don't use compiz/normal appearances, that is no compositing or special effects it doesn't happen. I've looked at some of the other threads but this is not a screen flickering or a blank screen. I am using the 32bit version of Hardy Heron with an AMD64 processor and ATI X200M video. Output of the system log file when the event happens is as follows:

```
May 13 01:00:42 vladimir-laptop kernel: [51018.816690] [fglrx] interrupt source 20008000 successfully disabled!
May 13 01:00:42 vladimir-laptop kernel: [51018.816702] [fglrx] enable ID = 0x00000000
May 13 01:00:42 vladimir-laptop kernel: [51018.816709] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000004
May 13 01:01:02 vladimir-laptop kernel: [22663.582953] [fglrx] PCIe has already been initialized. Reinitializing ...
May 13 01:01:02 vladimir-laptop kernel: [22663.591456] [fglrx] GART Table is not in FRAME_BUFFER range 
May 13 01:01:02 vladimir-laptop kernel: [22663.591468] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
May 13 01:01:02 vladimir-laptop kernel: [22663.591471] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
May 13 01:01:02 vladimir-laptop kernel: [22663.678916] [fglrx] interrupt source 20008000 successfully enabled
May 13 01:01:02 vladimir-laptop kernel: [22663.678924] [fglrx] enable ID = 0x00000004
May 13 01:01:02 vladimir-laptop kernel: [22663.679775] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
May 13 01:01:17 vladimir-laptop pulseaudio[8051]: pid.c: Stale PID file, overwriting.
May 13 01:01:17 vladimir-laptop pulseaudio[8051]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
May 13 01:01:17 vladimir-laptop pulseaudio[8051]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
```

---

### Post by Veyron on 2008-05-14
bump

---

### Post by Veyron on 2008-05-27
Seriously, no one has any advice? c'mon..

---

### Post by Veyron on 2008-05-30
buuuuump!

---

### Post by Veyron on 2008-06-06
bump

---

