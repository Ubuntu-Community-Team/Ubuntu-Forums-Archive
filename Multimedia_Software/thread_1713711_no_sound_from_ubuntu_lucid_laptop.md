---
title: "no sound from ubuntu lucid laptop"
date: 2011-03-24
forum: Multimedia Software
---

### Post by Gingalone on 2011-03-24
I used to listen music and watch films with my with my laptop but, after an upgrade (to 10.04 lucid) it is impossible to hear any sounds.
The sound card is detected and it works since making the laptop boot from live CD (of ubuntu 10.10) I get sounds without problems.

I tried to reinstall alsa-base and alsa-utils with no results. 
Everything looks OK, but the sound! (It's not muted!)

To me it looks like a mysterious puzzle!
For days I tried to find out the catch!
Can somebody help?
Thanks in advance!

---

### Post by lidex on 2011-03-24
So upgrading to maverick is not an option?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Gingalone on 2011-03-28
quote (lidex wrote):
 So upgrading to maverick is not an option?

That's an old laptop, I thought to stop upgrading not to impair machine speed (which is still not high!)

How can I upload on the web your command output? (Sorry)

---

### Post by Gingalone on 2011-03-30
Code:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

from this command I got a lot of error messages and warnings

I post the beginning of the response:

Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2011-03-30 15:46:00--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: 27247 (27K) [text/plain]
Saving to: `alsa-info.sh'

100%[==========================================================>] 27,247      --.-K/s   in 0.002s  

2011-03-30 15:46:00 (11.7 MB/s) - `alsa-info.sh' saved [27247/27247]

WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
ALSA Information Script v 0.4.60
:confused:

---

### Post by lidex on 2011-03-31
Try removing that file:
```
sudo rm /etc/modprobe.conf
```
Now reboot and re-run the script.

---

### Post by Gingalone on 2011-04-01
OK, done, here the script response: 

[http://www.alsa-project.org/db/?f=509016383fe11141657a81ffebae9a56e8263d25](http://www.alsa-project.org/db/?f=509016383fe11141657a81ffebae9a56e8263d25)

hope you get the whole link...
thanks for help!

---

### Post by lidex on 2011-04-01
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Check your levels. Make sure your master and PCM are not muted and turned up.

---

### Post by Gingalone on 2011-04-07
Sorry lidex, I posted the response from another machine (not the one with sound problems!) Oops!

Here the "real" response:

[http://www.alsa-project.org/db/?f=5d022e854efeccd5c874f3b2354485dc60718cd5](http://www.alsa-project.org/db/?f=5d022e854efeccd5c874f3b2354485dc60718cd5)

Thanks for help and sorry again!

---

### Post by lidex on 2011-04-10
U R cracking me up. Anyway, try upgrading alsa via the link in my sig.

---

### Post by Gingalone on 2011-04-11
sorry for cracking up...

Alsa updated to v1.0.24.2 but still no sound.
All levels up in Alsamixer.

The response to alsa-info.sh after the alsa update posted in: 
[http://www.alsa-project.org/db/?f=0697923fce3be7a8b122a8eac8bf68d6591d52a3](http://www.alsa-project.org/db/?f=0697923fce3be7a8b122a8eac8bf68d6591d52a3)

---

### Post by Yellow Pasque on 2011-04-11
What happens when you try to play sound directly to device?
```
aplay -D hw:0,0 "path/to/some/sound/file"
```

---

### Post by lidex on 2011-04-11
I'm thinking this is something simple. Your alsa-info looks fine. What profile do you have selected in 'Sound Preferences'? Barely any threads related to this laptop involve audio issues. See post #11 here:
[http://ubuntuforums.org/showthread.php?t=1430060&page=2](http://ubuntuforums.org/showthread.php?t=1430060&page=2)

---

### Post by Gingalone on 2011-04-26
sorry for delay (been away 2 weeks)...

> **Temüjin said:**
> What happens when you try to play sound directly to device?
```
aplay -D hw:0,0 "path/to/some/sound/file"
```

No sound, I get:

```
aplay -D hw:0,0 "/home/gano/Music/testMusic.ogg"
Playing raw data '/home/gano/Music/testMusic.ogg' : Unsigned 8 bit, Rate 8000 Hz, Mono
aplay: set_params:1059: Sample format non available
Available formats:
- S16_LE
- S32_LE
```

Just the same response with mp3 encoding.
what about?

---

### Post by Gingalone on 2011-04-26
> **lidex said:**
> I'm thinking this is something simple. Your alsa-info looks fine. What profile do you have selected in 'Sound Preferences'? Barely any threads related to this laptop involve audio issues. See post #11 here:
[http://ubuntuforums.org/showthread.php?t=1430060&page=2](http://ubuntuforums.org/showthread.php?t=1430060&page=2)

I had a look there, but I can't find the "Headphone Jack Sense" option in Sound Preferences...

---

### Post by lidex on 2011-04-27
> **Gingalone said:**
> I had a look there, but I can't find the "Headphone Jack Sense" option in Sound Preferences...

Use gnome-alsamixer.
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by Gingalone on 2011-04-29
> **lidex said:**
> Use gnome-alsamixer.
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

installed gnome-alsamixer, found the Headphone Jack Sense switch but no difference if that is ticked or not: no sound!!!:confused:

---

### Post by Gingalone on 2011-05-05
'Extrema ratio' I updated my laptop to Natty, the machine is a bit slow now, but the sound is back!
Thanks anyway to Lidex and Temüjin for helping!

---

