---
title: "Problem with 4870-Catalyst 9.2-Display Configuration"
date: 2009-03-13
forum: Multimedia Software
---

### Post by Ceza on 2009-03-13
Hello all,
   Wondering if anyone can help me. I have managed to install the latest 9.2 Catalyst driver successfully a few times. I tried it on a different installs to make sure it wasn't something wrong with my main install so I loaded up Kubuntu fresh and tried again but find the same problem.

I can't get any dual monitor setup to work. The CCC doesn't seem to know what to do and thus is greyed out. Anyone else have this issue and managed to fix it?
[IMG]http://home.comcast.net/~mrsir/CCCSnapshot.jpg[/IMG]

I am running a fresh install of Kubuntu 8.04 but I have done the updates it found after the install. I didn't update it to 8.10, I like 8.04 better. I have a ATI 4870 w/1 Gig memory. I'm running a AMD Phenom II 940 with an Asus M3A79 Deluxe motherboard. I have 8 Gigs of Ram and I'm running just a single hard drive. No other problems noticed but this driver ( if that is what it is) issue.

I would really like some help here. Thanks for any assistance and also keep in mind I'm new to Kubuntu and not real bright to begin with so keep the words small and I would love explanations of what you tell me to do so I might be able to help the next guy.

Regards,
Ceza

P.S. I tried to query my monitor and got this response "ceza@ceza-desktop:~$ aticonfig --query-monitor
Error: option --query-monitor is not supported when RandR 1.2 is enabled!".  I don't know if that will help anyone know what is going wrong with my setup. Thanks for helping!

---

### Post by ult_avatar on 2009-03-15
Hi, i seem to have exactly the same problem ! Until now i haven't figured out a solution yet...

---

### Post by ult_avatar on 2009-03-15
this seems to be a bug in the new ati driver.
I managed to disable xrandr via the xorg.conf by adding:

```
Section "Extensions"
        Option "RANDR" "Disable"
EndSection
```

And after i restarted X, xrandr stopped working:

```
xrandr
Xlib:  extension "RANDR" missing on display ":0.0".
RandR extension missing
```

but still, the ait-driver doesn't care

```
sudo aticonfig --query-monitor
Error: option --query-monitor is not supported when RandR 1.2 is enabled!
```

---

### Post by markbuntu on 2009-03-16
Are you trying to set up separate x sessions or a bigdesktop?

---

### Post by maloo on 2009-03-29
Im having the same problem with a 4870. I have tried both the dual-head setup and big-desktop, both return back to a cloned output after the X server is restarted.

I have tried setting up the big desktop by following this guide on both 8.04 and 9.04:
[http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)
and
[http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)
Under 8.04 i have used the drivers from the repos and both 9.2 and 9.3 from ati. Under 9.04 I could only get the drivers from the repos to work (as i understand they are a prerelease of the 9.4 ati drivers)

Anyway from reading other posts etc all I should have to do to enable big desktop is ensure no x server is running (not 100% sure if this has to happen) then run aticonfig --initial -f then aticonfig --dtop=horizontal.

Anyway Ive been fiddling with this for a few days now and I guess I just want to know if anyone has had any success.

---

### Post by GnarusLeo on 2009-04-20
BUMP! =) 

I have a 4870 with a 24" inch monitor and a 32" LCD HDTV. Cant get dual to work, and I want them to be two different resolutions. One at 1920x1200 (works independent) and the LCD at 720p. Same problem as OP, anyone care to help? Try using the 9.4 drivers, CCC from AMD:popcorn:

---

