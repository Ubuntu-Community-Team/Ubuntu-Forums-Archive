---
title: "PulseAudio callback audio device connection"
date: 2016-01-14
forum: Multimedia Software
---

### Post by sander8 on 2016-01-14
Hey everybody,

I have had some issues regarding my audio output. When I connect my monitor to my laptop, I want the audio to come through the HDMI port and when the monitor is disconnected, I want it to come through my built-in speakers. I also have a headphone that connect through bluetooth. What I want to do is set up a priority list of some sort, for example HDMI has priority 3, built-in has 2 and bluetooth has priority 1 (highest is first), so that when my headphone connects, it will select this as output. I know you can do this with setting the default sink with _**pacmd**_ but this does not work with HDMI because this port is always available so I constantly need to switch between HDMI and built-in. I found code [here]("http://ubuntuforums.org/showthread.php?t=1370383") to switch with a command (I adjusted it a bit, see below). But now I want to define a priority list to set which output to try first, but I only want this code to run when a new device is connected. I first thought of doing this via _**[FONT=arial]cron[/FONT]**_ but this would put a strain on my system I think (or am I wrong?). The second thing is that _**cron**_ can only be run every minute, which would be too slow if I connected a device through which I want output immediately. Ideally this would be done with a callback method from PulseAudio or is there another possibillity? I've searched alot but could not find anything useful on the priority list.

```
#!/bin/bash

declare -i sinks_count=`pacmd list-sinks | grep -c index:[[:space:]][[:digit:]]`
declare -i active_sink_index=`pacmd list-sinks | sed -n -e 's/\*[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`
declare -i major_sink_index=$sinks_count-1
declare -i next_sink_index=0

x=`pacmd list-sinks | sed -n -e 's/[\* ]*[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`

array=($x)

#Associative array, contains[i] = 1 if index i is in x.
declare -A contains
for constant in $x
do
    contains[$constant]=1
done

if [ $active_sink_index -ne $major_sink_index ] ; then
    next_sink_index=$active_sink_index+1
    
    while [[ ! ${contains[$next_sink_index]} ]] ; do
        if [[ $next_sink_index -gt ${array[${#array[@]}-1]} ]] ; then
            next_sink_index=0
            break
        else
            next_sink_index=$next_sink_index+1
        fi
    done    
fi

#change the default sink
pacmd "set-default-sink ${next_sink_index}"

#move all inputs to the new sink
for app in $(pacmd list-sink-inputs | sed -n -e 's/index:[[:space:]]\([[:digit:]]\)/\1/p');
do
    pacmd "move-sink-input $app $next_sink_index"
done

#display notification
declare -i ndx=0
pacmd list-sinks | sed -n -e 's/device.description[[:space:]]=[[:space:]]"\(.*\)"/\1/p' | while read line;
do
    if [ $next_sink_index -eq $ndx ] ; then
        notify-send -i notification-audio-volume-high "Sound output switched to" "$line"
        exit
    fi
    ndx+=1
done;
```

---

### Post by sander8 on 2016-01-16
Or can anyone point me to where in the source code I could adjust this?

Any help would be much appreciated.

---

