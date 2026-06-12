---
title: "Another Bluetooth Headset Question/Problem"
date: 2009-05-27
forum: Multimedia Software
---

### Post by b18b on 2009-05-27
I have a Nokia BH-503 bluetooth setup and working in 9.04.  All works very well for listening to music.  However what I have to go through to make it work is just way too many steps.  

I have a ~/.asoundrc setup with the following:
```

pcm.btheadset {
type bluetooth
device "00:0D:3C:B1:6F:6A"
profile "auto"

```

Here is how I do it now:
1) Boot the computer (Asus eee 901).
2) Turn on the bluetooth headset.
3) Pair up the computer with the headset
4) Open up PulseAudio Manager and click the disconnect button on the "Server Information" tab.
5) Run this script
```

#!/bin/bash
pulseaudio -k; sleep 4; pulseaudio -vv;
sleep 5
pactl load-module module-alsa-sink device="btheadset"
sleep 5
pactl load-module module-alsa-source device="btheadset"

```
6) Wait a few moments and go back to the PulseAudio Manager and click connect button on the "Server Information" tab.  
7) In the PulseAudio Manager, click the "Devices" tab.  If btheadset is shown as active devices I continue.  If it does not show up, I repeat steps 4, 5, 6, and 7.
8) If btheadset shows up on the Devices tab, I single click on the "PulseAudio Applet" and click on Default Sink -> other and enter in "alsa_output.btheadset".

DONE!

Now I have full sound from Rhythmbox.  

Way too many steps just to listen to music with a bluetooth headset.  

If the machine comes out of a "suspend", I have to add one more step by restarting the "bluetooth services".

Now either I am missing something completely and going a long way around to get things to work.  Or this is just the way it is.  However, I am just glad to see it work.

Suggestions on making the process shorter or ??

Thanks.

---

### Post by markbuntu on 2009-05-27
If you have all this, bluetooth should work sort of OOB for you. It will be in Koala.

bluez 4.35 or later
pulseaudio 0.9.15 or later
alsa 1.0.19 or later
Kernel 2.6.29 or later
gnome bluetooth 2.27.4 or later

---

### Post by b18b on 2009-05-28
From what I can tell, I am running the latest available from the repos.  

bluez 4.35 or later  [COLOR="Red"](4.32 - only version in the repos)[/COLOR]
pulseaudio 0.9.15 or later [COLOR="Red"](0.9.14 - only version in the repos)[/COLOR]
alsa 1.0.19 or later [COLOR="Red"](1.0.18 - only version in the repos)[/COLOR]
Kernel 2.6.29 or later [COLOR="Red"](2.6.28-12-netbook-eeepc)[/COLOR]
gnome bluetooth 2.27.4 or later [COLOR="Red"](0.11.0 - ????)[/COLOR]

> **markbuntu said:**
> If you have all this, bluetooth should work sort of OOB for you. It will be in Koala.


Maybe I don't know what Koala is.  Off to search....

---

### Post by markbuntu on 2009-05-28
Koala is the next release. Late October.

---

### Post by b18b on 2009-06-01
So I guess I have to wait until late October to simplify my headset connectivity?  There certainly ought to be a way to write a script or something that will do it with one or 2 clicks.  

I just don't know enough about what is happening here to work it out.

---

### Post by RgnKjnVA on 2009-06-02
Not sure if this applies to Jaunty (probably not but it may with some tweaking)

[http://ubuntuforums.org/showthread.php?t=1132200](http://ubuntuforums.org/showthread.php?t=1132200)

Here's the Money Shot of the thread:

```
pactl load-module module-alsa-sink device=Headset; sleep 2
pactl load-module module-alsa-source device=Headset; sleep 2
echo "set-default-sink alsa_output.Headset" | pacmd
echo "set-default-source alsa_input.Headset" | pacmd
```

---

### Post by b18b on 2009-06-06
> **RgnKjnVA said:**
> Not sure if this applies to Jaunty (probably not but it may with some tweaking)

[http://ubuntuforums.org/showthread.php?t=1132200](http://ubuntuforums.org/showthread.php?t=1132200)

Here's the Money Shot of the thread:

```
pactl load-module module-alsa-sink device=Headset; sleep 2
pactl load-module module-alsa-source device=Headset; sleep 2
echo "set-default-sink alsa_output.Headset" | pacmd
echo "set-default-source alsa_input.Headset" | pacmd
```

Thanks for the reply and suggestion!

To the most part the code above is what I am using, with the exception of the 2 echo statements.

Yes, they do work ONLY if I run them from a terminal window.  If I put them in a script, they seem to be non-functional.  

For example if I run within a script call "btheadset.sh" (set as executable)
```
pactl load-module module-alsa-sink device=btheadset; sleep 2
pactl load-module module-alsa-source device=btheadset; sleep 2
echo "set-default-sink alsa_output.btheadset" | pacmd
echo "set-default-source alsa_input.btheadset" | pacmd
```
NO change is noted.

But if I open a terminal window and run 
```
pactl load-module module-alsa-sink device=bteadset
```
then
```
pactl load-module module-alsa-source device=btheadset
```

The bluetooth headset modules initializes fine.

Then in a separate script I can run
```
echo "set-default-sink alsa_output.btheadset" | pacmd
echo "set-default-source alsa_input.btheadset" | pacmd
```
and my btheadset becomes default - which is good.

I suppose one of the big problems here is why doesn't the script where pactl loads the modules work?  But does in an open terminal session?  Is this a permissions thing??

---

### Post by RgnKjnVA on 2009-06-06
You have the following at the top of that file?

```
#!/bin/bash

```

...or ksh or whatever shell you prefer?


Oops nevermind. I posted that before noticing you do in fact have it in your script which you posted previously. That's kind of odd that it doesn't run those commands but I'm at a loss to explain why.


BTW Is there no means to delete a post on these forums?

---

### Post by josh_moore on 2009-06-10
I'm glad I found this thread as I am having the exact same difficulties, though I did not have a script as handy as the owner of this thread.
I however am not having as much luck making it work on demand.
After realizing the problem and searching around I found this thread
 [FONT=&quot][http://forums.overclockers.com.au/showthread.php?t=780054](http://forums.overclockers.com.au/showthread.php?t=780054)[/FONT]
Which had much of the same steps.
Following this I was able to get all sound working thru the bluetooth headset, but on reboot it was all gone.

I am running ubuntu Netbook Remix on my Dell Mini 10v using the Dell BH200 bluetooth headset.

If anyone has suggestions on the simplest method of making this work after a reboot I would appreciate it.
I tried to create a bash script that the original poster used but I am not sure if it was running properly, after several minutes I seemed to be getting the same entry over and over again, seemingly to no end, saying
D: module-console-kit,c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT1, member=PropertyModified

Not sure why the computer power supply/battery is being references from running

#!/bin/bash
pulseaudio -k; sleep 4; pulseaudio -vv;
sleep 5
pactl load-module module-alsa-sink device="btheadset"
sleep 5
pactl load-module module-alsa-source device="btheadset"

But then I'm still new to Linux

---

