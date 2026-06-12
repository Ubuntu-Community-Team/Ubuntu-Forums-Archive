---
title: "Dolby Digital Not Working"
date: 2018-12-17
forum: Multimedia Software
---

### Post by mpmckinnon on 2018-12-17
Hi there I am running Kubuntu 18.10 and running wanting to run Dolby Digital as per [https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio). It shows up on the list to pick for 5.1 digital but when I pick it the sound goes away and will not work till I go back to Stereo. Any thoughts and or help would go along ways.

Thank You

---

### Post by slickymaster on 2018-12-17
*Thread moved to **Multimedia Software**.*

---

### Post by mpmckinnon on 2018-12-18
I tried updating to Kernel 4.20 RC7 to see if it would make any difference and nothing. I can only listen to it via Stereo still no Dolby working.

---

### Post by mpmckinnon on 2018-12-24
Not sure if this helps I updated today to Kernel 4.20 and has all updated for Kubuntu 18.10 and Pulse audio still does not want to take Dolby at this moment.

---

### Post by mpmckinnon on 2019-01-02
Have not heard anyone for some help out input with 2019 here I am hoping someone might be willing to help :-).

---

### Post by 0x656b694d on 2019-01-22
Hello,

What is your audio connection scheme? You do have a digital audio connection to your audio system via optical or coaxial cable, right?
Just an idea: check what alsamixer shows.

---

### Post by mpmckinnon on 2019-01-23
Hi there thank you for getting back to me :-). I have optical connected to my 7.1 home receiver. I can get Stereo but it will not output for Dolby Digital. Pulse Audio show Digital 5.1 is unplugged.

---

### Post by mpmckinnon on 2019-02-12
Hey there guys never got anymore feedback, upgraded to kernel 5.0 RC6 and still not able to enable Dolby over toslink. Any help would go along ways thank you.

---

### Post by 0x656b694d on 2019-04-20
Hi,

I've upgraded to 19.04 and pulse doesn't see my 5.1 digital output anymore :)

---

### Post by 0x656b694d on 2019-04-20
> **0x656b694d said:**
> Hi,

I've upgraded to 19.04 and pulse doesn't see my 5.1 digital output anymore :)

That's because in 19.04 alsa.conf.d is moved to /etc/alsa/conf.d/!

So I created another symbolic link in there:
```

$ ls -l /etc/alsa/conf.d/*a52*
lrwxrwxrwx 1 root root 36 &#1072;&#1087;&#1088; 20 14:27 /etc/alsa/conf.d/70-a52.conf -> /usr/share/alsa/alsa.conf.d/a52.conf

```

---

### Post by Autodave on 2019-04-22
To both of you: did it work in 18.04?  If so, I recommend going back to 18.04.  That is an LTS (long term service release). Understand that releases afte that should probably be considered "beta" releases for the next LTS release in 20.04.  A lot of times things just don't work in the "beta" releases because the developers are trying new things.  It is always best to only use the LTS releases.

---

