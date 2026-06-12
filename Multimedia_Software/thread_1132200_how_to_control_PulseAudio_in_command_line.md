---
title: "how to control PulseAudio in command line?"
date: 2009-04-21
forum: Multimedia Software
---

### Post by natrixnatrix89 on 2009-04-21
Hi. If I want to change the default sink of pulseaudio, I have to run padevchooser, then click on "other" in the "default sink" and enter the name of the sink I want to use.
Is there a way to do this from command line? So it could be included in a script or sth..
Maybe someone can suggest me where to look for pulse audio commands?

---

### Post by markbuntu on 2009-04-21
You can do that in pavucontrol.

pacmd 

is the pulseaudio command. Try

pacmd help 

for a list of options

---

### Post by natrixnatrix89 on 2009-04-21
How do you exit pacmd?

---

### Post by natrixnatrix89 on 2009-04-22
pacmd really works, but i'd really like to know, how to use pacmd in a script, because
```
#!/bin/bash
pacmd set-default-sink alsa_output.bluetooth
``` or ```
#!/bin/bash
pacmd set-default-sink
alsa_output.bluetooth
``` won't work.
It would just open pacmd. Could anyone please tell me, what could be the syntax for bash script to run pacmd and then run a command in IT?

---

### Post by markbuntu on 2009-04-22
If you want to load modules into a running daemon from a script you can use 

pactl

I have used it in scripts to load modules so I know it works for that.

I am not sure if pactl can set defaults or even if setting default will do what you are expecting it to. Default will not redirect all your applications to your bluetooth headset for example if they have been opened on another device before.

You could try commenting out the load-module module-volume-restore line in /etc/pulse/default.pa. That is the module that remembers where each application was last playing and restores it to that but then you will loose that function entirely.

More on pactl here

[http://linux.die.net/man/1/pactl](http://linux.die.net/man/1/pactl)

[http://pulseaudio.org/wiki/Modules](http://pulseaudio.org/wiki/Modules)

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

---

### Post by natrixnatrix89 on 2009-04-23
pacmd set-default-sink worked perfectly fine in command line.
What I want is to put it in a script.
Is the conclusion that I can't use pacmd in a script?

---

### Post by markbuntu on 2009-04-23
You probably can somehow but I do not know how, not being a big script fan.

---

### Post by RgnKjnVA on 2009-05-20
> **natrixnatrix89 said:**
> pacmd set-default-sink worked perfectly fine in command line.
What I want is to put it in a script.
Is the conclusion that I can't use pacmd in a script?

I found your thread because I was planning to do the same thing. Would be nice only have two steps to get BT rolling. However I notice that the man page for pacmd says it accepts no command line options which I believe is biting us in the butt. That would explain why the command isn't mentioned in the ~1500 threads I had to read to find the two that finally got my bluetooth headset working. 

At the very least it would be nice if paman would remember recent sink names so you don't have to enter it each time. =o/

---

### Post by landgrvi on 2009-05-31
Hey,  I was struggling with this too, and thought I was going to have to use expect or something like that, but I found a not-too-complicated solution: pipe the command through pacmd.

For example --
```
echo "set-default-sink jack_out" |pacmd
```It doesn't cause pulseaudio to exit, and doesn't leave any pacmd processes lying around.

Hope this works for you!

---

### Post by RgnKjnVA on 2009-05-31
Thank you landgrvi! Works great and now I can get my BT headset working in only two clicks. It almost qualifies as 'just works' although it's taken a lot of work to get there. heh

For the record here is my 'enableHeadset' script

```

pactl load-module module-alsa-sink device=Headset; sleep 2
pactl load-module module-alsa-source device=Headset; sleep 2
echo "set-default-sink alsa_output.Headset" | pacmd
echo "set-default-source alsa_input.Headset" | pacmd

```

---

### Post by jjordan on 2009-07-30
This topic is a little cold but if you are still looking, check here:

[http://pulseaudio.org/wiki/CLI](http://pulseaudio.org/wiki/CLI)

Basically you are loading a different command interpreter in the first line of your script:
 
[B]#!/usr/bin/pulseaudio -nF
[/B]
That is going to route the lines in the script to pulseaudio instead of the BASH shell.

Haven't found any information on command line switches, the MAN page says "none."

-j

---

### Post by GNUbee40 on 2009-08-01
Hey guys!

The reason why > echo "yadayada command" | pacmd works is simply because the commands for pacmd need to be in quotation marks when run from script or command line.
> pacmd "yadayada command" should work as well.
Of course if your script only contains commands for pulseaudio, the previous post contains a more elegant solution.

For more information on how to get pulseaudio to load bluetooth sinks automatically (which does not always seem to work, but - heck - you might give it a try) try this link:
[http://wiki.bluez.org/wiki/HOWTO/AudioDevices#PulsenativeBluetoothsink]("http://wiki.bluez.org/wiki/HOWTO/AudioDevices#PulsenativeBluetoothsink")

Regards

---

### Post by rrob on 2010-01-12
Hey guy, you did miracle!!!
Im googling solution of this problem half day and you find it!!!
Pacmd have problem with command line parameters.
If you ask manual "man pacmd" he tell you that he didnt accept cmdline parameters but if you ask help "pacmd help", he show you accepted parameters but they didnt work. You find incredible souliton, many thanks .)

Btw if you want redirect audio stream, you could use this [http://pulseaudio.org/wiki/DefaultDevice](http://pulseaudio.org/wiki/DefaultDevice) ...set the fallback device, then stop PulseAudio, then erase the stream-restore database by deleting the file containing the string "stream-volumes" in its name in the ~/.pulse directory, and finally restarting PulseAudio ...

---

### Post by rrob on 2010-01-12
my solution, script for switching soundcards 
[http://blog.robinpecha.cz/command-line-cli-switch-for-switching-default-sound-card-in-ubuntu-pulse-audio/](http://blog.robinpecha.cz/command-line-cli-switch-for-switching-default-sound-card-in-ubuntu-pulse-audio/)

---

### Post by Yellow Pasque on 2010-01-12
```
gstreamer-properties
```

---

### Post by avl555 on 2012-11-11
This thread is very old, but for anyone that is still looking for a simple solution:
[http://stackoverflow.com/questions/10739390/how-to-programmatically-change-volume-in-ubuntu](http://stackoverflow.com/questions/10739390/how-to-programmatically-change-volume-in-ubuntu)

---

