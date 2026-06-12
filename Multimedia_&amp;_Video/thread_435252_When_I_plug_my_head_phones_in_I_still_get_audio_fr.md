---
title: "When I plug my head phones in I still get audio from my speakers."
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by turingon on 2007-05-06
Hi,

I apologize if this is a bad question but when using windows, if I plugged in my ear phones, the speakers cut out and sound just came out the speakers.

In linux, when I plug in the ear phones, I get audio out both.  I tried going to the sound preferences but could not figure out an option to do this.  I tried to google but was unable to get an answer to my long query.

Is there something I need to set?  If so, where?

Thanks,

---

### Post by turingon on 2007-05-06
In case it matters, I have a Dell Inspiron 9400 w/ a Sigmatel STAC9200 sound card.....

---

### Post by zmatt on 2007-10-30
I have the same problem. I have a  compaq presario c557cl laptop with intel hda audio.

---

### Post by d_iane1954 on 2007-10-30
> **turingon said:**
> Hi,

I apologize if this is a bad question but when using windows, if I plugged in my ear phones, the speakers cut out and sound just came out the speakers.

In linux, when I plug in the ear phones, I get audio out both.  I tried going to the sound preferences but could not figure out an option to do this.  I tried to google but was unable to get an answer to my long query.

Is there something I need to set?  If so, where?

Thanks,

dont know if this will work but what if you went into alsa by double clicking your sound icon and muted your speakers.just a thought dont have a headset hooked up but thinking that should work but is a bit inconvient

---

### Post by ashlakim on 2007-11-14
Hello. I noticed this problem too. My Laptop is a HP520. My notebook speaker wont mute if i jack in my earpiece/headset. 

My mate has a Sony VAIO but there was no problem. Her notebook speakers mute as she jacked in her earpiece/headphones.

Does anyone can provide help? I have tried the previous post's solution but to no avail.

Anyone?

---

### Post by aspora.isernia on 2008-03-12
I'm having the same problem, but until yesterday all worked fine: plugging the jack of the headphones suddenly quieted the speakers, but today it doesn't work any more... I checked also with Windows if it was a hardware problem but it is not.
Any idea? I have a MSI s300 with GG.

Thanks

a.i :)

---

### Post by ryanisablond on 2008-03-13
I had this problem too, with my Compaq nx6110. The following solution worked for me, but your mileage may vary... :-s

In the terminal, type in "alsamixer" (without the quotes). You should come to a screen with a bunch of configuration options like speaker balance, recording levels, etc.. One of said options will be a check box labeled something along the lines of "mute speakers when headphones detected." 

Navigation is pretty simple: use the arrow keys. For complete keyboard commands, check out [http://en.wikipedia.org/wiki/Alsamixer#Keyboard_Commands]("http://en.wikipedia.org/wiki/Alsamixer#Keyboard_Commands").

I know I'm butchering the name of the option, but my Ubuntu box is in pieces right now, so I can't check. Still, I hope this helps!

---

### Post by aspora.isernia on 2008-03-14
> **ryanisablond said:**
> I had this problem too, with my Compaq nx6110. The following solution worked for me, but your mileage may vary... :-s

In the terminal, type in "alsamixer" (without the quotes). You should come to a screen with a bunch of configuration options like speaker balance, recording levels, etc.. One of said options will be a check box labeled something along the lines of "mute speakers when headphones detected." 

Navigation is pretty simple: use the arrow keys. For complete keyboard commands, check out [http://en.wikipedia.org/wiki/Alsamixer#Keyboard_Commands]("http://en.wikipedia.org/wiki/Alsamixer#Keyboard_Commands").

I know I'm butchering the name of the option, but my Ubuntu box is in pieces right now, so I can't check. Still, I hope this helps!

Sorry, I had already tried alsamixer, but no options helped!! I'm still stuck with this problem...
Any other suggestion??

Thanks.

a.i :)

---

### Post by britline on 2008-03-15
install alsa driver 
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)
maybe can help...

sory my inglish bad.....

---

### Post by aspora.isernia on 2008-03-15
> **britline said:**
> install alsa driver 
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)
maybe can help...

sory my inglish bad.....

I don't understand: ALSA is the default component to handle sounds in ubuntu and is already present in all the installations...

---

### Post by aspora.isernia on 2008-03-15
Hi guys...
I just found an alternative solution (not just what I wanted...) to mitigate the issue of the thread topic: the solution was found in this [THIS FORUM]("http://www.mepislovers.org/forums/showthread.php?t=9446"), that (strange but true) found its inspiration by ubuntuforums... After the reboot indicated by the link, I have a couple of new sliders in the mixer and a new check box called HEADPHONE: checking the box cut the audio from the speakers and enable only the headphone jack as output.

Actually, I'm still looking for the option that allows me to plug in the headphone's jack and stop my speakers channel... But this is better than nothing!! ;)

Cheers

a.i :)

---

### Post by newone757 on 2008-03-16
i had this problem last week and solved it by searching google. i cant remember for sure but i think this is what i did to get it working right. but im using an hp laptop so you might need to do a variation of this. backup files before trying

**scroll to "Sound"**

[https://wiki.ubuntu.com/HP_Pavillion_dv6000_(dv6604nr](https://wiki.ubuntu.com/HP_Pavillion_dv6000_(dv6604nr))

---

