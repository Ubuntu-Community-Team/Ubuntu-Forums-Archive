---
title: "[SOLVED] No sound on Dell Studio 540"
date: 2008-11-03
forum: Multimedia Software
---

### Post by marcoil on 2008-11-03
I wasn't getting any sound on the integrated HDA Intel sound card in a new Ubuntu 8.10 Inteprid Ibex installation on a Dell Ubuntu Studio 540 (the desktop one).

The output of aplay -l is:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Looking at the codec gave:
```
$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC888
```

But alsamixer was giving "No mixer elems found" and /var/log/messages contained the infamous "Got POLLERR from ALSA", so I wasn't getting any sound.

After looking a lot on the web, I found the correct parameter to pass the snd-hda-intel module, so now I have a functioning sound system :)

If you have the same problem, edit /etc/modprobe.d/alsa-base and add the following line:
```
options snd-hda-intel probe_mask=1
```

Reboot or reload the module with
```
sudo modprobe -r snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=1

```

I hope this helps!

---

### Post by parallax68 on 2008-11-06
thanks marcoil it does work also for me (same machine)

---

### Post by Atze_B on 2008-11-26
This solved my audio problem too. Same machine.

Thanks a lot!!!

---

### Post by astralbodies on 2008-11-28
I tried this with the Dell Studio Slim Desktop PC and it didn't work.  I downloaded the new ALSA drivers (1.0.18a) and they compiled fine.  I selected various different types of models in the alsa-base configuration file with no success through the S/PDIF connector.  I was able to get audio out of the headphone jack and stereo speaker connection, however.

Any suggestions?  Are you using the digital audio through HDMI or S/PDIF at all?

Thanks -
Aaron

---

### Post by marcoil on 2008-11-29
> **astralbodies said:**
> I tried this with the Dell Studio Slim Desktop PC and it didn't work.

Any suggestions?  Are you using the digital audio through HDMI or S/PDIF at all?

I suppose the Slim model uses a different audio card, and I haven't tried S/PDIF output at all... I'm sorry I can't be of further help, but try searching the forums, maybe someone else with the same model has had better luck than you.

---

### Post by Sav on 2008-12-06
On my Dell Studio slim I didn't manage to have audio trough spdif.
Maybe this motherboard is still unsupported.

---

### Post by ouaibe@ouaibe.info on 2008-12-10
Same machine, same problem but it doesn't work at all ;o(

---

### Post by marcoil on 2008-12-10
> **ouaibe@ouaibe.info said:**
> Same machine, same problem but it doesn't work at all ;o(

Can you paste here the output of
```
aplay -l
```
on the command line?

---

### Post by ouaibe@ouaibe.info on 2008-12-11
it's OK and it's work.
I first did a mistake. Thanks a lot

Do you accept I translate in french your proc in my thread ?
[http://forum.ubuntu-fr.org/viewtopic.php?id=269104]("http://forum.ubuntu-fr.org/viewtopic.php?id=269104")

---

### Post by marcoil on 2008-12-11
> **ouaibe@ouaibe.info said:**
> Do you accept I translate in french your proc in my thread ?
[http://forum.ubuntu-fr.org/viewtopic.php?id=269104]("http://forum.ubuntu-fr.org/viewtopic.php?id=269104")

Sure, great idea!

---

### Post by ouaibe@ouaibe.info on 2008-12-11
Done ... and again ... merci beaucoup

---

### Post by astralbodies on 2008-12-22
In case anyone else is trying to get the Dell Studio Slim to function with ALSA, I've opened a bug with the project.

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4299](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4299)

---

### Post by Dale Sexton on 2008-12-24
Thanks, same problem same machine. Works great!

---

### Post by Yvon on 2008-12-25
I have a studio slim and it fixed the problem. 

Thanks a lot!

---

### Post by gacostac on 2008-12-31
Hi there, sorry to bother you with this. Today is my first day with kubuntu and got the same problem with the same computer.

Im figuring out how to use linux, so I need a little more "step by step" instructions. I typed "aaplay -l" in the terminal and got this:

card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So I figure we have the same system. What do i do next? I dont know how to get to:  "edit /etc/modprobe.d/alsa-base" 

 and add the following line:
```
options snd-hda-intel probe_mask=1
```

Reboot or reload the module with
```
sudo modprobe -r snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=1

```


Sorry again, Im a new linux user.

---

### Post by gacostac on 2008-12-31
Guys, I got to the lasa-base document (finally figured out it was not a terminal command...) and added the line you suggested. But when i try to save it wont let me. For some reason I only have "read access"... 

Can you help me get through that?

---

### Post by gacostac on 2008-12-31
With help form the Absolute Beginner Talk guys, i was able to get my sound to work in no time, this solution really works! thanks a lot

---

### Post by Dale Sexton on 2009-01-01
Sorry I didn't help. I'm pretty much a noobi also.

---

### Post by Sav on 2009-01-04
Did some one try the spdif output?

---

### Post by OldBiker on 2009-01-10
Thanks again to marcoil (same machine)

But found the sound level too low so with the help from another thread on the forum was able to increase it.

Open up a terminal and at the command prompt type alsamixer -c 0
use the arrow keys to select Front and increase level.
To list other options type alsamixer --help

---

### Post by Sav on 2009-01-17
I found a solution to get spdif output working.
I removed alsa and pulse, installed OSS4 and all is working.
The downside is that not all the multimedia apps are compatible, but xine does the job.
For flash support: [http://www.4front-tech.com/forum/viewtopic.php?t=2960](http://www.4front-tech.com/forum/viewtopic.php?t=2960)

---

### Post by mattme on 2009-01-23
I have a Dell Studio Slim (sold elsewhere as dell studio 540 slim). I had no sound, but the fix above solved the problem.

Note, after I'd applied the fix, one of the volume in volume control was really low, ~1%, so I had changed this too.

---

### Post by umechanism on 2009-01-25
YES!!!!!!

After weeks of reading and researching I found this thread and your suggestion worked!  I install the code then followed these directions:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

and it works!!!!:popcorn::popcorn::popcorn:

---

### Post by Sav on 2009-02-15
> **umechanism said:**
> YES!!!!!!

After weeks of reading and researching I found this thread and your suggestion worked!  I install the code then followed these directions:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

and it works!!!!:popcorn::popcorn::popcorn:

Did you try the spdif output?

---

### Post by arrowind on 2009-02-17
I have the same error message. When tried the solution and rebooted machine,  the sound card still didnt work.  I am getting a different error message though.

output of 'aplay -l' :
aplay: device_list:215: no soundcards found...


can you please help me?

---

### Post by umechanism on 2009-02-17
Are you using PulseAudio?
Did you install the PulseAudio device manager?

---

### Post by alicefrog on 2009-02-18
Did this on my new Dell Studio 540, re-booted, played around with the volume settings in Volume Control and it now works like a charm !

Thanks for that guys

:KS

---

### Post by arrowind on 2009-02-20
> **umechanism said:**
> Are you using PulseAudio?
Did you install the PulseAudio device manager?
I have installed pulseaduio device manager.  ALSA sound mixer.  When I oepn any of them they hang.  Music players hang also (totem, rythmbox)

---

### Post by umechanism on 2009-02-21
When it "hangs" does it make any sound at all?  Does Rhythmbox allow you to play streaming musing from Last.fm?

What finally worked for me was to get Last.fm streaming a song.  I could not initially hear the song but then I opened the Pulseaudio Volume Manager, clicked on the Playback Devices tabs, then right-clicked on the default devices and selected "change audio stream" which allowed me to select my front speakers.

You'd think your speakers would be chosen automatically but, in my case, I had several other usb connected devices that could "play" sound.  For example, I had an external sound-card interface device for my ham radio equipment (amateur radio [http://www.hello-radio.org/](http://www.hello-radio.org/)) which PulseAudio thought was my default speakers.  Once I changed the audio stream to go through my speakers instead of this interface device - all worked great!

See if you can change the audio streams.

---

### Post by Sav on 2009-02-22
I did it! :popcorn:

To have a fully working audio sub system on the Dell studio mini (inspiron 540s), the latest alsa git driver must be installed.

I used the script located at this post: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
with the -snap option (read the post).
The script need the build-essential packages and the git packages, as well.
Now the spdif output works and there is no need to modify the modprobe.d/alsa-base file.
I'm running the latest jaunty alpha (2.6.28 kernel) 64bit version.
I hope this could help others.

---

### Post by sipi on 2009-05-02
Thks very much. problemo solved.

---

### Post by sictransitgloria on 2009-06-02
Hello all.

I used this post and got the sound up and running on my Dell Studio 540 about 2 weeks ago.  The only difference between what I did and the solution was where I saved the ```
options snd-hda-intel probe_mask=1
``` command was in the /etc/modprobe.d/alsa-base.conf.dpkg-new file instead of the alsa-base file (which does not exist on my machine.)  This fixed the sound, but I had to use the two commands ```
sudo modprobe -r snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=1
``` to get the sound to work after every time I turned on/restarted my computer.

So I got ambitious, and sought a way to make the computer execute these commands automatically.  I tried three ways - putting the commands in the /etc/modules file, in the /etc/rc.local file, and adding the two commands under System-->Preferences-->Startup Applications.  And this worked for a couple of reboots.  Then the sound would work before I logged in, but not after.

Now, the sound has stopped working all together, even if I erase any changes made to the files and just reset the sound module manually.  My question is thus: has anyone else had this fix suddenly stop working?  Am I doing something wrong?

I should note, too, that, from the beginning, after typing in the two commands the terminal always output ```
WARNING: /etc/modprobe.d/alsa-base.conf line 1: ignoring bad line starting with 'snd_hda_intel'
``` which I found odd because I couldn't find any line with snd_hda_intel with underscores (only hyphens.)

Sorry that this post is so long, but  I was trying to walk through all of my steps.  If there are any other details you need, please let me know.  I've kept track of all the changes I have made.

Cheers,

-Jonathan

---

### Post by Atze_B on 2009-07-11
> **marcoil said:**
> If you have the same problem, edit /etc/modprobe.d/alsa-base and add the following line:
```
options snd-hda-intel probe_mask=1
```


Since last Karmic update i had to repatch using /etc/modprobe.d/alsa-base.conf instead of /etc/modprobe.d/alsa-base. Applying the patch to .conf works also.

---

