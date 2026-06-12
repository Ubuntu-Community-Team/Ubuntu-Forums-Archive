---
title: "No Surround Sound"
date: 2008-05-22
forum: Multimedia Software
---

### Post by spotteddog on 2008-05-22
Finally got my X-Fi working with OSS 4. :)
But, I only have the front speakers working. 
How do I get my surround sound (7.1) working? All the posts I have read have to do with ALSA rather than OSS.

Thanks

---

### Post by garyedwardjohnston on 2008-05-22
PulseAudio and 5.1 surround sound on Hardy Heron

The new Ubuntu 8.04 look very good and has many improvements over the older releases. I will not discuss about them now. I’ll just stick on the new default sound server, PulseAudio that offers sophisticated mixing capabilities and network transparency.
The purpose of this post is to help other Ubuntu users to enable 5.1 surround sound on their computers, using PulseAudio (you must have a 5.1 capable sound card).
I have a Creative Labs SB Audigy sound card but I tested this solution on a Creative Labs SB Live!. The results were the same in both cases.
The solution is very simple. Run this in your terminal:

    sudo joe /etc/pulse/daemon.conf 

Uncomment the line containing:

    default-sample-channels = 2 

and replace ‘2&#8242; with ‘6&#8242;.
(if you have a 7.1 card, replace ‘2&#8242; with ‘8&#8242;)
Restart the window manager and enjoy the new sound!

---

### Post by Yellow Pasque on 2008-05-22
Sorry spotteddog, but the OSS4 Creative X-fi drivers are currently 2.1 only.

---

### Post by spotteddog on 2008-05-22
Bummer! At least I have 2.1! That's better than nothing. 
I'll wait for the surround sound, whenever that happens.

Thanks.

---

### Post by JohnsShadow on 2009-11-29
> **garyedwardjohnston said:**
> PulseAudio and 5.1 surround sound on Hardy Heron

The new Ubuntu 8.04 look very good and has many improvements over the older releases. I will not discuss about them now. I&#8217;ll just stick on the new default sound server, PulseAudio that offers sophisticated mixing capabilities and network transparency.
The purpose of this post is to help other Ubuntu users to enable 5.1 surround sound on their computers, using PulseAudio (you must have a 5.1 capable sound card).
I have a Creative Labs SB Audigy sound card but I tested this solution on a Creative Labs SB Live!. The results were the same in both cases.
The solution is very simple. Run this in your terminal:

    sudo joe /etc/pulse/daemon.conf 

Uncomment the line containing:

    default-sample-channels = 2 

and replace &#8216;2&#8242; with &#8216;6&#8242;.
(if you have a 7.1 card, replace &#8216;2&#8242; with &#8216;8&#8242;)
Restart the window manager and enjoy the new sound!

i would like to correct you the code is 

```
sudo gedit /ect/pulse/daemon.conf
```

then change the default-sample-channels = 2 to 6(for 5.1) or 8 (for 7.1)
im testing this as we speak
rebooting to see if it works

Edit: DIDNT WORK, i also changed the system settings for my sound card and the application sould settings missing anything?

help please :)

---

