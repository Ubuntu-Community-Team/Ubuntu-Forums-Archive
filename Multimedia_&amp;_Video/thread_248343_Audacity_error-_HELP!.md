---
title: "Audacity error- HELP!"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by pak33m on 2006-08-31
Everytime I start Audacity I get the message:

Error Initalizing Audio

There is an error initalizing the audio i/o layer.
You will not be able to play or record audio.

Error: Host error.

I'm going to need Audacity running without errors in orde rto record a live DJ event tomorrow - HELP!

---

### Post by sebastfr on 2006-09-01
close any other programs using the sound card (xmms etc) and start audacity again.

Seb

---

### Post by vladozan on 2006-09-02
I have the same problem, but the solution offered here did not work. I tried also following wiki and run audacity as root, but with the same result

---

### Post by sebastfr on 2006-09-02
ha yeah I remember now... can you try to kill the 'esd' process before starting audacity? that was the problem for me (besides having also this problem when xmms was running)

~> sudo killall esd

(and make sure esd is not running anymore: ps aux | grep esd)

then start audacity as normal

Seb

---

### Post by freddy metz on 2006-09-17
i have the same problem and i still get the i/o error after trying sebas' solution :(
i get 
```

29583  0.0  0.1   2880   792 pts/0    R+   21:09   0:00 grep esd

``` when i enter "ps aux | grep esd" into the terminal. What does it mean?

---

### Post by Kingstrum on 2006-09-18
> **freddy metz said:**
> i have the same problem and i still get the i/o error after trying sebas' solution :(
i get 
```

29583  0.0  0.1   2880   792 pts/0    R+   21:09   0:00 grep esd

``` when i enter "ps aux | grep esd" into the terminal. What does it mean?

Ok, this is my first forum post, so please bare with me...

First, I'm having the same issue having just downloaded Audacity 1.2.4b-2ubuntu2 on a 2.6.15-26 kernel using an Intel ICH6 integrated sound card in my HP laptop. I too used the "sudo killall esd" to remove ESD (confirmed with "ps aux|grep esd", but I really should've looked first to see how it was attached).

No joy (as a normal user or with sudo).

In going over my full process list ("ps axf" to show and organize things is my preference) I don't see anything else that would be taking up sound resources. Also, when looking at the Prefs for Audacity after it loads there is nothing in the selections for playback or recording devices, nor anyway to add anything. That sort of hints to me that there may be an issue with the package itself and how it was compiled.

Second, the command "ps aux|grep esd" brings up a view of running processes (similar to Ctrl-Alt-Del in Windows), but filters the results with grep to only show results (if any) involving ESD (the Enlightenment Sound Daemon).

Now I am a bit confused as in years past I've never had an issue with such things when running ALSA (which I have set in "System -> Prefs -> Multimedia system selector"). I know some of it can/is based on the hardware, but it was never anything to run multiple sound apps (simultaneously even!) without conflict. Nowadays I don't need 25+ instances of XMMS running (thought it'd be nice, if just as a party trick), but being able to run a couple of apps  without conflict is always a Good Thing.

Kingstrum

---

### Post by Kingstrum on 2006-09-18
Further research has not yet yeilded a solution, but I did find some interesting bits:

[http://audacityteam.org/wiki/index.php?title=Linux_Issues]("http://audacityteam.org/wiki/index.php?title=Linux_Issues")

Now I tried everything listed here as a possible fix  without success. On a whim, and because I already have *build-essentials* installed, I'm gonna try to set it up from source and apply the bit about "PortAudio v19 instead of v18" (farther down the page in the disccusion of **OSS vs. ALSA**).

Report to follow.

Kingstrum

---

### Post by freddy metz on 2006-09-19
okay it finally works.. i enabled disabled esd for the millionth time and it just worked then. My problem now is that my mic wont work. It doesnt need any drivers or software but linux wont record any sound. Is ubuntu not detecting the mic or is it detected but doesnt record? How do i find out?

---

### Post by Kingstrum on 2006-09-19
Very much weirdness...

Following your tip, I had turned ESD off at "System -> Sound" and had rebooted a couple times in the last 24 hours. About 8 hours ago I saw your post and reinstalled Audacity on a whim.

*POOF!* Now suddenly it works without complaint -- for now.

As to your mic issue: a lot depends on your particular sound card, but I highly recommend looking at the ALSA site for specifics on your hardware and then try "sudo /usr/bin/alsamixer" and make sure that it isn't muted by default. If it is, you just press "m" to unmute it, ESC to exit, then I'd run "sudo /sbin/alsactl store" just to make sure the settings get saved (they are by default when you shutdown, but you can never be too sure).

See if that solves the problem and thanks for the heads up.

Kingstrum

---

### Post by sebastfr on 2006-09-20
> **freddy metz said:**
> okay it finally works.. i enabled disabled esd for the millionth time and it just worked then. My problem now is that my mic wont work. It doesnt need any drivers or software but linux wont record any sound. Is ubuntu not detecting the mic or is it detected but doesnt record? How do i find out?

Did you check on the Volume Control panel that the capture device (mic/line-in) is enabled?

Also... considered using jack+rosegarden? ;)

Seb

---

### Post by dolphinsonar on 2006-09-21
Kingstrum, that link now contains the information to fix the error in question:

If you use Audacity with Ubuntu 6.06 LTS "Dapper" (i.e. with the GNOME desktop) and you are greeted with this error message, try disabling the eSound (ESD) server in the Sound Preference Panel. Navigate to "System" > "Preferences" > "Sound". The Sound Preferences panel opens. Click on the "Sounds" tab. See if the box next to "Enable software sound mixing (ESD)" is checked. Uncheck it and click on the "Close" button. Audacity should now work.

Thanks, audacity has stopping giving that error.

---

### Post by Kingstrum on 2006-09-23
> **dolphinsonar said:**
> Kingstrum, that link now contains the information to fix the error in question:

If you use Audacity with Ubuntu 6.06 LTS "Dapper" (i.e. with the GNOME desktop) and you are greeted with this error message, try disabling the eSound (ESD) server in the Sound Preference Panel. Navigate to "System" > "Preferences" > "Sound". The Sound Preferences panel opens. Click on the "Sounds" tab. See if the box next to "Enable software sound mixing (ESD)" is checked. Uncheck it and click on the "Close" button. Audacity should now work.

Thanks, audacity has stopping giving that error.
Yep, it was there when I looked at it originally, however, like the Original Poster, turning it off didn't change anything. I *still* got the same error and had the same issues. Even after several reboots.

I uninstalled Audacity in frustration and left it for a day or two. Then read about his sudden success and decided to retry the exact same steps. Suddenly it **Just Worked**.

Haven't had a chance to play with it as much as I'd like, but it seems ok now.

Still unclear why ESD is even involved...the audio side of things is murky to me, but I thought ALSA handled all this stuff (the subsystem with some sort of internal daemon to do the grunt work)? I know GNOME doesn't have its own sound subsystem and its probably a bigger undertaking than just reusing bits.

Kingstrum

---

