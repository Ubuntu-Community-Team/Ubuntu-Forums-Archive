---
title: "DVDs don't work"
date: 2014-02-22
forum: Multimedia Software
---

### Post by Audiosurfer on 2014-02-22
Whenever I try and play a DVD on my laptop I get some sort of error and it fails to run. Not sure how to fix this but it's getting annoying since my laptop is my main method of watching DVDs that I have. Any help would be appreciated

---

### Post by oldos2er on 2014-02-22
What error? Do you have libdvdcss2 installed? ```
sudo apt-get install libdvdread4

sudo /usr/share/doc/libdvdread4/install-css.sh
``` will install it.

---

### Post by Audiosurfer on 2014-02-25
Ok, I did this, but now every time I try to start the DVD in VLC it immediately crashes. Not sure what the problem is.

---

### Post by oldos2er on 2014-02-25
Have you tried playing the DVD in a different computer or DVD player?

---

### Post by andrew.46 on 2014-02-26
> **Audiosurfer said:**
> Ok, I did this, but now every time I try to start the DVD in VLC it immediately crashes. Not sure what the problem is.

There is a chance that vlc has some incompatible settings in its config file. Unless you have some deeply cherished settings in place you can set back to default with the following:

```

cvlc --reset-config && cvlc --reset-plugins-cache

```

and then try to open dvd as before... A second choice would be to look at what video output device you have set in vlc's preferences and see if this is breaking your video / dvd playback.

---

### Post by tomaspo on 2014-02-27
I had the same problem with my laptop. DVDs would not play with any of the media players including VLC. This code above seems to have fixed the problem. Thank you.

---

### Post by andrew.46 on 2014-02-27
> **tomaspo said:**
> I had the same problem with my laptop. DVDs would not play with any of the media players including VLC. This code above seems to have fixed the problem. Thank you.

Good to hear :). It is a bit of a shotgun approach to a vlc problem but it can be helpful when vlc is dead in the water...

---

### Post by Audiosurfer on 2014-03-18
Ok, did this and was able to play a DVD when I tried it today, so thanks for the help :)

---

