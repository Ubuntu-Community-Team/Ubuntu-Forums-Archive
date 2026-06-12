---
title: "Headphones don't disable laptop speakers"
date: 2010-05-20
forum: Multimedia Software
---

### Post by RedRecidivist on 2010-05-20
Hi,

Thanks in advance for any help. My problem is simple, I have looked for an answer and have found other people with the same problem, but no working solution.

I have a Samsung P28 laptop. When I plug in headphones, the sound continues to come out of the speakers too. I would like it to flick from one to the other, as it does in Windows. I have tried adjusting the "Sound Preferences...", including trying various different "Connector" settings under "Output".

Thanks for any tips.

---

### Post by ipatfrmww on 2010-05-20
Ok, what you have to do is relatively simple.
This is a problem with the way ALSA (sound driver) talks to your audio card.
The configurations are different for different sound cards, and apparently the ALSA programmers haven't quite got the nack of auto detecting all types of hardware(especially laptops).

To fix it you need to tell ALSA what laptop model you are using.
I found this quite helpful [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
What you have to do is go into the terminal
then enter this:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```(note that you need root privileges to edit this config file)

Then go down to the very end of the file and add this:

```
Samsung model=laptop
M50 model=laptop
R65 model=laptop-eapd
```Note that none of those say model = P28, so if the above doesn't work perhaps try adding the following instead:
 ```
P28 model=laptop
```If you want to spend a bit of time working this out I suggest having a look around(this is a common problem)(I had this same problem on an HP Pavilion, in fact the sound didn't work at all in karmic before I did this)

-some good links to try are:[URL="http://%20http://ubuntuforums.org/showthread.php?t=820959"]
[/URL][_http://ubuntuforums.org/showthread.php?t=820959_]("http://ubuntuforums.org/showthread.php?t=820959")
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by ipatfrmww on 2010-05-20
Forgot to add the most important bit:
Log off, log back on.
-or you could just do this;
```
sudo alsa force-reload
```

Although for some reason I had to restart my computer when I did it in lucid(not in karmic)

- also now that I remember a piece of general advice: Never, EVER uninstall alsa-utils or alsa-base, this is a very very bad idea (your computer won't boot- I know this from experience)

---

### Post by RedRecidivist on 2010-05-20
Hey... thanks for taking the time to reply. I'll be back with this PC on Monday so I'll try it then.

---

### Post by ipatfrmww on 2010-05-21
I figured it would be worth passing it on to at least somebody, it was a real struggle for me to find a link to those lists of [configurations]("http://ubuntuforums.org/showthread.php?t=1043568"). Then by chance I saw it in somebody's signature(its in mine now too :razz:) -problem solved. It doesn't have nearly enough combinations of things to solve everybodys sound problems since it was last edited a while back, but it does at least give a starting place of where to look(and links to places that have been updated recently)
- the trick is just playing round with the settings in /etc/modprobe.d/alsa-base.conf (add different things to the end of the file)(which is annoying if you have to restart a couple of times to get it to refresh)

-you'll notice that most of the things it says to add are like model=<something>
I think that's cause ALSA isn't very good at finding out for itself what computer type you have. But once you tell it, it knows what to do by itself. Which seems odd. But that's what all this problem that people have been having is about. Very Odd.

In case your wondering, I had to add this to the end of MY file:
```
options snd-hda-intel model=dell-m4-3 enable_msi=1
options snd-hda-intel model=hp-dv5
```
for my HP Pavilion dv6, which is slightly different to the advise they give you in the big list for a dv6:
```
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
```
Note that you probably have to add "options snd-hda-intel" to the start of each line that I gave you(like in my one), I forgot that lol.
Also note that it didn't matter that I said model=hp-dv5, cause all it really wants to know is that it is an HP.
So in you case all it really wants to know is that it is a Samsung, so any valid model that it already knows how to deal with will work.

---

### Post by RedRecidivist on 2010-05-23
None of those changes made any difference unfortunately.

I have now discovered though that if I change **Sound Preferences/Output/Connector** to one of the **Analog Mono Output** options, the sound comes from only the headphones (but still doesn't switch properly and is presumably not stereo...)

---

### Post by ipatfrmww on 2010-05-28
have a look around, see if you can find an active thread where people are being helped. Look for ones relating to /etc/modprobe.d/alsa-base.conf and sound problems. Chances are that somebody who knows the right sequence will see your post that way.
Hope I was of help.

---

### Post by RedRecidivist on 2010-05-28
Thanks, I'll try that - and yes, I really appreciate the effort! :)

---

### Post by lidex on 2010-05-30
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by RedRecidivist on 2010-05-30
Hi Lidex, and thanks for your help.

Here is the output you wanted. It's a **Samsung P28** laptop (old but trustworthy!)

```
chris@Flipper:~$ uname -a
Linux Flipper 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
chris@Flipper:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
chris@Flipper:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
chris@Flipper:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

---

### Post by lidex on 2010-05-31
> **RedRecidivist said:**
> Hi Lidex, and thanks for your help.

Here is the output you wanted. It's a **Samsung P28** laptop (old but trustworthy!)

```
chris@Flipper:~$ uname -a
Linux Flipper 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
chris@Flipper:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
chris@Flipper:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
chris@Flipper:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```
In alsamixer, what do the headphone and master controls affect?
Try upgrading alsa via the alsa-upgrade link in my sig.

---

### Post by RedRecidivist on 2010-05-31
For unrelated reasons, I've reinstalled with 10.04 Netbook Edition 32-bit... Of course, the sound problem still remains - here's the output Lidex asked for again in case anything has changed:

```
chris@Flipper:~$ uname -a
Linux Flipper 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
chris@Flipper:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chris@Flipper:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
chris@Flipper:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

---

### Post by RedRecidivist on 2010-05-31
Okay, Lidex, I've tried what you said:

[LIST]
[*]alsamixer's "Master" and "Headphones" faders control what they're supposed to! So I suppose that means that the problem is really only that the master volume is not automatically muted when the headphones are connected (as it is in Windows)
[*]Re: trying your upgrade script, I probably won't as alsamixer has basically given me a way to fix my problem! :) I don't have much time so I don't want to risk creating more problems.
[/LIST]

**You've basically helped me work around my problem, so thanks very much! :)**

---

### Post by lidex on 2010-05-31
You could also try backports.
Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

---

### Post by RedRecidivist on 2010-06-01
Hi,

After you got me to look at alsamixer, I dug around further and found a "Headphone Jack Sense [Off]" setting in it! I turned it on, and that's totally fixed my problem.

I won't be diagnosing why I had to change this setting any further as to be honest this works and I just don't have time but I *really* appreciate everyone's help - thanks!

---

### Post by lidex on 2010-06-01
Awesome. I think you can mark the thread solved now.

---

