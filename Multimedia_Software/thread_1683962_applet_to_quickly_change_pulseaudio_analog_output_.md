---
title: "applet to quickly change pulseaudio analog output connector"
date: 2011-02-08
forum: Multimedia Software
---

### Post by gadzoinks on 2011-02-08
hi, i was wondering if there is an applet (or even a way to do it from command-line) to quickly tell pulseaudio to switch from "Analog Output" output connector to "Analog Headphones" output connector?

the reason ("use-case") is:

i have a dell with a headphone audio output connector on the front of the box, and another normal audio output connector at the rear of the box (both 3.5mm stereo audio out).

i have the front connector connected to my headphones, and the rear connector connected to my monitor which has tiny speakers.  the monitor itself does not have a separate mute button for its volume, unfortunately.  (one has to go through all these menus just to find mute.   it's a pain).

i have skype going, and sometimes a skype call comes in, and i want to mute the monitor quickly (so the call is not broadcast all over the office for others to hear), but keep the headphones still going. 

if i switch pulseaudio from "Analog Output" (both jacks audible) to "Analog Headphones" (only front jack, i.e., headphones audible), using my Sound Preferences in Ubuntu, i find that this accomplishes what i want quite nicely: it turns off the rear audio (to the monitor), but it keeps my headphones going.  when i'm done with the call, i can return the output to "Analog Output" so i can continue to use the monitor to hear other notifications (such as incoming IM messages, etc.) without having to wear the headphones all the time (tho' the sound is still coming out of them and i *can* if i want to).

so i was wondering if there was a nice little applet, or even a way to send a command to pulseaudio via shell, for switching back and forth between these two connector choices, without having to keep the whole "Sound Preferences" window open on the desktop all day, taking up valuable real estate?

thanks in advance for any ideas..
--jeff

p.s. - i had even thought of reversing where the cables are plugged in.  that is, plugging the headphones into the rear, and the monitor into the front, and then just unplugging the monitor audio cable from the front whenever a call comes in -- like the old switchboard-style operators.  however, i have had the experience before of these little 3.5mm jacks wearing down and malfunctioning if they are used too much like that. so i want to avoid plugging/unplugging.

i'd also thought of finding a little external audio mute switch to connect inline in the audio cable to the monitor. i may still do that, as a last resort.  but i'd like to find a software solution first, if possible.

---

### Post by Ashrael on 2011-12-29
I TOTALLY AGREE! We need an easy way to switch output! I do not have any problems, I bought a Senheiser PC36 headset AND have pavucontrol installed :) But still I would like to be able to switch the ouput in a convenient manner! I somehow think that many people would be very happy with this kind of panel app.....

:popcorn:

---

