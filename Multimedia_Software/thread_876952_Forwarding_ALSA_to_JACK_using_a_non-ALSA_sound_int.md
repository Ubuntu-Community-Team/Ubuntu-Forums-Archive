---
title: "Forwarding ALSA to JACK using a non-ALSA sound interface"
date: 2008-08-01
forum: Multimedia Software
---

### Post by Drack on 2008-08-01
Hello!  I have recently bought an Echo Audiofire 4 firewire sound interface, and I've got the hardware working with linux through the ffado project.  As it's a firewire interface, no ALSA or OSS is involved at all.  The driver is ffado, and all sound must go through JACK as its sound server.  However, I use a lot of apps that don't have an option to use JACK, but output to ALSA or OSS.

The solution that would make everything work would be a way to forward ALSA and OSS to the JACK server.  The posts I've read here generally deal with JACK using ALSA as its backend.  I want a solution that, with no ALSA card installed, will just send ALSA sound information to the JACK sound server.  I've seen a post about oss2jack, and I'll try that after exhausting any ALSA options.

---

### Post by Drack on 2008-08-01
Poking around a bit for a solution, I found this [bug report](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/148510) concerning the removal (!) of the alsa-jack plugin on Gutsy.

Checked libasound2-plugins in hardy's APT description, says JACK and other plugins were removed to conserve space on the install media.  Outrageous!

So, installed libasound2-plugins and its required deps that aren't in hardy apt from debian lenny repos (which DOES have the JACK plugin), so I *should* have alsa-jack.

Found more information on this problem here: [http://ubuntuforums.org/showthread.php?t=554373](http://ubuntuforums.org/showthread.php?t=554373)

Following the instructions and after setting up /etc/asound.conf, I get this:```
$ aplay -D jackplug nomachinejob.wav 
aplay: main:546: audio open error: No such file or directory
```

---

### Post by markbuntu on 2008-08-01
I have figured out how to forward all oss and alsa to pulseaudio here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

And someone has figured out how to get pulseaudio to forward through jack here:


[http://ubuntuforums.org/showthread.php?t=875378](http://ubuntuforums.org/showthread.php?t=875378)

Maybe you can get this all put together for us.

---

### Post by Drack on 2008-08-02
Partial success!

Pulseaudio didn't work for me.  The jack-sink module was failing with a cryptic error that I tracked down to the (compiled from svn) version of JACK I was running - which I need to run to use the ffado drivers to get any sound at all, so pulseaudio won't work, probably until the next jack release.

What DID work, was instead of using a debian package for alsa-jack, I used the ubuntu libasound2-plugins (with no jack plugin), downloaded the same version's source code from [http://www.alsa-project.org/](http://www.alsa-project.org/) and compiled it.  It made the jack plugin, which I copied (the .so and .la) into my lib folder.  Now alsa-jack works after configuration in /etc/asound.conf

Great!  So what alsa apps work and don't work well with alsa-jack?  In theory, all of them should work, but in Computer Science, theory and practice are never the same.

-aplay:  Works perfectly

-totem-xine: Works Perfectly

-Audacious: Not an issue as it has a jack plugin, but its alsa plugin works perfectly.

-Flash in web browsers:  I'm using the nonfree flash plugin, and unfortunately it doesn't play nice with alsa-jack.  No sound, and looking in my jack connections, it's constantly creating and removing connections over and over :confused:

-Wine:  This is interesting because it has both alsa and jack plugins, and neither are working for me.  The jack plugin seems to create several new jack *input* devices and nothing to handle output.  Testing it gives "Audio test failed!"  The alsa plugin shows up in the list but the checkbox to use it isn't there. :confused:  There's an oss plugin too, but it looks like the ONLY place to download oss2jack from is currently down.  Looking into that and aoss.

---

### Post by markbuntu on 2008-08-02
If you have flash 9, it will do that. It does that with Pulse also and as far as I could ever figure out, would only play sound through PulseAudio.

Libflashsupport is supposed to help with that but I got flash10b which fixed that problem for me. I am now unable to find 10b anywhere since 10b2 came out with tons of bugs that weren't in 10b. I doubt that even this would work without pulse though.

Wine really needs, those other things are just to get you excited. alsa-oss should fix that problem for you. It is the alsa wrapper for oss apps.

There is a newer version of libasound2 in launchpad somewhere, probably the same one you got from alsa-project. The one in the repos has a lot of issues with jack, like no working plugin.

I just got UbuntuStudio installed on a spare drive last night with a zillion updates but this morning when I went to use it, the rt kernel would not boot from grub. So, I want to get that working and repair some multiboot issues with my 4 hard drives and 4 OSs before delving into jack issues. That, and getting my 4 sound devices all in order on at least 1 OS before messing around with them in Studio to get jack running the way I hope to.

I am thinking of giving jack exclusive control of one card but I would like to use a different one for headphone work. Once again, off into the woods, lol.

---

