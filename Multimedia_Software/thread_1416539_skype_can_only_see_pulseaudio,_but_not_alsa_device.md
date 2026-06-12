---
title: "skype can only see pulseaudio, but not alsa devices"
date: 2010-02-26
forum: Multimedia Software
---

### Post by ireneshusband on 2010-02-26
i am having a problem with skype that i wasn't having before, and afaik skype hasn't been upgraded recently, so something else presumably has changed.

because of driver issues i have to use an external usb audio interface to do voip. this interface is not connected to the pulseaudio server. i am able to connect it to jackd and it works fine for both audio in and out. however it no longer shows up in the list of sound devices available to skype. this used not to be the case. i have tried stopping and restarting skype, as well as unplugging and reattaching the interface. the interface does not show up in pulseaudio manager in the lists of devices.

any idea this device isn't showing up in skype?

---

### Post by Timothy Taylor on 2010-02-26
I've just installed Skype and I find the same problem. Any ideas on how to make it work will be very welcome.

---

### Post by ireneshusband on 2010-02-26
I have managed to work around the problem, at least this once, using the following procedure. Most likely some of the following steps aren't necessary, so you may be able to simplify it somewhat:

[LIST=1]
[*]Turn PulseAudio autospawn off, normally: $ echo "autospawn = no" > ~/.pulse/client.conf
[*]Kill PulseAudio: $ killall pulseaudio
[*]Shut down and restart Skype
[*]Go to the Skype sound device options, where your devices should now be exposed; Choose something.
[*]Shut down Skype
[*]Turn PulseAudio autospawn back on: $ echo "autospawn = yes" > ~/.pulse/client.conf
[*]Relaunch PulseAudio: $ pulseaudio -D
[*]Launch Skype
[*]Edit and test Skype sound device preferences
[/LIST]

---

### Post by Timothy Taylor on 2010-02-27
That doesn't work for me.
I still just see "PulseAudio Server (local)" as the only available sound device in Skype.
:?:

---

### Post by malel on 2010-02-27
I had the same problem and took care of it by deleting/removing pulse audio
cheers

---

### Post by segisaurus on 2010-02-28
> **malel said:**
> I had the same problem and took care of it by deleting/removing pulse audio
cheers

Just wanted to say that removing pulse audio worked for me too.

> sudo apt-get purge pulseaudio

---

### Post by greybeard95a on 2010-03-20
Removing pulseaudio seems to solve a number of problems.  What I'm wondering, now that I've done it myself, is if I have created any.  I rely on properly functioning sound not just so Skype can have a ring device besides my USB headset, but so twinkle can find any audio devices at all.

---

### Post by laceration on 2010-07-26
Thanks Ireneshusband.  I just did a clean install of Lucid and you solved a problem for me.  I streamlined your steps though:

1. Turn PulseAudio autospawn off, normally: $ echo "autospawn = no" > ~/.pulse/client.conf
2. Kill PulseAudio: $ killall pulseaudio
3. Quit and restart Skype.  
4. Go to the Skype sound device options, where your devices should now be exposed; Choose something.(May not be necessary as Skype might remember what was previously selected)
5. Relaunch PulseAudio: $ pulseaudio -D

Problem is you need to do this after every reboot.  Has anyone figured out how to make this stick across reboots?  I tried doing sound w/o pulse but could not find a volume control for the panel that would work.

---

### Post by mdurham on 2010-08-13
> **laceration said:**
> Thanks Ireneshusband.  I just did a clean install of Lucid and you solved a problem for me.  I streamlined your steps though:

1. Turn PulseAudio autospawn off, normally: $ echo "autospawn = no" > ~/.pulse/client.conf
2. Kill PulseAudio: $ killall pulseaudio
3. Quit and restart Skype.  
4. Go to the Skype sound device options, where your devices should now be exposed; Choose something.(May not be necessary as Skype might remember what was previously selected)
5. Relaunch PulseAudio: $ pulseaudio -D

Problem is you need to do this after every reboot.  Has anyone figured out how to make this stick across reboots?  I tried doing sound w/o pulse but could not find a volume control for the panel that would work.
How about starting from a script that does all this before starting skype, would that work?
I can't believe it's so hard to use my usb phone with skype. I've seen so many people say they have removed Pulse from their system, I wonder why the devs continue with what appears to be a useless package.
Anyway, thanks for the idea.
Cheers, Mike

---

### Post by laceration on 2010-08-14
Mike,

Pulse is the sound server, while Alsa works w/ the hardware layer.  So Pulse supposedly gives you sound control per each app.  To me it doesn't seen to do that much but add complexity to the system.  But I think the blame here should be probably be with Skype.  From the Skype readme:
>   
* If you have a normal sound card, we recommend using the Default sound  device for now. Sound output to hw: specific or plughw: specific devices may not work for all sound cards, or may result in single-channel playback or loss of sound mixing support on your system.

I rarely reboot my computer. When I do, since I have autospawn off and pulse unchecked in Startup Applications, all I have to do is this at the cli:
```
$ pulseaudio -D
```

but I couldn't resist I wrote a startup script.
Save it as /usr/local/bin/startpulse
then do this
```
sudo chmod +x /usr/local/bin/startpulse
```
Add the script to your Startup Applications

here is the script:
```

#!/bin/bash
# Starts pulseaudio after testing to see if skype has already started
# pulse should be unchecked in Startup Applications
# pulse autospawn should be turned off. Do it like this:
# $ echo "autospawn = no" > ~/.pulse/client.conf
# see following link to see why this would be useful
# http://ubuntuforums.org/showthread.php?t=1416539
# # requires libnotify-bin for the notification
######################
test4skype(){
if [[ $i -lt 6 ]]
then
    if [[ $(pgrep skype | wc -l) -gt 0 ]]
    then
        pulseaudio -D
    else
        let i=($i+1)
        sleep 3
        test4skype
    fi
else
notify-send "Pulseaudio failed to start. Start by \"pulseaudio -D\" at the cli"
fi
}
i=0
test4skype
kill $$

```

---

### Post by mdurham on 2010-08-14
> **laceration said:**
> Mike,

Pulse is the sound server, while Alsa works w/ the hardware layer.  So Pulse supposedly gives you sound control per each app.  To me it doesn't seen to do that much but add complexity to the system.  But I think the blame here should be probably be with Skype.

Hi laceration, thanks for your post, I'll give your script a try later. From your text above "Pulse supposedly gives you sound control per each app", how is it supposed to do that? I don't see anything that enables this feature. And, I don't see how the problem is Skype's when all it's doing is sending to and receiving from Pulse. The problem for me is that I can set the usb mic as input to Pulse but there is no way (that I can see) to set the output of Pulse to the usb phone when using Skype.
Ready for the desktop? I think not!
Cheers, Mike

---

### Post by thomas.horner on 2011-07-26
there's an easier way to make skype (i'm using 2.2.0.35) not use pulseaudio - there's no need to uninstall or disable pulse:

create an executable file
/usr/bin/skype-wrapper
with the following content:
PULSE_SERVER=127.0.0.1 /usr/bin/skype &

don't forget to also change the desktop file so that the new script will be called when choosing skype from the start menu:
edit file /usr/share/applications/skype.desktop
and change
Exec=skype
to
Exec=skype-wrapper

explanation:
PULSE_SERVER is a way to tell skype to use a pulse instance on a machine other than the local.
invalid values (e.g. empty string) make skype interrupt the startup and quit - so we give the local adress which is valid but obviously pulse runs at user level so it's not reachable via network, even not on the local machine.
skype tries to use pulse but cannot reach/connect to it and falls back to alsa.
the result on ubuntu natty is that pulse continues to work unmodified and skype can be configured to use whatever you want to :)



:!: HOWEVER :!:
the real problem - at least in my case - wasn't skype. the strange distortion came from somewhere below and was noticeable also in some other programs.
the real solution for my case was _not_ to disable pulseaudio but to fix it: edit file /etc/pulse/default.pa
and change
load-module module-udev-detect
to
load-module module-udev-detect tsched=0

see [http://pulseaudio.org/wiki/BrokenSoundDrivers](http://pulseaudio.org/wiki/BrokenSoundDrivers)

---

### Post by mdurham on 2011-07-26
> **thomas.horner said:**
> there's an easier way to make skype (i'm using 2.2.0.35) not use pulseaudio - there's no need to uninstall or disable pulse:

create an executable file
/usr/bin/skype-wrapper
with the following content:
PULSE_SERVER=127.0.0.1 /usr/bin/skype &

don't forget to also change the desktop file so that the new script will be called when choosing skype from the start menu:
edit file /usr/share/applications/skype.desktop
and change
Exec=skype
to
Exec=skype-wrapper

explanation:
PULSE_SERVER is a way to tell skype to use a pulse instance on a machine other than the local.
invalid values (e.g. empty string) make skype interrupt the startup and quit - so we give the local adress which is valid but obviously pulse runs at user level so it's not reachable via network, even not on the local machine.
skype tries to use pulse but cannot reach/connect to it and falls back to alsa.
the result on ubuntu natty is that pulse continues to work unmodified and skype can be configured to use whatever you want to :)



:!: HOWEVER :!:
the real problem - at least in my case - wasn't skype. the strange distortion came from somewhere below and was noticeable also in some other programs.
the real solution for my case was _not_ to disable pulseaudio but to fix it: edit file /etc/pulse/default.pa
and change
load-module module-udev-detect
to
load-module module-udev-detect tsched=0

see [http://pulseaudio.org/wiki/BrokenSoundDrivers](http://pulseaudio.org/wiki/BrokenSoundDrivers)

Thank you very much Thomas, that makes it so much easier than messing around with the Pulse Audio Device Chooser which I have found unreliable, that is, it has on occasions been reset and removed skype from itself somehow.
Thanks again, Mike

---

### Post by gatewayasteroid on 2011-08-07
> **thomas.horner said:**
> there's an easier way to make skype (i'm using 2.2.0.35) not use pulseaudio - there's no need to uninstall or disable pulse:

create an executable file
/usr/bin/skype-wrapper
with the following content:
PULSE_SERVER=127.0.0.1 /usr/bin/skype &

don't forget to also change the desktop file so that the new script will be called when choosing skype from the start menu:
edit file /usr/share/applications/skype.desktop
and change
Exec=skype
to
Exec=skype-wrapper

explanation:
PULSE_SERVER is a way to tell skype to use a pulse instance on a machine other than the local.
invalid values (e.g. empty string) make skype interrupt the startup and quit - so we give the local adress which is valid but obviously pulse runs at user level so it's not reachable via network, even not on the local machine.
skype tries to use pulse but cannot reach/connect to it and falls back to alsa.
the result on ubuntu natty is that pulse continues to work unmodified and skype can be configured to use whatever you want to :)



:!: HOWEVER :!:
the real problem - at least in my case - wasn't skype. the strange distortion came from somewhere below and was noticeable also in some other programs.
the real solution for my case was _not_ to disable pulseaudio but to fix it: edit file /etc/pulse/default.pa
and change
load-module module-udev-detect
to
load-module module-udev-detect tsched=0

see [http://pulseaudio.org/wiki/BrokenSoundDrivers](http://pulseaudio.org/wiki/BrokenSoundDrivers)

The only solution I found so far to use my USB phone and skype under a system with pulseaudio (such as Natty) is to install "padevchooser" and play with the audio streams *WHILE THEY'RE PLAYING*. This way you can redirect (as I need) the voice to USB phone and the ring to the onboard audio.

I ended by building up my system from the Minimal CD. But I like your solution.

Thank you!

---

### Post by jminker on 2012-06-05
> **thomas.horner said:**
> there's an easier way to make skype (i'm using 2.2.0.35) not use pulseaudio - there's no need to uninstall or disable pulse:

create an executable file
/usr/bin/skype-wrapper
with the following content:
PULSE_SERVER=127.0.0.1 /usr/bin/skype &

don't forget to also change the desktop file so that the new script will be called when choosing skype from the start menu:
edit file /usr/share/applications/skype.desktop
and change
Exec=skype
to
Exec=skype-wrapper

explanation:
PULSE_SERVER is a way to tell skype to use a pulse instance on a machine other than the local.
invalid values (e.g. empty string) make skype interrupt the startup and quit - so we give the local adress which is valid but obviously pulse runs at user level so it's not reachable via network, even not on the local machine.
skype tries to use pulse but cannot reach/connect to it and falls back to alsa.
the result on ubuntu natty is that pulse continues to work unmodified and skype can be configured to use whatever you want to :)



:!: HOWEVER :!:
the real problem - at least in my case - wasn't skype. the strange distortion came from somewhere below and was noticeable also in some other programs.
the real solution for my case was _not_ to disable pulseaudio but to fix it: edit file /etc/pulse/default.pa
and change
load-module module-udev-detect
to
load-module module-udev-detect tsched=0

see [http://pulseaudio.org/wiki/BrokenSoundDrivers](http://pulseaudio.org/wiki/BrokenSoundDrivers)
Thanks for this! It worked for me after some recent updates to either Pulse or Skype totally messed up a perfect setup.

---

### Post by mdurham on 2012-06-05
Thanks from me too. It's certainly a lot better and more reliable than messing about with Pulse.
Cheers, Mike

---

