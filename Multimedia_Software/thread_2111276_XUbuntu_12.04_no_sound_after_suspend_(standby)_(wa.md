---
title: "XUbuntu 12.04 no sound after suspend (standby) (wake up)"
date: 2013-02-01
forum: Multimedia Software
---

### Post by sberla54 on 2013-02-01
Hello everybody,
my problem is: if i put my Asus EEE netbook on suspension mode (standby), after it wakes up there is no sound. 
I mean, the audio players correctly play an mp3, everything seems ok, but there's no sound from speakers. 

In the volume and sound device manager i can see there isn't the usual progress bar shown when any software is using the sound card.
If i reboot, everything come back ok.

I've already googled a lot and i've found it's a common problem.

Those are the most relevant post i've found:
[http://ubuntuforums.org/showthread.php?t=1475616http://ubuntuforums.org/showthread.php?t=1475616](http://ubuntuforums.org/showthread.php?t=1475616http://ubuntuforums.org/showthread.php?t=1475616)
[https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20ALSA%20to%20work%20after%20suspend%20/%20hibernate](https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20ALSA%20to%20work%20after%20suspend%20/%20hibernate)

I my case none of the suggested solutions works.

They suggest to create this script:
```
case "$1" in
        hibernate|suspend)
                # Stopping is not required
                ;;
        thaw|resume)
                /sbin/alsa force-reload > /dev/null
        sleep 1
        /usr/sbin/alsactl restore 
                ;;
        *) exit $NA
                ;;
esac

```or even try this command:
```

sudo alsa force-reload

```but i've seen that it's useless for me. Those commands just don't do nothing....maybe because XUbuntu 12.04 use Pulseaudio and not ALSA?

I can temporary fix the problem doing a 

```

killall pulseaudio

```and then restarting che audio player, but it really sucks.
I'm using my netbook just to quickly wake it up and start playing music from my Subsonic home server (via Google Chrome). If i have to turn it on everytime or kill a bunch of stuff it really sucks.

I've tried a lot of commands, like

```

/etc/init.d/pulseaudio force-reload

``````

/etc/init.d/pulseaudio stop
/etc/init.d/pulseaudio start

```but they don't fix my problem.

If i could find the right command to type to restart the Pulseaudio (and ALSA?) server, i could put them in a script, like the old topics suggests..

Have you got any tips?

By the way, are there any other distro i could try? Maybe something minimal without Pulseaudio...i don't know, Puppy, Bodhi, CrunchLinux...
I imagine that Ubuntu will have the same problems of XUbuntu...

Thank you!

---

### Post by sberla54 on 2013-02-03
I think i've solved it.

The script reporter in this page works fine: [http://ubuntuforums.org/showthread.php?t=1475616&page=2](http://ubuntuforums.org/showthread.php?t=1475616&page=2)

```

cd /etc/pm/sleep.d
mv 50alsa 09alsa

``````
case "$1" in
        hibernate|suspend)
                # Stopping is not required
                ;;
        thaw|resume)
                /sbin/alsa force-reload > /dev/null
        sleep 1
        /usr/sbin/alsactl restore 
                ;;
        *) exit $NA
                ;;
esac
```I just forgot the first piece and i didn't rename the file.

**Anyway, the problem wasn't the audio but the bluetooth.**

**After the wake up from suspend, the bluetooth doesn't work**. Since the audio was sent to the bluetooth output, there was no sound.

If i don't use the bluetooth output but only the internal speaker, the audio never fails, even without the script.

So i found this script for the bluetooth: [http://ubuntuforums.org/showthread.php?t=1387211](http://ubuntuforums.org/showthread.php?t=1387211)

```
cd /etc/pm/sleep.d
sudo touch 10_bluetooth
``````
#!/bin/bash
#Code from http://ubuntuforums.org/showthread.php?t=1387211

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    rfkill block bluetooth
    ;;
    thaw|resume)
    rfkill unblock bluetooth
    ;;
    *)
    ;;
esac

exit
```It turns off the bluetooth before the standby and turns it on again after the wake up.
The audio starts on the internal speakers and after some seconds goes to the bluetooth output.

Now the only problem i've left is that if i reboot i have to reconnect the bluetooth device. It is already connected-paired but it is not connected in "audio sink", and i have to do it manually every time.
Any advices about this?

Thank you.

---

