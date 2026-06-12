---
title: "DVDs not playing"
date: 2008-11-08
forum: Multimedia Software
---

### Post by grayfox444 on 2008-11-08
I have both VLC and Totem movie player, but DVDs will not work in either. When I try to run it in VLC it tries to open it then quickly closes it, as if it were finished with the DVD.

other videos I have on my hard drive work fine in both however.

---

### Post by agentsmith23 on 2008-11-08
I had this same problem recently and this is how i fixed it. Now I am not at my home Ubuntu box box right now (I am at work on a windows PC) so I may not remember everything exactly. Go into either VLC or Totem's video options and look at what you have setup for video rendering. I can't remember what exactly I had to change it to but I think it was X11. If it wasn't X11 just keep changing it till it works, that is what is causing your problem right now.

Good luck!

---

### Post by stinger30au on 2008-11-08
i have had this.

cured it by installing every video codec i could lay my hands on

i added medibuntu to my repos

[http://www.medibuntu.org/](http://www.medibuntu.org/)

i downloaded

non-free-codecs
 
w32codecs

i also went to applications->add remove
clicked on show all and searched on codec and added every codec i could find

let it install and also added avidemux as well in the same area

restarted pc, and it has been fine ever since

---

### Post by gandaran on 2008-11-08
you need to install **libdvdcss2** from the medibuntu repos for drm protected DVD play 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by grayfox444 on 2008-11-08
> **gandaran said:**
> you need to install **libdvdcss2** from the medibuntu repos for drm protected DVD play 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

i installed this, and i opened a dvd and it played the dvd strangely. it was all static, the screen size would jump a lot. it was going insane.

---

### Post by grayfox444 on 2008-11-08
got it guys, thanks.

---

### Post by Huss on 2008-11-09
Thanks agentsmith, 

Changing the VLC video preferences to X11 worked for me. VLC -> Tools-> preferences-> video output -> change from default to X11.

Funny coincidence: Mr and Mrs. Smith was the test DVD ;)

---

### Post by ukblacknight on 2008-11-09
> **gandaran said:**
> you need to install **libdvdcss2** from the medibuntu repos for drm protected DVD play 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

This didn't work for me.

```
tom@BlacKnight:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
```

How come it's so damned hard to play a DVD??!!

---

### Post by ukblacknight on 2008-11-09
> **ukblacknight said:**
> This didn't work for me.

```
tom@BlacKnight:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
```

How come it's so damned hard to play a DVD??!!

Got it working now, had to install the debs for the libdvdcss2 instead.  This process really needs to be simplified, i.e. a dialog box pops up asking if you want to use the restricted codec to play the DVD.

---

