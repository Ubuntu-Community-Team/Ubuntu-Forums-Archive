---
title: "Headphone jack not working"
date: 2011-06-24
forum: Multimedia Software
---

### Post by n3xsolo on 2011-06-24
Hello, I'm having a problem getting the headphone jack to work, I'm using Ubuntu 11.04 and had the same problem when I was using 10.10. When I plug in a USB headset it recognises that and it works but doesn't work for jack headphones. 
[http://www.alsa-project.org/db/?f=f1e393fb2595b4525730c1a8831cb8e2f5b78495](http://www.alsa-project.org/db/?f=f1e393fb2595b4525730c1a8831cb8e2f5b78495) 
^thats the link for the information thing.
Thanks for any help.

---

### Post by n3xsolo on 2011-06-25
bump

---

### Post by lidex on 2011-06-26
This is a relatively rare comp. on these forums and I know I recently saw a thread regarding same. But I cannot for the life of me remember what the fix was. Grrr. Anyway, try this:
```
echo "options snd-hda-intel model=ref" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by n3xsolo on 2011-06-26
I pasted that code into terminal, rebooted and now I've got no sound and the option to change the connector (the one under balance) has gone it sound preferences.

---

### Post by lidex on 2011-06-26
OK. To edit that:
```
gksu gedit /etc/modprobe.d/alsa-base .conf
```
Where you see the line with model=ref change the modelname to each of these in turn:
```

  ref		Reference board
  dell-m42	Dell (unknown)
  dell-m43	Dell Precision
  dell-m44	Dell Inspiron
  eapd		Keep EAPD on (e.g. Gateway T1616)
  auto		BIOS setup (default)
```
I'd go from the bottom up. Save each change then reload alsa to initialize:
```
sudo alsa force-reload
```

---

### Post by n3xsolo on 2011-06-26
I only get two:
options snd-hda-intel model=ref
options snd-hda-intel model=ref
which bit do I change?

---

### Post by lidex on 2011-06-26
I'd remove the last line completely and edit the one remaining.

---

### Post by n3xsolo on 2011-06-26
I don't get it:( can you post exactly what the code should look like afterwards? (sorry in advance for being a n00b)

---

### Post by lidex on 2011-06-26
```
options snd-hda-intel model=[COLOR="Red"]ref[/COLOR]
```
Use the model names from the left column.
```
options snd-hda-intel model=auto
```

---

### Post by n3xsolo on 2011-06-26
when I use the Dell Inspirion as a ref I get a bit of sound in the left ear and it's making me start to think that it could possibly be the actually jack that's broken. Only thing is when it's on the speaker connector and I plug headphones into the jack the sound goes off so I assume it's not broken.

---

### Post by lidex on 2011-06-27
> **n3xsolo said:**
> when I use the Dell Inspirion as a ref I get a bit of sound in the left ear and it's making me start to think that it could possibly be the actually jack that's broken. Only thing is when it's on the speaker connector and I plug headphones into the jack the sound goes off so I assume it's not broken.

If you get a response then try tweaking settings, preferences, etc, as new options/elements may be enabled.

---

