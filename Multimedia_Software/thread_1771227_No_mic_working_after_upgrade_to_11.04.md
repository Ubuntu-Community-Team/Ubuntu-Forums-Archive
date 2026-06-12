---
title: "No mic working after upgrade to 11.04"
date: 2011-05-30
forum: Multimedia Software
---

### Post by Emanuele_Z on 2011-05-30
Hi all,

apparently I have to change alsamixer **every** time I log in (or restart) in order to have my mic working.
I tried to perform the following:
- Running alsamixer as sudo
- Executing alsactl store
- Amending the pulse audio default file */etc/pulse/default.pa*

But every time I logout/restart **always** have to manually fix things in alsamixer.
This is the first time it happens.

What am I doing wrong?
Should I reinstall 11.04 instead of upgrading it?

After 5 years of Ubuntu only on all my PCs I'm considering buying a Win7 license and remove Ubuntu for good. 11.04 is deluding me from every point of view.

Cheers,

---

### Post by Emanuele_Z on 2011-05-30
Adding more info.
After I amend the mic settings with 'alsamixer' I get the following entry when I execute amixer:
```

Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 20 [65%] [-4.50dB] [on]

```

But then when I restart or logout/login, this entry becomes:
```

Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 0 [0%] [-34.50dB] [off]

```

And if I run diff of the file
*/var/lib/alsa/asound.state*
with a local saved version copied after I save settings with 'alsamixer' I get **no differences**.
What other files is alsamixer/amixer modifying?

Cheers,

---

### Post by Emanuele_Z on 2011-05-30
Btw I got the following alsa version:

!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.24.2

is that correct?

Cheers,

---

### Post by ChrisKu on 2011-05-30
Have your tried the procedure provided by lidex:
 
>  
Originally Posted by **lidex** [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10278699#post10278699") 
*The command to save alsamixer settings is:*
*Code:*
*sudo alsactl store 0*
*If that doesn't work, open this file for editing:*
*Code:*
*gksudo gedit /etc/pulse/default.pa*
*Scroll down to this line:*
*Code:*
*load-module module-device-restore*
*Comment it out so it looks like this:*
*Code:*
*#load-module module-device-restore*
*Save. Close. Logout/in.*


---

### Post by Emanuele_Z on 2011-05-30
> **ChrisKu said:**
> Have your tried the procedure provided by lidex:
Yes. Unfortunately no luck at all.

Btw, if I execute:
```

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

```
Is this the correct version?

---

### Post by ChrisKu on 2011-05-30
> **Emanuele_Z said:**
> Yes. Unfortunately no luck at all.
 
Btw, if I execute:
```

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

```
Is this the correct version?
 
Although I am not an expert it looks ok to me. It is the same version as on my system.

---

### Post by ChrisKu on 2011-05-30
Just thinking a bit. My feeling is that it has nothing to do with the driver as you get your sound working. Have you got any other programs running which might "reset" your audio settings? I heard Skype is one of the candidates which might do things like that.

---

### Post by Yellow Pasque on 2011-05-30
> **Emanuele_Z said:**
> Btw I got the following alsa version:

!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.24.2

is that correct?

Cheers,
For a default Natty install, yes.

---

### Post by Emanuele_Z on 2011-05-30
I've fixed that applying the following command in *~/.profile*:
```

alsactl restore

```
(I've seen a similar solution here: [http://itbubbles.wordpress.com/2011/04/29/ubuntu-11-04-fight-for-microphone/](http://itbubbles.wordpress.com/2011/04/29/ubuntu-11-04-fight-for-microphone/) )

Apparently in Ubuntu 11.04 or PulseAudio or alsamixer are bugged and don't save user settings.
With *alsactl restore* basically you really the latest settings (usually saved in the default file here: */var/lib/alsa/asound.state*.

Personally I consider this to be more a *hack* than a solution... Anyway now it's working, but I would expect the latest of the distribution which prides itself to be *human friendly* **not** to ask users to mess around with *~/.profile* file.

What do you think?

Cheers,
Ema

---

### Post by kai_kan on 2011-09-20
> **Emanuele_Z said:**
> I've fixed that applying the following command in *~/.profile*:
```

alsactl restore

```
(I've seen a similar solution here: [http://itbubbles.wordpress.com/2011/04/29/ubuntu-11-04-fight-for-microphone/](http://itbubbles.wordpress.com/2011/04/29/ubuntu-11-04-fight-for-microphone/) )

Apparently in Ubuntu 11.04 or PulseAudio or alsamixer are bugged and don't save user settings.
With *alsactl restore* basically you really the latest settings (usually saved in the default file here: */var/lib/alsa/asound.state*.

Personally I consider this to be more a *hack* than a solution... Anyway now it's working, but I would expect the latest of the distribution which prides itself to be *human friendly* **not** to ask users to mess around with *~/.profile* file.

What do you think?

Cheers,
Ema

The good news: Ema's solution worked delightfully for me...

Until now, when I just upgraded to the latest version of Skype (2.2.0.35). Now I'm back to square one, having to change my settings via alsamixer with each reboot. That's the bad news.

Strangely, though, the line we added is still in my .profile. Ideas??

---

### Post by lidex on 2011-09-21
Purge your pulseaudio settings and make sure skype preference to adjust audio is disabled.

For pulse:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by Emanuele_Z on 2011-09-21
> **lidex said:**
> Purge your pulseaudio settings and make sure skype preference to adjust audio is disabled.

For pulse:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*
Do you recommend this as a full fix or as a fix to then re-source the amended profile at each login?
Cheers,
Ema! :-)

---

### Post by lidex on 2011-09-22
It's a start. Old pulse settings can cause issues, so you want to clear them out.

---

