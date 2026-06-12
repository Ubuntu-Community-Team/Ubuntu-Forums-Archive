---
title: "Mencoder and Black &amp;white"
date: 2006-10-20
forum: Multimedia &amp; Video
---

### Post by tzulberti on 2006-10-20
Hi. I have a generic tv card, and it works great in tvtime (i have sound and image). Nevertheless, i want to make videos, so I use the following command:
mencoder -tv driver=v4l2:width=640:height=480:norm=pal_nc:input=2:chanlist=argentina:channel=43 -ffourcc DIVX -fps 25 -ovc lavc -lavcopts vcodec=mpeg4:vhq -oac mp3lame -lameopts cbr:br=128 -endpos 30 -o outfile.mpg tv://

I use argentina and pal_nc, becuase i am in argentina, and is the same configuration I have in tvtime. 

I do not know why the video that is saved, it does not has any colours, It is only black and white.

Thanks,
Tomas Zulberti

---

### Post by Jose Catre-Vandis on 2006-10-22
The only time I see b&w is when NTSC is the file format (If I change my TV to NTSC it goes B&W)

Have you tried just norm=pal ?

---

### Post by tzulberti on 2006-10-23
Thanks for answering, but nevertheless i tired it and i can only see b&w

---

### Post by Jose Catre-Vandis on 2006-10-23
What do you see if you use mplayer to view TV. Colour or Black and White?

(should be something like)
```
mplayer -tv driver=v4l2:width=640:height=480:norm=pal_nc:input =2:chanlist=argentina:channel=43 tv://
```

---

### Post by tzulberti on 2006-10-25
> **Jose Catre-Vandis said:**
> What do you see if you use mplayer to view TV. Colour or Black and White?

(should be something like)
```
mplayer -tv driver=v4l2:width=640:height=480:norm=pal_nc:input =2:chanlist=argentina:channel=43 tv://
```

yes, I see b&w... I have just noticed that it does not use the channel I pass (43), but it uses the one that was set by tvtime the last time i closed it..

---

### Post by Jose Catre-Vandis on 2006-10-27
Hmmm, so it may be something to do with the channel you are calling or your output format?

Try this:
```
mplayer -tv on:driver=v4l2:width=640:height=480:outfmt=i420 -vc rawi420 -vo xv
```

I know you are Pal-NC in Argentina, but try some other PAL variants, and check that TVTime is using PAL-NC to give you colour

---

### Post by tzulberti on 2006-10-27
Thanks a lot for helping me...
if I run your command this is the output..

MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 47, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


-tv on is deprecated, use tv:// instead.

if i delete "-tv" and use tv://, all i see is a green window...

---

### Post by Jose Catre-Vandis on 2006-10-28
Right, sorry. Now I am awake, I can perhaps be of a bit more help. As you rightly say, mplayer picks up the last channel tvtime was playing. This is my config for tvtime (and I am in the UK so some settings will be different from yours). This file is in /home/"user"/.tvtime/tvtime.xml
```
<?xml version="1.0"?>
<!DOCTYPE tvtime PUBLIC "-//tvtime//DTD tvtime 1.0//EN" "http://tvtime.sourceforge.net/DTD/tvtime1.dtd">
<tvtime xmlns="http://tvtime.sourceforge.net/DTD/">
  <option name="Channel" value="102"/>
  <option name="WideScreen" value="1"/>
  <option name="DefaultBrightness" value="-1"/>
  <option name="DefaultContrast" value="-1"/>
  <option name="DefaultSaturation" value="-1"/>
  <option name="DefaultHue" value="-1"/>
  <option name="PrevChannel" value="98"/>
  <option name="FramerateMode" value="0"/>
  <option name="OverScan" value="0.0"/>
  <option name="CheckForSignal" value="1"/>
  <option name="AudioBoost" value="100"/>
  <option name="AlwaysOnTop" value="1"/>
  <option name="QuietScreenshots" value="0"/>
  <option name="UnmuteVolume" value="14135"/>
  <option name="Muted" value="0"/>
  <option name="V4LInput" value="0"/>
  <option name="AudioMode" value="stereo"/>
  <option name="PalDKMode" value="0"/>
<option name="DeinterlaceMethod" value="TelevisionFull"/><option name="FullScreen" value="0"/><option name="MirrorInput" value="0"/><option name="InputWidth" value="720"/></tvtime>

```

The channel listing from the same directory is as follows:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE stationlist PUBLIC "-//tvtime//DTD stationlist 1.0//EN" "http://tvtime.sourceforge.net/DTD/stationlist1.dtd">
<stationlist xmlns="http://tvtime.sourceforge.net/DTD/">
  <list frequencies="europe" norm="PAL" audio="dk">
    <station audio="auto" position="1" active="0" band="VHF E2-E12" name="1" finetune="0" channel="E1" norm="PAL"/>
    <station audio="auto" position="2" active="0" band="VHF E2-E12" name="2" finetune="0" channel="E2" norm="PAL"/>
    <station audio="auto" position="3" active="0" band="VHF E2-E12" name="3" finetune="0" channel="E3" norm="PAL"/>
    <station audio="auto" position="4" active="0" band="VHF E2-E12" name="4" finetune="0" channel="E4" norm="PAL"/>
    <station audio="auto" position="5" active="0" band="VHF E2-E12" name="5" finetune="0" channel="E5" norm="PAL"/>
    <station audio="auto" position="6" active="0" band="VHF E2-E12" name="6" finetune="0" channel="E6" norm="PAL"/>
    <station audio="auto" position="7" active="0" band="VHF E2-E12" name="7" finetune="0" channel="E7" norm="PAL"/>
    <station audio="auto" position="8" active="0" band="VHF E2-E12" name="8" finetune="0" channel="E8" norm="PAL"/>
    <station audio="auto" position="9" active="0" band="VHF E2-E12" name="9" finetune="0" channel="E9" norm="PAL"/>
    <station audio="auto" position="10" active="0" band="VHF E2-E12" name="10" finetune="0" channel="E10" norm="PAL"/>
    <station audio="auto" position="11" active="0" band="VHF E2-E12" name="11" finetune="0" channel="E11" norm="PAL"/>
    <station audio="auto" position="12" active="0" band="VHF E2-E12" name="12" finetune="0" channel="E12" norm="PAL"/>
    <station audio="auto" position="13" active="0" band="VHF S1-S41" name="13" finetune="0" channel="S1" norm="PAL"/>
    <station audio="auto" position="14" active="0" band="VHF S1-S41" name="14" finetune="0" channel="S2" norm="PAL"/>
    <station audio="auto" position="15" active="0" band="VHF S1-S41" name="15" finetune="0" channel="S3" norm="PAL"/>
    <station audio="auto" position="16" active="0" band="VHF S1-S41" name="16" finetune="0" channel="S4" norm="PAL"/>
    <station audio="auto" position="17" active="0" band="VHF S1-S41" name="17" finetune="0" channel="S5" norm="PAL"/>
    <station audio="auto" position="18" active="0" band="VHF S1-S41" name="18" finetune="0" channel="S6" norm="PAL"/>
    <station audio="auto" position="19" active="0" band="VHF S1-S41" name="19" finetune="0" channel="S7" norm="PAL"/>
    <station audio="auto" position="20" active="0" band="VHF S1-S41" name="20" finetune="0" channel="S8" norm="PAL"/>
    <station audio="auto" position="21" active="0" band="VHF S1-S41" name="21" finetune="0" channel="S9" norm="PAL"/>
    <station audio="auto" position="22" active="0" band="VHF S1-S41" name="22" finetune="0" channel="S10" norm="PAL"/>
    <station audio="auto" position="23" active="0" band="VHF S1-S41" name="23" finetune="0" channel="S11" norm="PAL"/>
    <station audio="auto" position="24" active="0" band="VHF S1-S41" name="24" finetune="0" channel="S12" norm="PAL"/>
    <station audio="auto" position="25" active="0" band="VHF S1-S41" name="25" finetune="0" channel="S13" norm="PAL"/>
    <station audio="auto" position="26" active="0" band="VHF S1-S41" name="26" finetune="0" channel="S14" norm="PAL"/>
    <station audio="auto" position="27" active="0" band="VHF S1-S41" name="27" finetune="0" channel="S15" norm="PAL"/>
    <station audio="auto" position="28" active="0" band="VHF S1-S41" name="28" finetune="0" channel="S16" norm="PAL"/>
    <station audio="auto" position="29" active="0" band="VHF S1-S41" name="29" finetune="0" channel="S17" norm="PAL"/>
    <station audio="auto" position="30" active="0" band="VHF S1-S41" name="30" finetune="0" channel="S18" norm="PAL"/>
    <station audio="auto" position="31" active="0" band="VHF S1-S41" name="31" finetune="0" channel="S19" norm="PAL"/>
    <station audio="auto" position="32" active="0" band="VHF S1-S41" name="32" finetune="0" channel="S20" norm="PAL"/>
    <station audio="auto" position="33" active="0" band="VHF S1-S41" name="33" finetune="0" channel="S21" norm="PAL"/>
    <station audio="auto" position="34" active="0" band="VHF S1-S41" name="34" finetune="0" channel="S22" norm="PAL"/>
    <station audio="auto" position="35" active="0" band="VHF S1-S41" name="35" finetune="0" channel="S23" norm="PAL"/>
    <station audio="auto" position="36" active="0" band="VHF S1-S41" name="36" finetune="0" channel="S24" norm="PAL"/>
    <station audio="auto" position="37" active="0" band="VHF S1-S41" name="37" finetune="0" channel="S25" norm="PAL"/>
    <station audio="auto" position="38" active="0" band="VHF S1-S41" name="38" finetune="0" channel="S26" norm="PAL"/>
    <station audio="auto" position="39" active="0" band="VHF S1-S41" name="39" finetune="0" channel="S27" norm="PAL"/>
    <station audio="auto" position="40" active="0" band="VHF S1-S41" name="40" finetune="0" channel="S28" norm="PAL"/>
    <station audio="auto" position="41" active="0" band="VHF S1-S41" name="41" finetune="0" channel="S29" norm="PAL"/>
    <station audio="auto" position="42" active="0" band="VHF S1-S41" name="42" finetune="0" channel="S30" norm="PAL"/>
    <station audio="auto" position="43" active="0" band="VHF S1-S41" name="43" finetune="0" channel="S31" norm="PAL"/>
    <station audio="auto" position="44" active="0" band="VHF S1-S41" name="44" finetune="0" channel="S32" norm="PAL"/>
    <station audio="auto" position="45" active="0" band="VHF S1-S41" name="45" finetune="0" channel="S33" norm="PAL"/>
    <station audio="auto" position="46" active="0" band="VHF S1-S41" name="46" finetune="0" channel="S34" norm="PAL"/>
    <station audio="auto" position="47" active="0" band="VHF S1-S41" name="47" finetune="0" channel="S35" norm="PAL"/>
    <station audio="auto" position="48" active="0" band="VHF S1-S41" name="48" finetune="0" channel="S36" norm="PAL"/>
    <station audio="auto" position="49" active="0" band="VHF S1-S41" name="49" finetune="0" channel="S37" norm="PAL"/>
    <station audio="auto" position="50" active="0" band="VHF S1-S41" name="50" finetune="0" channel="S38" norm="PAL"/>
    <station audio="auto" position="51" active="0" band="VHF S1-S41" name="51" finetune="0" channel="S39" norm="PAL"/>
    <station audio="auto" position="52" active="0" band="VHF S1-S41" name="52" finetune="0" channel="S40" norm="PAL"/>
    <station audio="auto" position="53" active="0" band="VHF S1-S41" name="53" finetune="0" channel="S41" norm="PAL"/>
    <station audio="auto" position="54" active="0" band="VHF Misc" name="54" finetune="0" channel="X" norm="PAL"/>
    <station audio="auto" position="55" active="0" band="VHF Misc" name="55" finetune="0" channel="Y" norm="PAL"/>
    <station audio="auto" position="56" active="0" band="VHF Misc" name="56" finetune="0" channel="Z" norm="PAL"/>
    <station audio="auto" position="57" active="0" band="VHF Misc" name="57" finetune="0" channel="Z+1" norm="PAL"/>
    <station audio="auto" position="58" active="0" band="VHF Misc" name="58" finetune="0" channel="Z+2" norm="PAL"/>
    <station audio="auto" position="59" active="0" band="VHF Russia" name="59" finetune="0" channel="R1" norm="PAL"/>
    <station audio="auto" position="60" active="0" band="VHF Russia" name="60" finetune="0" channel="R2" norm="PAL"/>
    <station audio="auto" position="61" active="0" band="VHF Russia" name="61" finetune="0" channel="R3" norm="PAL"/>
    <station audio="auto" position="62" active="0" band="VHF Russia" name="62" finetune="0" channel="R4" norm="PAL"/>
    <station audio="auto" position="63" active="0" band="VHF Russia" name="63" finetune="0" channel="R5" norm="PAL"/>
    <station audio="auto" position="64" active="0" band="VHF Russia" name="64" finetune="0" channel="R7" norm="PAL"/>
    <station audio="auto" position="65" active="0" band="VHF Russia" name="65" finetune="0" channel="R8" norm="PAL"/>
    <station audio="auto" position="66" active="0" band="VHF Russia" name="66" finetune="0" channel="R9" norm="PAL"/>
    <station audio="auto" position="67" active="0" band="VHF Russia" name="67" finetune="0" channel="R10" norm="PAL"/>
    <station audio="auto" position="68" active="0" band="VHF Russia" name="68" finetune="0" channel="R11" norm="PAL"/>
    <station audio="auto" position="69" active="0" band="VHF Russia" name="69" finetune="0" channel="R12" norm="PAL"/>
    <station audio="auto" position="70" active="0" band="VHF Russia" name="70" finetune="0" channel="SR1" norm="PAL"/>
    <station audio="auto" position="71" active="0" band="VHF Russia" name="71" finetune="0" channel="SR3" norm="PAL"/>
    <station audio="auto" position="72" active="0" band="VHF Russia" name="72" finetune="0" channel="SR4" norm="PAL"/>
    <station audio="auto" position="73" active="0" band="VHF Russia" name="73" finetune="0" channel="SR5" norm="PAL"/>
    <station audio="auto" position="74" active="0" band="VHF Russia" name="74" finetune="0" channel="SR6" norm="PAL"/>
    <station audio="auto" position="75" active="0" band="VHF Russia" name="75" finetune="0" channel="SR7" norm="PAL"/>
    <station audio="auto" position="76" active="0" band="VHF Russia" name="76" finetune="0" channel="SR8" norm="PAL"/>
    <station audio="auto" position="77" active="0" band="VHF Russia" name="77" finetune="0" channel="SR12" norm="PAL"/>
    <station audio="auto" position="78" active="0" band="VHF Russia" name="78" finetune="0" channel="SR13" norm="PAL"/>
    <station audio="auto" position="79" active="0" band="VHF Russia" name="79" finetune="0" channel="SR14" norm="PAL"/>
    <station audio="auto" position="80" active="0" band="VHF Russia" name="80" finetune="0" channel="SR15" norm="PAL"/>
    <station audio="auto" position="81" active="0" band="VHF Russia" name="81" finetune="0" channel="SR16" norm="PAL"/>
    <station audio="auto" position="82" active="0" band="VHF Russia" name="82" finetune="0" channel="SR17" norm="PAL"/>
    <station audio="auto" position="83" active="0" band="VHF Russia" name="83" finetune="0" channel="SR19" norm="PAL"/>
    <station audio="auto" position="84" active="0" band="VHF Italy" name="84" finetune="0" channel="A" norm="PAL"/>
    <station audio="auto" position="85" active="0" band="VHF Italy" name="85" finetune="0" channel="C" norm="PAL"/>
    <station audio="auto" position="86" active="0" band="VHF Italy" name="86" finetune="0" channel="E" norm="PAL"/>
    <station audio="auto" position="87" active="0" band="VHF Italy" name="87" finetune="0" channel="F" norm="PAL"/>
    <station audio="auto" position="88" active="0" band="VHF Italy" name="88" finetune="0" channel="G" norm="PAL"/>
    <station audio="auto" position="89" active="0" band="VHF Ireland" name="89" finetune="0" channel="I1" norm="PAL"/>
    <station audio="auto" position="90" active="0" band="VHF Ireland" name="90" finetune="0" channel="I3" norm="PAL"/>
    <station audio="auto" position="91" active="0" band="VHF Ireland" name="91" finetune="0" channel="I7" norm="PAL"/>
    <station audio="auto" position="92" active="1" band="UHF" name="92" finetune="0" channel="U21" norm="PAL"/>
    <station audio="auto" position="93" active="0" band="UHF" name="93" finetune="0" channel="U22" norm="PAL"/>
    <station audio="auto" position="94" active="0" band="UHF" name="94" finetune="0" channel="U23" norm="PAL"/>
    <station audio="auto" position="95" active="1" band="UHF" name="95" finetune="0" channel="U24" norm="PAL"/>
    <station audio="auto" position="96" active="0" band="UHF" name="96" finetune="0" channel="U25" norm="PAL"/>
    <station audio="auto" position="97" active="0" band="UHF" name="97" finetune="0" channel="U26" norm="PAL"/>
    <station audio="auto" position="98" active="1" band="UHF" name="98" finetune="0" channel="U27" norm="PAL"/>
    <station audio="auto" position="99" active="0" band="UHF" name="99" finetune="0" channel="U28" norm="PAL"/>
    <station audio="auto" position="100" active="0" band="UHF" name="100" finetune="0" channel="U29" norm="PAL"/>
    <station audio="auto" position="101" active="0" band="UHF" name="101" finetune="0" channel="U30" norm="PAL"/>
    <station audio="bg" position="102" active="1" band="UHF" name="102" finetune="0" channel="U31" norm="PAL"/>
    <station audio="auto" position="103" active="0" band="UHF" name="103" finetune="0" channel="U32" norm="PAL"/>
    <station audio="auto" position="104" active="0" band="UHF" name="104" finetune="0" channel="U33" norm="PAL"/>
    <station audio="auto" position="105" active="0" band="UHF" name="105" finetune="0" channel="U34" norm="PAL"/>
    <station audio="auto" position="106" active="0" band="UHF" name="106" finetune="0" channel="U35" norm="PAL"/>
    <station audio="auto" position="107" active="0" band="UHF" name="107" finetune="0" channel="U36" norm="PAL"/>
    <station audio="auto" position="108" active="0" band="UHF" name="108" finetune="0" channel="U37" norm="PAL"/>
    <station audio="auto" position="109" active="0" band="UHF" name="109" finetune="0" channel="U38" norm="PAL"/>
    <station audio="auto" position="110" active="0" band="UHF" name="110" finetune="0" channel="U39" norm="PAL"/>
    <station audio="auto" position="111" active="0" band="UHF" name="111" finetune="0" channel="U40" norm="PAL"/>
    <station audio="auto" position="112" active="0" band="UHF" name="112" finetune="0" channel="U41" norm="PAL"/>
    <station audio="auto" position="113" active="0" band="UHF" name="113" finetune="0" channel="U42" norm="PAL"/>
    <station audio="auto" position="114" active="0" band="UHF" name="114" finetune="0" channel="U43" norm="PAL"/>
    <station audio="auto" position="115" active="0" band="UHF" name="115" finetune="0" channel="U44" norm="PAL"/>
    <station audio="auto" position="116" active="0" band="UHF" name="116" finetune="0" channel="U45" norm="PAL"/>
    <station audio="auto" position="117" active="0" band="UHF" name="117" finetune="0" channel="U46" norm="PAL"/>
    <station audio="auto" position="118" active="0" band="UHF" name="118" finetune="0" channel="U47" norm="PAL"/>
    <station audio="auto" position="119" active="0" band="UHF" name="119" finetune="0" channel="U48" norm="PAL"/>
    <station audio="auto" position="120" active="0" band="UHF" name="120" finetune="0" channel="U49" norm="PAL"/>
    <station audio="auto" position="121" active="0" band="UHF" name="121" finetune="0" channel="U50" norm="PAL"/>
    <station audio="auto" position="122" active="0" band="UHF" name="122" finetune="0" channel="U51" norm="PAL"/>
    <station audio="auto" position="123" active="0" band="UHF" name="123" finetune="0" channel="U52" norm="PAL"/>
    <station audio="auto" position="124" active="0" band="UHF" name="124" finetune="0" channel="U53" norm="PAL"/>
    <station audio="auto" position="125" active="0" band="UHF" name="125" finetune="0" channel="U54" norm="PAL"/>
    <station audio="auto" position="126" active="0" band="UHF" name="126" finetune="0" channel="U55" norm="PAL"/>
    <station audio="auto" position="127" active="0" band="UHF" name="127" finetune="0" channel="U56" norm="PAL"/>
    <station audio="auto" position="128" active="0" band="UHF" name="128" finetune="0" channel="U57" norm="PAL"/>
    <station audio="auto" position="129" active="0" band="UHF" name="129" finetune="0" channel="U58" norm="PAL"/>
    <station audio="auto" position="130" active="0" band="UHF" name="130" finetune="0" channel="U59" norm="PAL"/>
    <station audio="auto" position="131" active="0" band="UHF" name="131" finetune="0" channel="U60" norm="PAL"/>
    <station audio="auto" position="132" active="0" band="UHF" name="132" finetune="0" channel="U61" norm="PAL"/>
    <station audio="auto" position="133" active="0" band="UHF" name="133" finetune="0" channel="U62" norm="PAL"/>
    <station audio="auto" position="134" active="0" band="UHF" name="134" finetune="0" channel="U63" norm="PAL"/>
    <station audio="auto" position="135" active="0" band="UHF" name="135" finetune="0" channel="U64" norm="PAL"/>
    <station audio="auto" position="136" active="0" band="UHF" name="136" finetune="0" channel="U65" norm="PAL"/>
    <station audio="auto" position="137" active="0" band="UHF" name="137" finetune="0" channel="U66" norm="PAL"/>
    <station audio="auto" position="138" active="0" band="UHF" name="138" finetune="0" channel="U67" norm="PAL"/>
    <station audio="auto" position="139" active="0" band="UHF" name="139" finetune="0" channel="U68" norm="PAL"/>
    <station audio="auto" position="140" active="0" band="UHF" name="140" finetune="0" channel="U69" norm="PAL"/>
  </list>
  <list frequencies="freevo" norm="PAL"/>
  <list frequencies="freevo" norm="PAL"/>
</stationlist>
```

I get good picture and sound

So now to mplayer

Inputting this to terminal I get good sound and picture:
```
mplayer -tv driver=v4l2:width=640:height=480:input=0 -vo xv tv://
```
(input=0 gives you TV, 1 composite, 2 Svideo)
The output in terminal is as follows:
```
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP Thoroughbred; Duron Applebred (Family: 6, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing tv://.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: ASUSTeK P7131 Dual
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO
 Capabilites:  video capture  video overlay  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = PAL; 1 = PAL-BG; 2 = PAL-I; 3 = PAL-DK; 4 = NTSC; 5 = SECAM; 6 = PAL-M; 7 = PAL-Nc; 8 = PAL-60;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video;
 Current input: 0
 Current format: BGR24
v4l2: current audio mode is : MONO
Opening video filter: [pp=0x20077]
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Audio: no sound
Starting playback...
v4l2: 123 frames successfully processed, 0 frames dropped.

```

Inputting this to terminal I also get good sound and picture:
```
 mplayer -tv driver=v4l2:width=640:height=480:input=0:outfmt=i420 -vc rawi420 -vo xv tv://
```
and the output in terminal is:
```
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP Thoroughbred; Duron Applebred (Family: 6, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing tv://.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: ASUSTeK P7131 Dual
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO
 Capabilites:  video capture  video overlay  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = PAL; 1 = PAL-BG; 2 = PAL-I; 3 = PAL-DK; 4 = NTSC; 5 = SECAM; 6 = PAL-M; 7 = PAL-Nc; 8 = PAL-60;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video;
 Current input: 0
 Current format: BGR24
v4l2: current audio mode is : MONO
Opening video filter: [pp=0x20077]
==========================================================================
Forced video codec: rawi420
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Planar I420)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar I420 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar I420
Selected video codec: [rawi420] vfm: raw (RAW I420)
==========================================================================
Audio: no sound
Starting playback...
v4l2: 715 frames successfully processed, 1 frames dropped.

```

Note: I do get sound, regardless of what mplayer is saying!

So try the same, and see what outputs you get in terminal, and if there are any significant differences with what I get. this might point us in the right direction. i would be interested to know what set of frequencies you are using and channels tuning to, as you do not have a list in tvtime?

Cheers Joe

---

### Post by tzulberti on 2006-10-28
Thanks for your help i was able to see it with sound and image:
mplayer -tv driver=v4l2:norm=pal-nc:width=640:height=480:input=2 -vo xv tv://


THANK YOU... :D :D :D :D

---

### Post by Jose Catre-Vandis on 2006-10-28
And in colour too I guess. That's great. it is the -vo xv that is doing the trick. You can select this as default in the gui version of mplayer, it is the xv  X11/xv option in Video tab. When using mencoder make sure you use this option somewhere so that you use the correct driver. 

Also, edit your original post heading to [SOLVED] as this will help others.

---

### Post by tzulberti on 2006-10-29
Thanks for all your help

---

