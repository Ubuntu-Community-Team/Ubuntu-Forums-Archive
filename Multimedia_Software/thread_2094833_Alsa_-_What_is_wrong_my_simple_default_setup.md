---
title: "Alsa - What is wrong my simple default setup?"
date: 2012-12-14
forum: Multimedia Software
---

### Post by PeterTaps on 2012-12-14
Folks,

I am running minimal Ubuntu 12.04 with openbox. The system does not have any pulseaudio stuff. 

I just installed a Soundblaster Audigy card. Ubuntu automatically recognized the card and installed the driver.

$ cat /proc/asound/cards

0 [PCH
1 [CA0106

$ aplay -L
...
surround51:CARD=CA0106,DEV=0
...

$ speaker-test -c6 -twav -Dsurround51:CARD=CA0106

This works perfectly. Each speaker works as expected.

Now, I just want CA0106 to be my default. So I created ~/.asoundrc with the following lines:

pcm.!default {
  type hw
  card CA0106
}

ctl.!default {
   type hw
   card CA0106
}

After the reboot, I tried the following command:

$ speaker-test -c6 -twav

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument

I am confused. Why doesn't this work? Is there something wrong with my .asoundrc definition?

Appreciate your help.

Regards,
Peter

---

### Post by BicyclerBoy on 2012-12-15
The hw device does not support auto channnel num & rate conversion.
If you send 48K stereo it might work..

You want the surround5.1 (6 PCM to discrete analogue outputs) to be default.

Try this for a guess:
```

pcm.!default {
   @args.0 SLAVE
   @args.SLAVE {
               type string
               default "surround51"
   }
   type route
   slave {
         pcm $SLAVE
         channels 6
   }
   ttable {
     0.0= 1
     1.1= 1
     2.2= 1
     3.3= 1
     4.4= 1
     5.5= 1
   }
}

```

---

### Post by Yellow Pasque on 2012-12-15
Note that your onboard audio has index 0, so it may be easier to set your soundblaster to index 0 (or for really easy solution, disable onboard audio on BIOS).

---

