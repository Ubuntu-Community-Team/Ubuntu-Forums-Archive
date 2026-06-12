---
title: "No sound in right channel. Asus M2A-VM HDMI."
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by Jurin on 2007-10-28
Hello everyone.

Relevant hardware: Asus M2A-VM HDMI, AMD X2 4400+

Odd problem with my new Ubuntu 7.10 box: no sound from the right front channel. The right channel gets lost if I connect thru the motherboards back-panel plug (analog stereo). But if I connect thru the front panel connector and unmute the "headphone" -section from alsamixer , it works perfectly.

I am beginning to wonder if this is a hardware problem (faulty connector on the mobo maybe). 

Any ideas?

---

### Post by Jurin on 2007-10-30
I found a temporary fix.

(updated alsa to [1.0.15]("http://www.alsa-project.org/main/index.php/Download"))

Configured .asoundrc
```

# for 5.1 speakers
pcm.hda-intel {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 1
         ttable.1.5 1
}

```


And /etc/rc.local 
```
...
echo Setting 5.1 Channel volumes...
amixer -q set Master 100% unmute 
amixer -q set PCM 40% unmute  
amixer -q set Surround 100% unmute  
amixer -q set "Surround Jack Mode" "Independent"  
amixer -q set Center 81% unmute  
amixer -q set LFE 100% unmute  
amixer -q set "Mic select" "Mic1"   
amixer -q set "Mic" 65% unmute  
amixer -q set "Channel mode" "6ch"   
amixer -q set "Center/LFE Down mix" mute   
amixer -q set "Duplicate Front" mute
```

[Source here.  ALSA Multi-channel Audio mini-HOWTO]("http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml")

Now the front left and front right channels come out from the rear channels plug on the motherboard. This is a dump fix, but it works.

---

### Post by dkdwong on 2008-04-05
I have exactly the same problem in Gutsy and Hardy.

I will give this a try.  

I also had problems with ATI video in Gutsy but seems to be partially solved in Hardy.

Thx

---

