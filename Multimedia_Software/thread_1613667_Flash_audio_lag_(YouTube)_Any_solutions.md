---
title: "Flash audio lag (YouTube) Any solutions?"
date: 2010-11-04
forum: Multimedia Software
---

### Post by Liam1995 on 2010-11-04
Okay so this is a problem that has been annoying me for the whole duration of my time using Ubuntu and indeed any Linux system.

When I watch a flash video (YouTube) or play a flash game (Armor Games) the audio seems to be out of sync, or lags. In videos it's not as noticeable, and I can only notice when I watch a drum video or an instrumental video. Speech seems to be in sync. The audio also remains for around a second or two when I pause the video, however the video pauses basically instantly. In a flash game, it is a great deal more noticeable.

My laptop is a Toshiba Satellite L300, and I have 2GB of RAM. My processor is an Intel Core 2 Duo with 2.00GHz (none of this makes much sense to me, I'm not very good with hardware). 

Here's a full list of my specifications: [http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&toshibaShop=false&BV_UseBVCookie=yes&PRODUCT_ID=1056298](http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&toshibaShop=false&BV_UseBVCookie=yes&PRODUCT_ID=1056298)

My version is Ubuntu 10.10. 
I use Google Chrome as my primary browser, but I've tried it in many other browsers and the problem remains.
The lag/out of sync also appears in VLC video player, but not totem.

Does anyone know how to fix this?

---

### Post by lovinglinux on 2010-11-04
Which flash plugin are you using?

You could try to delete pulseaudio and asound config files and reboot. After that you might need to reconfigure the audio options from the audio panel widget, make a backup to be safe.

```
rm -fr ~/.pulse 
rm -fr ~/.asound*
```

---

### Post by Liam1995 on 2010-11-04
> **lovinglinux said:**
> Which flash plugin are you using?

You could try to delete pulseaudio and asound config files and reboot. After that you might need to reconfigure the audio options from the audio panel widget, make a backup to be safe.

```
rm -fr ~/.pulse 
rm -fr ~/.asound*
```

I'm using the flash plugin that is already with Google Chrome, I went to download Flash 10 manually from the Adobe website but it only informed me that my browser already has a Flash 10 plugin. 

If I were to remove both of these, what would be the outcome? I don't understand how deleting these will solve my problem, could you explain in further detail please? :)

---

### Post by lovinglinux on 2010-11-04
> **Liam1995 said:**
> I'm using the flash plugin that is already with Google Chrome, I went to download Flash 10 manually from the Adobe website but it only informed me that my browser already has a Flash 10 plugin. 

If I were to remove both of these, what would be the outcome? I don't understand how deleting these will solve my problem, could you explain in further detail please? :)

Usually when there is audio issues with flash plugins, is some problem with pulseaudio configuration. Deleting those will reset it.

More info [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by arindammanidas on 2010-11-04
Liam, first check again that you are using the latest version of flash.  Secondly do what LovingLinux says...that will make the system re-configure those  modules. 

Does the same happen in Mozilla?

---

### Post by Liam1995 on 2010-11-05
> **lovinglinux said:**
> Usually when there is audio issues with flash plugins, is some problem with pulseaudio configuration. Deleting those will reset it.

More info [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

Okay thanks :)

---

### Post by Liam1995 on 2010-11-05
> **arindammanidas said:**
> Liam, first check again that you are using the latest version of flash.  Secondly do what LovingLinux says...that will make the system re-configure those  modules. 

Does the same happen in Mozilla?

I'll try what LovingLinux says & yes it does unfortunately, I've tried all web browsers I can possibly thing of.

---

### Post by Liam1995 on 2010-11-05
> **lovinglinux said:**
> Which flash plugin are you using?

You could try to delete pulseaudio and asound config files and reboot. After that you might need to reconfigure the audio options from the audio panel widget, make a backup to be safe.

```
rm -fr ~/.pulse 
rm -fr ~/.asound*
```

Sorry, this method didn't work. Do you have any other solutions?

---

### Post by lovinglinux on 2010-11-05
Create a new Ubuntu user, just for testing, and check if the problem persist while logged with that account.

---

