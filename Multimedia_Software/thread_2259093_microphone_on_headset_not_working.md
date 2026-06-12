---
title: "microphone on headset not working"
date: 2015-01-01
forum: Multimedia Software
---

### Post by jimbo10 on 2015-01-01
just tried out the mic' on Skype/linux......

every-thing else seems OK.......head-phones &c.....

but.....mic' not working......

went to "system settings"/sound ...... didn't seem to be any response when i tested the mic'

any hints/tips much appreciated, as always......


ta!

(OK....i tried editing the mic file in[COLOR=#000000]* /usr/share/pulseaudio/alsa-mixer/paths/analog-input-internal-mic.conf  *as per this 'thread*'.......[http://ubuntuforums.org/showthread.php?t=2230136](http://ubuntuforums.org/showthread.php?t=2230136)*[/COLOR]......[COLOR=#000000]but it didn't work using "gedit"......does that mean i have to use the Terminal window?.......[that particular file is "read only".....***can*** i even 'edit' it?* )*[/COLOR]

---

### Post by Bucky Ball on 2015-01-01
Do you have Pulseaudio Volume Control installed? If not, install that and tweak around in the 'Input' tab. You should see the level going up and down if the mic is working. 

Open PAVControl, open Skype and make a test call. You will see the Skype audio stream in the 'Playback' tab of PAVControl. Go to the Input tab and make sure you have the mic set to use the correct device.

Might take a few test calls to get things working, but hope that helps. Shouldn't be a reason (yet) to edit any files in a terminal. Probably not that involved. ;)

---

### Post by jimbo10 on 2015-01-01
> **Bucky Ball said:**
> Do you have Pulseaudio Volume Control installed? If not, install that and tweak around in the 'Input' tab. You should see the level going up and down if the mic is working. 

Open PAVControl, open Skype and make a test call. You will see the Skype audio stream in the 'Playback' tab of PAVControl. Go to the Input tab and make sure you have the mic set to use the correct device.

Might take a few test calls to get things working, but hope that helps. Shouldn't be a reason (yet) to edit any files in a terminal. Probably not that involved. ;)

thnx for that..... installed PAV......went to "input" tab.....but....uh!.....mic doesn't seem to be working still, eh?  :(
....mic' is *definitely* working OTW, though.....was using just recently......
(i tried both front and rear RCA audio jacks......i have two audio plugs in front of desk-top and two [plus vid'] in back)

i'll re-boot...see if that helps any, eh?

cheers!

---

### Post by Bucky Ball on 2015-01-01
Did you make a test call with Skype and check where everything was being sent? Try changing the device in the Input tab while you are in the Skype call.

---

### Post by jimbo10 on 2015-01-01
> **Bucky Ball said:**
> Did you make a test call with Skype and check where everything was being sent? Try changing the device in the Input tab while you are in the Skype call.

thnx....tried that.......yeh.......the head-phones showed up in the "PlayBack" tab a-OK......but.......nothing from the mic'.......  :(

(do i need to change some-thing in the "configuration" tab for the input device......? .....i'll have a fiddle with it, eh?......its currently 'set' @  : input device==VT8237A/VT8251 HDA controller; profile: analogue stereo output + digital stereo  [IEC958 input]  )

**OK....tried it....the only two options in the config' tab that work are the "analogue stereo output + digital stereo [IEC958 input] " and "analogue stereo duplex"......the other 'drop-down' options don't even 'register' in PlayBack......but......mic' still not working.......  :(

---

### Post by jimbo10 on 2015-01-02
OK.....just tried editing two(2) config files using "sudo gedit"...... internal mic and head-set mic.....as per that prvs post/'thread'

[COLOR=#000000][I]comment out all lines that start with "required-any";

did NOT work!.....nothing....zilch.....nada......no mic*' *[/I][/COLOR]:frown:

what "gives", eh?

don't tell me i'm gunna hafta go back to frickin' Windows.......

(i'v[COLOR=#ff0000]*** GOT***[/COLOR] to have Skype because we live in a remote, rural area and  can't afford to make regular 'phone calls to STD or mobile nmbrs )

fair dinkum!

this SUX!!

---

### Post by jimbo10 on 2015-01-02
OK.....finally!....i got the mongrel bastard working........[COLOR=#ff0000]***thank***[/COLOR] Christ!

ended up doin' a !Google! and got on to a Y-tb...
[https://www.youtube.com/watch?v=tULmqpe5Yos](https://www.youtube.com/watch?v=tULmqpe5Yos) ;

i cut 'n' pasted the line of code he said to.....

and....yeh.....she's a GO-er......

still one problem, though....the front mic' jack ain't working......so.....any 'tips' on this would be greatly appreciated.....'cos an old fart like me has to get down on his hands and bloody knees (and i got a bung knee) and plug in to the back of the desk-top tower on the floor......  :frown:

still.......i got the Skype goin' now......so......again....***.thank Christ.***...i don't hafta go back to bloody Windows!   :cool: :cool:

---

