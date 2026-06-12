---
title: "Sound is off"
date: 2006-01-14
forum: Multimedia &amp; Video
---

### Post by Ubuntuud on 2006-01-14
Hi, I've got a problem with my sound, it isn't there. I don't know what the exact problem is but I think my sound card isn't working... What can I do to make it work? If you need more information, just ask.

---

### Post by 23meg on 2006-01-14
What's your sound card? Is it detected in Device Manager and is any device name shown in the Gnome panel mixer applet?

---

### Post by Ubuntuud on 2006-01-14
It's builded in and I don't think it has a specific name. So I don't know if it is listed in the device manager.

---

### Post by xylene2301 on 2006-01-14
I'm having a similar problem while trying to ressurect a compaq presario 5100 with audio on the motherboard.  The problem is; no driver.
I found a provider, OSS, [http://www.opensound.com](http://www.opensound.com) that has a lot of linux drivers for linux 2.4 debian (which I think is Ubuntu) but they eventually want $50...is it worth it?   Dunno.

---

### Post by rossjman1 on 2006-01-14
You can always just reinstall the OSS trial. It's a pain to look at the message when you do soundon though.

---

### Post by Teroedni on 2006-01-14
cat /proc/asound/cards


that will list the drivers if they exist

If they dont
You need to compile modules
or recompile  completely alsa

---

### Post by Ubuntuud on 2006-01-14
There are so many developers for linux. Can't they think of a solution?

---

### Post by Teroedni on 2006-01-14
Not easy no
The problem is this
They(hardware manufactor of sound cards) wont give out information about their card .Therefore it often get difficult to build drivers,near Mission Impossible;)


But what did  ```
cat /proc/asound/cards 
```

give you?

---

### Post by Ubuntuud on 2006-01-14
Oh, sorry. I didn't refresh the page. It resulted in: IHC4 - Intel IHC6 Intel IHC6 with ALC250 at 0xb0040800, irq 17. Thanks, now I can go and search for the driver.

---

### Post by Ubuntuud on 2006-01-15
I can't find the driver, on the intel website there aren't any soundcard drivers...

---

### Post by Teroedni on 2006-01-15
ahh you need to look at 
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

---

### Post by JanvL on 2006-01-15
Hi all

It all depends wether your soundcard is detected OK.
After installing Ubuntu you should give user "root" a password
that you know so you can enter your system as the superuser root.
Mind that you even have to allow that root anters the system in the Grafical
user environment, I know some appose to it but I am lazy enough to
want to mouse-around even as root.

When you have the account root so that you can enter the system as root
in the grafical environment, then log in as root.
If you hear your sound the card is OK.
Then go to "Systemtools" - "users and groups" select your user, then choose 
properties, then choose the Tab "userrights" there the second choice is the
soundcard, and allow yourself to have some sound!

After that log off as root, log of as the user that you changed it for and log on again,
then you will have your sound.

It sounds complicated, but it is not.

Jan

---

### Post by Ubuntuud on 2006-01-16
I understand, but I allready could hear that sound, but that is all. In all my games/apps I can't hear a thing, one demo (Tribal Trouble) "said" that there was a problem with my sound card...

---

### Post by Ubuntuud on 2006-01-16
And something else, it is displayed in the device manager... I really don't get it.

---

