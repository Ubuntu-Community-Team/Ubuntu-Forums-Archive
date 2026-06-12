---
title: "Sound is off after every start-up"
date: 2009-06-27
forum: Multimedia Software
---

### Post by stenshorne on 2009-06-27
Hi, I`m new here, and gonna get right to the point.

Every time I start up I have to click on the speaker, and manually turn off the mute and drag the volume up to get sound. This gets quite irritating, knowing that it is a little crappy problem, and quite possibly a very simple sollution to it all.

Is there a way to fix this, so it becomes permanent, so you don`t have to do this every time on start-up?

I`ve got the 9.04, and this is my sound specs, if it is of any help: HDA-Intel - HDA NVidia.


Thanks in advance, from stenshorne

---

### Post by linuxmagick on 2009-06-27
Maybe run alsamixer from a prompt.  From there you should be able to use your up and down arrow keys to adjust the volume and the M key to mute/unmute (muted will show as MM and unmuted will show as 00).  Once you have it set correctly, exit alsamixer and run alsactl store.  Someone else may have a better idea.

---

### Post by stenshorne on 2009-06-27
Okay, thanks, but that did not seem to work tho .)

---

### Post by linuxmagick on 2009-06-27
Try this:  [http://ubuntuforums.org/showthread.php?t=764576]("http://ubuntuforums.org/showthread.php?t=764576")

It has an extra step that goes along with what I said before.  The link above is kind of an old thread, but it's worth a shot.

---

### Post by stenshorne on 2009-06-27
Okay, these where the tips:

So here are the steps:
1) open **alsamixer** and set the volumes you want;
2) as root, type **alsactl store**;
3) after booting up, type **alsactl restore**.

If you want to have **alsactl restore** started every time you boot up, you can always add it to your **/etc/rc.local** file (just put the command above the line that reads **exit 0**)
_

After step two and enter I got this:

~$ sudo alsactl store
[sudo] password for oc: 
E: core-util.c: Home directory /home/oc not ours.

---

### Post by linuxmagick on 2009-06-27
Try this:

sudo chmod 666 /var/lib/alsa/asound.state
alsactl store (without sudo)

Use sudo chmod 644 /var/lib/alsa/asound.state to set the permissions back to the defaults (at least what they are on my system).

Beyond that, I'm not sure.  I'm fairly new to using Pulseaudio myself.  Hopefully someone who knows a little more about it will see this thread.  Good luck and I hope you're able to get it sorted out.

---

### Post by stenshorne on 2009-06-27
Sorry, that was a no-go,

I typed: sudo chmod 666 /var/lib/alsa/asound.state

nothing happened

then: alsactl store

nothing happened

I also tried alsactl restore, after reboot, just for the hell of it, but no, nothing. 

Could it be a packagebug of some sort?


But anyways, thanks for your effort, mighty nice of you! Hope I can get this silly little problem off my hands soon.

---

### Post by dozch on 2009-06-27
I had exactly the same problems as you (same sound card even) and the suggestions above did fix it for me.

To get around the "Home directory not ours" problem:

* Set up the volumes in alsamixer:

```
alsamixer -Dhw
```

* Save the mixer settings in a temporary file .asound.state in your Home folder:

```
alsactl -f ./.asound.state store
```

* As root, backup the actual asound.state file and then open it in the editor:

```
sudo mv /var/lib/alsa/asound.state /var/lib/alsa/asound.state.bck
```
```
gksudo gedit /var/lib/alsa/asound.state
```

* In gedit, open your temporary file .asound.state as well and copy the contents in the (empty) asound.state file. Press Save. 

* Now open /etc/rc.local and add the line

```
alsactl restore
```

before the line "exit 0" (leave that in)

Hope this helps.

---

### Post by Nyhus on 2009-06-27
I have the exact same problem and i've also tried saving "alsactl store" in "rc.local", but it just dose not seem to work. The mute button didn't shine the first time i rebooted, but there still was no sound.

> * In gedit, open your temporary file .asound.state as well and copy the contents in the (empty) asound.state file. Press Save.When i open the .asound.state file it's empty, so there is nothing to copy. 

This is basicly everything i've done to this point:

```

alsamixer (in the mixer, i turned everything to max)
sudo alsactl store;
sudo alsactl restore (then the volum is turned up the way it's supposed to be)
sudo gedit /etc/rc.local (where i put alsactl restore above the exit 0 command)

```I dont understand what went wrong, cause the sound is still muted when i boot up xubuntu and as far as i can understand it should have worked. I alos got the "/home/*not ours" message, but fixed it by going "sudo su" on its ***.

More suggestions would be appreciated.

I'm new to xubuntu, so i have no idea if you need this info, but this is what my .asound.state file says:
> state.NVidia {
    control.1 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 IntMic
        comment.item.1 ExtMic
        iface MIXER
        name 'Capture Source'
        value IntMic
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 23'
        comment.dbmin 0
        comment.dbmax 3450
        iface MIXER
        name 'Int Mic Capture Volume'
        value.0 0
        value.1 0
    }
    control.3 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Int Mic Capture Switch'
        value.0 true
        value.1 true
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 23'
        comment.dbmin 0
        comment.dbmax 3450
        iface MIXER
        name 'Ext Mic Capture Volume'
        value.0 0
        value.1 0
    }
    control.5 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Ext Mic Capture Switch'
        value.0 true
        value.1 true
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 20'
        comment.dbmin -3000
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 20
        value.1 20
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'PCM Playback Switch'
        value.0 true
        value.1 true
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 20'
        comment.dbmin -3000
        comment.dbmax 0
        iface MIXER
        name 'Int Mic Playback Volume'
        value.0 20
        value.1 20
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Int Mic Playback Switch'
        value.0 false
        value.1 false
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 20'
        comment.dbmin -3000
        comment.dbmax 0
        iface MIXER
        name 'Ext Mic Playback Volume'
        value.0 20
        value.1 20
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Ext Mic Playback Switch'
        value.0 false
        value.1 false
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 43'
        comment.dbmin -6450
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 43
        value.1 43
    }
    control.13 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.14 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.15 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.16 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.17 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
    }
}

---

### Post by dozch on 2009-06-29
You need to copy the contents of your created .asound.state file (ie. the output you posted) into the file /var/lib/alsa/asound.state. It is expected that it is empty because you 'moved' (= renamed) the old one to asound.state.bck.

/var/lib/alsa/asound.state is where alsactl restores the settings from.

Apologies for the confusion.

---

### Post by Nyhus on 2009-06-29
The same stuff is in my /var/lib/alsa/asound.state

> state.NVidia {
    control.1 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 IntMic
        comment.item.1 ExtMic
        iface MIXER
        name 'Capture Source'
        value IntMic
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 23'
        comment.dbmin 0
        comment.dbmax 3450
        iface MIXER
        name 'Int Mic Capture Volume'
        value.0 0
        value.1 0
    }
    control.3 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Int Mic Capture Switch'
        value.0 true
        value.1 true
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 23'
        comment.dbmin 0
        comment.dbmax 3450
        iface MIXER
        name 'Ext Mic Capture Volume'
        value.0 0
        value.1 0
    }
    control.5 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Ext Mic Capture Switch'
        value.0 true
        value.1 true
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 20'
        comment.dbmin -3000
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 20
        value.1 20
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'PCM Playback Switch'
        value.0 true
        value.1 true
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 20'
        comment.dbmin -3000
        comment.dbmax 0
        iface MIXER
        name 'Int Mic Playback Volume'
        value.0 20
        value.1 20
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Int Mic Playback Switch'
        value.0 false
        value.1 false
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 20'
        comment.dbmin -3000
        comment.dbmax 0
        iface MIXER
        name 'Ext Mic Playback Volume'
        value.0 20
        value.1 20
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Ext Mic Playback Switch'
        value.0 false
        value.1 false
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 43'
        comment.dbmin -6450
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 43
        value.1 43
    }
    control.13 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.14 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.15 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.16 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.17 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
    }
}

Still no working.

---

### Post by dozch on 2009-06-30
Since you seem to suggest that your audio works when you run the commands from the command line, I am running out of ideas...

Are you sure you put 'alsactl **_re_**store' in your /etc/rc.local?

---

### Post by initialxy on 2009-07-15
Hi,
I have the exact same problem. I got mine "solved" using the proposed work around. Now, here is where you went wrong.

Don't put "alsactl restore" in /etc/rc.local
Instead, put it in Xfce4's startup apps. So click your menu -> Settings -> Session and Startup. Go to Application Autostart tag and click Add. Give it some random name, random description, and fill in "alsactl restore" in the Command field then click OK.

There, yours should be working. Restart your computer and see if your volume gets restored. If it doesn't work, make sure "alsactl restore" actually restores your volume to some level, otherwise execute "alsactl store" again (like what you did before) to store volume status. There was one time, when I saved my volume at mute, and thought it wasn't working.

**Here is my proposal for some improvements on the work around.**
Now your Xubuntu should restore your volume to a predefined level every time you boot up, but that's not cool enough for me. Why not save your volume status at shutdown, so that every time you boot up, it restores to where you left off.

1. Copy the following script and save it somewhere on your computer (say, home directory). Save it with the file name store-volume (or whatever, but let's stick with that one for now).
```

#!/bin/bash

if [[ "$1" = "stop" ]]; then
    alsactl store
fi

```
2. Execute the following commands.
```

sudo mv store-volume /etc/init.d/store-volume
sudo chmod 755 /etc/init.d/store-volume
sudo chown root /etc/init.d/store-volume
sudo update-rc.d store-volume defaults

```
Done!

**My observations of this bug.**
I actually investigated into this bug, but due to the fact that I'm quite busy with school right now (final exams coming up), I had to give up without much useful results. If you happened to be a developer looking around this forum, hopefully followings could be helpful.

1. Only happens when Xfce4 desktop environment is loaded, doesn't happen to Gnome.
2. Volume seems to be reset to mute AFTER startup scripts (such as /etc/rc.local) is loaded. That's why having "alsactl restore" in /etc/rc.local doesn't work. Xfce4's startup programs are loaded some time afterwards.
3. Volume DOESN'T reset to mute when Xserver is restarted (with alt-ctrl-backspace).

---

