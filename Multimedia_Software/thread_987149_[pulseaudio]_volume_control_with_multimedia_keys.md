---
title: "[pulseaudio] volume control with multimedia keys ?"
date: 2008-11-19
forum: Multimedia Software
---

### Post by atlas95 on 2008-11-19
Hello, 
I have a openbox install, i search what are the command i must set for down/up/mute the volume with my multimedia key.

Could you help me please?

---

### Post by markjensen on 2008-11-19
First, you may need to get your keycodes for these special keys from the **xev** program that will dump the X events into your terminal screen.  So as you do mouse events, and keyboard events, the codes are dumped for you to see.

Use that program to get the key events for your volume keys you want to use.  It will dump output something like the following:```
KeyPress event, serial 32, synthetic NO, window 0x2000001,
    root 0x13a, subw 0x0, time 3204054097, (867,651), root:(868,673),
    state 0x0, keycode 161 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x2000001,
    root 0x13a, subw 0x0, time 3204054097, (867,651), root:(868,673),
    state 0x0, keycode 161 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```In this case, you see that the "keycode" is 161

Then (assuming openbox matches fluxbox in this matter) add the events to your keys file that contains your desired keyboard shortcuts.

In that case, for my system, 161 matches the calculator special key, so I have added the following entry to my keys file:```
None 161 :Exec xcalc
```You can execute any command line audio commands, such as alsa-mixer or what not.

I am not at my Linux box at the moment (I am on a short break at work), so I cannot be more specific at the moment, but I can check back on this thread later today if you have tried this and still have problems.

---

### Post by atlas95 on 2008-11-20
Hi, 
thanks for your help, could you help me to find what is the command to launch for set pulse volume, with command such as pacmd, pactl or whatever... I doesn't want to use alsamixer volume :)

---

### Post by kpkeerthi on 2008-11-20
[https://wiki.ubuntu.com/KeyTouch](https://wiki.ubuntu.com/KeyTouch)

---

### Post by atlas95 on 2008-11-20
Thanks but isn't the method to bind my multimedia keyboard that i search, but what is the command to attribute to set the PULSEAUDIO volume kpkeerthi ;)

---

### Post by markjensen on 2008-11-20
> **atlas95 said:**
> Thanks but isn't the method to bind my multimedia keyboard that i search, but what is the command to attribute to set the PULSEAUDIO volume kpkeerthi ;)

Unfortunately, you have caught me at work again.

I can see pulseaudio documentation here: [http://www.pulseaudio.org/wiki/CLI](http://www.pulseaudio.org/wiki/CLI)
But I can see an absolute setting, and not a +5% type of adjust that I am used to in alsa.

I haven't looked at keytouch, except to follow kpkeerthi's link, and not sure I would agree that an outside app would be better than using the native *box support.

(p.s. I see that Openbox uses a different keybinding system than fluxbox, so my example earlier will not apply, and you must use the openbox xml file that you are probably already familiar with)

---

### Post by Ast0815 on 2009-10-30
I managed to increase/decrease the volume of my pulseaudio with the following scripts.
Maybe they'll be of some use for other people:

vol+
```
#!/bin/bash

A=`pacmd dump | grep "set-sink-volume alsa_output.pci-0000_00_1b.0.analog-stereo" | cut -d " " -f 3`
B=$((A + 0x01000))
if [ $(($B)) -gt $((0x10000)) ]
 then
    B=$((0x10000))
fi
pactl set-sink-volume 0 `printf "0x%X" $B`

```vol-
```
#!/bin/bash

A=`pacmd dump | grep "set-sink-volume alsa_output.pci-0000_00_1b.0.analog-stereo" | cut -d " " -f 3`
B=$((A - 0x01000))
if [ $(($B)) -lt $((0x00000)) ]
 then
    B=$((0x00000))
fi
pactl set-sink-volume 0 `printf "0x%X" $B`

```mute
```
#!/bin/bash

A=`pacmd dump | grep "set-sink-mute alsa_output.pci-0000_00_1b.0.analog-stereo" | cut -d " " -f 3`
if [ $A = "no" ]
then
    pactl set-sink-mute 0 yes
else
    pactl set-sink-mute 0 no
fi
```

---

### Post by awg on 2010-04-16
The above scripts didn't work for me; they set the volume to a absolute levels instead of raising/lowering it.

The following zsh one-liners work great:

Volume up:
```
pacmd set-sink-volume 0 $(printf '0x%x' $(( $(pacmd dump|grep set-sink-volume|cut -f3 -d' ') + 0xf00)) )
```

Volume down:
```
pacmd set-sink-volume 0 $(printf '0x%x' $(( $(pacmd dump|grep set-sink-volume|cut -f3 -d' ') - 0xf00)) )
```

Mute:
```
pacmd set-sink-mute 0 $(if [ $(pacmd dump |grep set-sink-mute | cut -f 3 -d' ') = 'no' ]; then echo yes; else echo no; fi;)
```

Working well in my .awesomerc with zsh -c in front, should work fine in openbox configs as well.

---

### Post by johnlepikhin on 2010-12-12
Another script. Universal, based on AWK:

Volume up:

```
pacmd dump|awk --non-decimal-data '$1~/set-sink-volume/{system ("pacmd "$1" "$2" "$3+1000)}'
```

Volume down:

```
pacmd dump|awk --non-decimal-data '$1~/set-sink-volume/{system ("pacmd "$1" "$2" "$3-1000)}'
```

Mute:

```
pacmd dump|awk --non-decimal-data '$1~/set-sink-mute/{system ("pacmd "$1" "$2" "($3=="yes"?"no":"yes"))}'
```

---

### Post by alwayslurking on 2010-12-17
Extending those one-liners, adding the ability to jump larger increments and avoiding wrapping the volume to something huge when reducing (ouch!):

```
#!/bin/bash
[[ $0 == pa_vol_down ]] && _down=true 
[[ $1 ]] && let _vol_increment=$1*655 || _vol_increment=655
_full_line=`pacmd dump|grep "set-sink-volume"`
_sink_cmd=`echo $_full_line|cut -d" " -f1`
_sink_id=`echo $_full_line|cut -d" " -f2`
_sink_vol=`echo $_full_line|cut -d" " -f3`
[[ $_down ]] && let _vol=$_sink_vol-$_vol_increment || let _vol=$_sink_vol+$_vol_increment
[[ $_vol -lt 0 ]] && _vol=0
[[ $_vol -gt 65536 ]] && _vol=65536
pacmd $_sink_cmd $_sink_id $_vol > /dev/null
```

Create two links to that script, named pa_vol_up and pa_vol_down, then they can be run without parameters to step up/down by 1% or with a single parameter to make that the step. E.g.;

pa_vol_up 10
pa_vol_down 15

I'm sure there's an elegant way to extract the 3 elements of the dump and manipulate them, but I'm a bear of very little brain, so I've done my best.

---

### Post by cynyr on 2011-01-26
> **alwayslurking said:**
> 
```
#!/bin/bash
[[ $0 == pa_vol_down ]] && _down=true 
[[ $1 ]] && let _vol_increment=$1*655 || _vol_increment=655
_full_line=`pacmd dump|grep "set-sink-volume"`
_sink_cmd=`echo $_full_line|cut -d" " -f1`
_sink_id=`echo $_full_line|cut -d" " -f2`
_sink_vol=`echo $_full_line|cut -d" " -f3`
[[ $_down ]] && let _vol=$_sink_vol-$_vol_increment || let _vol=$_sink_vol+$_vol_increment
[[ $_vol -lt 0 ]] && _vol=0
[[ $_vol -gt 65536 ]] && _vol=65536
pacmd $_sink_cmd $_sink_id $_vol > /dev/null
```

```
 [[ $0 == pa_vol_down ]] && _down=true
```
should be
```
 [[ ${0##*/} == pa_vol_down ]] && _down=true
```
to avoid problems where the full path is used.

Other than that great script. I like how bash handles the conversion from hex to decimal on its own.

---

### Post by uriel1998 on 2012-02-10
I'm using a ruby script that actually changes *all* sinks at the same time - which comes in handy when you've suddenly started using an external USB speaker and all your keybound scripts work with only one sink.

I can't take credit for most of it - I forked and tweaked it a tiny bit.  The original script is here: [https://gist.github.com/814634](https://gist.github.com/814634);  I couldn't get it to run because of something in the muting code, so I fixed that and added in some output in case someone wants to send it to notify-osd or somesuch.  Mine's at: [https://gist.github.com/1791270](https://gist.github.com/1791270).

---

