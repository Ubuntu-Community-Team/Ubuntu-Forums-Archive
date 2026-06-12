---
title: "Audio through HDTV &amp; Analog"
date: 2012-01-18
forum: Mythbuntu
---

### Post by cedyathome on 2012-01-18
Audio through HDMI works fine, but I get no output from the headphone jacks or audio-out (analog-stereo). How do I configure the system to get both?

My browser (firefox) audio output goes through the headphone jacks & audio-out, but not hdmi. This is for information only - I do not need browser audio through hdmi.

I use the ASUS M3N78-VM motherboard, v.24.1 version of mythtv, Ubuntu 10.10. Updates are all current.

Output of 
```
aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I do not use any .asoundrc or .asound.conf file in the home directory.

Mythtv frontend and backend are on the same machine.
Mythtv Front end setting for [COLOR=#000000][FONT=Arial]Audio Output Device ALSA:hw:CARD=NVidia,DEV=3[/FONT][/COLOR]

Please help with a solution or a pointer to a tutorial that will help me understand what I'm supposed to be doing.

Thank you.

---

### Post by nickrout on 2012-01-18
> **cedyathome said:**
> Audio through HDMI works fine, but I get no output from the headphone jacks or audio-out (analog-stereo). How do I configure the system to get both?

My browser (firefox) audio output goes through the headphone jacks & audio-out, but not hdmi. This is for information only - I do not need browser audio through hdmi.

I use the ASUS M3N78-VM motherboard, v.24.1 version of mythtv, Ubuntu 10.10. Updates are all current.

Output of 
```
aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I do not use any .asoundrc or .asound.conf file in the home directory.

Mythtv frontend and backend are on the same machine.
Mythtv Front end setting for [COLOR=#000000][FONT=Arial]Audio Output Device ALSA:hw:CARD=NVidia,DEV=3[/FONT][/COLOR]

Please help with a solution or a pointer to a tutorial that will help me understand what I'm supposed to be doing.

Thank you.

There are several threads about this on the mailing list. I think the answer is in an appropriate /etc/asound.conf

[http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)

---

### Post by cedyathome on 2012-01-20
Thanks for the suggestion. I used a template provided at 

[http://alsa.opensrc.org/.asoundrc#Dupe_output_to_multiple_cards](http://alsa.opensrc.org/.asoundrc#Dupe_output_to_multiple_cards)

to create my .asoundrc and it allow sound from the browser or other music players to go through analog and hdmi outputs. (I am no expert at this & am learning as I go)

But, when I try to use it with Mythtv, it will not recognize ALSA:default as a valid entry (after the Scan for Audio devices). Even if I don't do the scan, I get no sound out of Mythtv if I use ALSA:default. Also, my HDMI output disappears!

Here's my .asoundrc 
Can anyone tell me what I'm doing wrong or how mythtv v.24.1 reads alsa config files?

```

pcm.!default plug:both

ctl.!default {
  type hw
  card NVidia
  dev 3
}

pcm.both {
  type route;
  slave.pcm {
      type multi;
      slaves.a.pcm "HDMI";
      slaves.b.pcm "ANALOG";
      slaves.a.channels 2;
      slaves.b.channels 2;
      bindings.0.slave a;
      bindings.0.channel 0;
      bindings.1.slave a;
      bindings.1.channel 1;

      bindings.2.slave b;
      bindings.2.channel 0;
      bindings.3.slave b;
      bindings.3.channel 1;
  }

  ttable.0.0 1;
  ttable.1.1 1;

  ttable.0.2 1; # front left
  ttable.1.3 1; # front right
}

ctl.both {
  type hw;
  card NVidia
  dev 3;
}

pcm.ANALOG {
   type dmix
   ipc_key 1024
   slave {
       pcm "hw:0,0"
#       period_time 0
#       period_size 2048
##        buffer_size 8192
#       buffer_size 65536
#       buffer_time 0
#       periods 128
       rate 48000
       channels 2
    }
    bindings {
       0 0
       1 1
    }
}

pcm.HDMI {
   type dmix
   ipc_key 2048
   slave {
       pcm "hw:0,3"
#       period_time 0
#       period_size 2048
##        buffer_size 8192
#       buffer_size 65536
#       buffer_time 0
#       periods 128
       rate 48000
       channels 2
    }
    bindings {
       0 0
       1 1
    }
}

ctl.ANALOG {
   type hw
   card "NVidia"
   dev 0
}

ctl.HDMI {
   type hw
   card "NVidia"
   dev 3
}

```

---

### Post by nickrout on 2012-01-20
> **cedyathome said:**
> Thanks for the suggestion. I used a template provided at 

[http://alsa.opensrc.org/.asoundrc#Dupe_output_to_multiple_cards](http://alsa.opensrc.org/.asoundrc#Dupe_output_to_multiple_cards)

to create my .asoundrc and it allow sound from the browser or other music players to go through analog and hdmi outputs. (I am no expert at this & am learning as I go)

But, when I try to use it with Mythtv, it will not recognize ALSA:default as a valid entry (after the Scan for Audio devices). Even if I don't do the scan, I get no sound out of Mythtv if I use ALSA:default. Also, my HDMI output disappears!

Here's my .asoundrc 
Can anyone tell me what I'm doing wrong or how mythtv v.24.1 reads alsa config files?



Look in the mailing list, the answers are there.

---

### Post by cedyathome on 2012-01-27
I finally figured it out! I found this interesting tidbit about v0.24

"Also supports definitions in the ~/.asoundrc file, so long as the hint{} attribute was used."

I got this information from [http://www.mythtv.org/wiki/Release_Notes_-_0.24#Audio](http://www.mythtv.org/wiki/Release_Notes_-_0.24#Audio) following the #23794.

I changed the following in the definition of default in my previous .asoundrc  to add the hint{} attribut and it works!

pcm.!default {
   type plug
   slave {
    pcm "both"
    }
   hint {
    show on
    description "Multiple Output"
  }
}
Now, when you "Scan for Audio Devices" after entering ALSA:default in the Audio Output field, mythtv does not flag an error and can use the device.

I've found a number of .asoundrc scripts that work to get audio over multiple outputs, but unless you have the Hint attribute **mythtv v.024 **will not work with it.

Thanks for the help.

---

### Post by Bara84 on 2012-02-05
Hey,

I also have the M3N78-VM. So far I get no sound using the back outs. I tried following:

- purged pulseaudio
- created the asoundrc like in this thread named .asoundrc placed in /home/myuser

Output of found cards is

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfce78000 irq 21

So, what might be wrong in my setup? :o

---

### Post by nickrout on 2012-02-06
> **Bara84 said:**
> Hey,

I also have the M3N78-VM. So far I get no sound using the back outs. I tried following:

- purged pulseaudio
- created the asoundrc like in this thread named .asoundrc placed in /home/myuser

Output of found cards is

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfce78000 irq 21

So, what might be wrong in my setup? :o

What is a backout?

---

### Post by Bara84 on 2012-02-09
"backside output" of my pc tower (opposite of front outputs). ;-)

Sorry, I am no native in English...

---

### Post by nickrout on 2012-02-09
I think you need to start a new thread as your question has nothing to do with the topic being discussed in this thread.

---

