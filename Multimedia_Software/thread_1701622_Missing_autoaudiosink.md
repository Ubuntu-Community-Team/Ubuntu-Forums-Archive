---
title: "Missing autoaudiosink"
date: 2011-03-06
forum: Multimedia Software
---

### Post by sideburns on 2011-03-06
My sister's using Ubuntu 10.0.4 (I'm her tech support.) and for the past several days has been unable to get sound to work on her desktop.  She first noticed it on youtube videos, but we've tried other things and all sound is gone.  She just let me know that the autoaudiosink element is missing.  Alas, that's all I have from her email, or I'd give more details.  What's the best way to get it back and maybe get her sound working again?

---

### Post by Yellow Pasque on 2011-03-06
The autoaudiosink is in the gstreamer0.10-plugins-good package. Sometimes, it doesn't work for some reason. You can usually get around this by manually specifying the sink (probably pulsesink) in gconf.

```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink pulsesink
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink pulsesink
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink pulsesink
```

---

### Post by Softa on 2011-03-06
We tried your suggestion, but it didn't work.  Reinstalling the package didn't do any good, either.  Checking with a terminal, rhythmbox (used for testing) was still sitting in the background, hung but responded to kill -9.

---

### Post by Yellow Pasque on 2011-03-08
Hmm. I'm not sure what else to look for other than more detailed terminal output. Personally, I would install gstreamer dbg packages and start playing with gst-launch to see if I could find a more specific error, but that can get involved.

Anyway.. here's a free bump.

---

### Post by sideburns on 2011-03-08
Does Ubuntu use pulseaudio like Fedora does?  If so, maybe that's what needs reinstalling.

---

### Post by Yellow Pasque on 2011-03-08
> Does Ubuntu use pulseaudio like Fedora does?
Ever since Ubuntu 8.04/Hardy, Ubuntu uses pulseaudio by default.
First, try removing pulse's config files and restarting it:
```
cd ~/
rm -rf .pulse*
pulseaudio -k
```

---

### Post by Softa on 2011-03-09
when I ran the second command I got this in response:

E: main.c: Failed to kill daemon: No such process

And, when I tried to play an mp3, no sound.  Sigh!

---

### Post by Yellow Pasque on 2011-03-09
So pulseaudio isn't running.. Did you remove it by chance?
What is the output when you try to start it in terminal?
```
pulseaudio --start -v
```

---

### Post by Softa on 2011-03-09
Same as before: the daemon failed to start.  However,

ps aux | grep pulseaudio

showed that it was running, along with a helper.I killed it, tried again and it reported that it was able to start, but failed to do anything.  We did, however, get a message that it couldn't find a plugin: Gstreamer autoaudiosink.  And, I might add, DVDs don't play any more, not even the video.  Don't know if it's related, but you never know.

---

### Post by Yellow Pasque on 2011-03-09
Hmm. Does gst-inspect see the sink?
```
sudo apt-get install gstreamer0.10-tools
gst-inspect-0.10 autoaudiosink
```

As a last resort, you may want to delete the gstreamer registry (rm .gstreamer-0.10/* ) and install the latest stable version of gstreamer from this PPA: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by Softa on 2011-03-09
The utility was already installed and it found autoaudiosink, just fine.

I took a look at that link, but it wasn't at all clear to me how to get the data about that repository added to the system.  I'm the tech support (posting from my sister's box) but I'm not at all familiar with such things in Ubuntu or any other Debian-based system.

---

### Post by sideburns on 2011-03-13
OK, I've looked at that link again when I'm more alert and found the instructions I'd missed.  I've now installed that repo, updated to get the latest package list and installed the latest and greatest gstreamer.  No change.  By the time I'd done the tests, my sister's computer was reporting a flit-load of updates, all from there so I let it do its job.  No effect.  I'm beginning to wonder if it's hardware and if a new sound card is indicated.  If so, it'll be a shame, because installing it will kill 102 days of uptime on that box.

---

### Post by Yellow Pasque on 2011-03-13
Run the alsa-info script. [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)
Post results.

---

### Post by Softa on 2011-03-14
OK, I've downloaded and run the script.  The first thing it did was update itself.  The second time, I had it upload the info on my sister's machine to here: [http://www.alsa-project.org/db/?f=e373bd433101e7af5edbca262457a5b309b41b29](http://www.alsa-project.org/db/?f=e373bd433101e7af5edbca262457a5b309b41b29) and I hope you can get more from it than I did.

---

### Post by Softa on 2011-03-23
Hi Everyone,
I've tried your suggestions, unfortunately to no avail.  I *do* have the video back up and running, but I still don't have audio.

I was wondering if it would be a good idea to swap-out my sound card?

---

### Post by Yellow Pasque on 2011-03-23
Try to upgrade ALSA first: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by Softa on 2011-03-23
I installed Pulseaudio Volume Control to make sure nothing's muted.  On the Output Devices tab,it only shows Dummy Output.  If I change from All Devices to Hardware Devices, it shows nothing.  Checking, /proc/asound/cards shows this:

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9df4000 irq 22

We may well need a new sound card, and that means blowing away 113 days of uptime.  *Sigh!*

---

