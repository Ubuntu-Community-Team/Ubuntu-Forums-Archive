---
title: "[SOLVED] System Sounds !!!"
date: 2008-05-10
forum: Multimedia Software
---

### Post by ENigma885 on 2008-05-10
*(it's the second time to post this problem ,any help would be appreciated)*

After an upgrade from 7.10 to 8.04 i couldn't enable system sounds-but the media sounds r working well- (System>>Preferences>>Sound> Sounds Tab)..i faced the same problem in 7.10 but i got it to work after installing those packages 
```
sudo apt-get mpg123 mpg123-alsa esound
```
when i tried to do the same thing in Hardy Heron and i rebooted my system,*_GNOME panels weren't loaded properly_* and the system in general didn't response . 
So i booted up in safe mode and uninstalled the previously installed packages and after several tries i figured out that *_(esound) is the reason behind this problem._*

***[COLOR="Red"]so is there any way to enable the system sounds or to configure esounds not to crash my system at start up?[/COLOR]***

btw after uninstalling esound ,sounds preview in (System>>Preferences>>Sound> Sounds Tab) doesn't work. and i tried to play the files in Audacious and they worked .

---

### Post by ebazz on 2008-07-08
I'm a newbie, and I have the same problem.
I upgraded to 8.04 and the system sounds don't play.

I wish some could give me a plain language answer to this.

Thank you.
Sincerely,
Frustrated.

---

### Post by ENigma885 on 2008-07-08
I have solved my problem ....

It's all about the PulseAudio, the new sound server in 8.04 Hardy,. Instead of that every application has its way to access the sound card, PulseAudio becomes a common (gate) to access ur sound card. The problem is that not all applications can deal with the new sound server. But it's getting better.

[COLOR="Red"]***Regarding ur problem***[/COLOR], apparently System Sounds have also a problem dealing with PulseAudio to get over it i installed "PulseAudio ESD compatibility layer" u can install it by opening a new terminal *(Applications>>Accessories>>Terminal)* and paste 
```
 sudo apt-get install pulseaudio-esound-compat
```

One last thing:
-Make sure that PulseAudio is configured the primary sound device *(System>>Preferences>>Sound)* and in the* _Device_ tab* select PulseAudio Sound Server, sometimes it will require a system restart to work properly, 
-Make sure that Software Sound Mixing is enabled from the *[I]_Sounds_* tab[/I] in Sound Preferences check "*Enable Software Sounds Mixing ESD"*

---

### Post by ebazz on 2008-07-11
Thank you for the reply.
I'll try your suggestion and let you know how I make out.

---

### Post by ebazz on 2008-07-11
Ok I tried your suggestion and still no sound.
There is no sound on Firefox either.

Upgading to Hardy seems to have been a mistake. Everything worked in version 7.+.

Thank you for trying though.
EBazz

---

### Post by ebazz on 2008-07-11
Update!

I've got some system sounds, but still no sound from Firefox.
Some of this ALSA thing is working, but obviously not all of it.

I get sound effects on startup,login, but when I go to preferences\sound I 
can't get anything to play. I changed all of the settings to ALSA and sounds do play from the devices menu only.
Any more help would be appreciated.

ebazz

---

### Post by Spaced on 2008-07-27
I have done as you suggested, but the "End session" sound still doesn't work.

---

### Post by ENigma885 on 2008-07-27
Well
[COLOR="Red"]@ Spaced:-[/COLOR] the shutdown sound is a known issue and i suppose it's because PulseAudio Server shuts down earlier before the complete shutdown of the whole system.
And unfortunately i haven't found any work around to delay PulseAudio shutdown...if i found any i will let u know of course.
But i'm glad that u were able to make the "System Sounds" work =)

[COLOR="Red"]@ebazz:-[/COLOR] i will try to make a mini-howto with pictures to make it easier for u...
and for the Firefox thing it's not related to "System Sounds" most properly related to FlashPlayer Support library to use PulseAudio open a terminal window and enter
```
 sudo apt-get install libflashsupport
```

---

### Post by ENigma885 on 2008-07-27
[COLOR="Red"]@ebazz[/COLOR] (late reply sry)
1.That's wat i meant by making PulseAudio the primary sound device It's PulseAudio Sound Server [COLOR="Red"]***not ALSA ***[/COLOR]
[[IMG]http://img516.imageshack.us/img516/7758/soundprefrences1devicesen3.jpg[/IMG]](http://imageshack.us)

2.That's wat i mean by checking Software Sound Mixing
[[IMG]http://img291.imageshack.us/img291/2155/soundprefrences2soundsyc3.jpg[/IMG]](http://imageshack.us)

---

### Post by Spaced on 2008-07-28
> **ENigma885 said:**
> Well
[COLOR="Red"]@ Spaced:-[/COLOR] the shutdown sound is a known issue and i suppose it's because PulseAudio Server shuts down earlier before the complete shutdown of the whole system.
And unfortunately i haven't found any work around to delay PulseAudio shutdown...if i found any i will let u know of course.
But i'm glad that u were able to make the "System Sounds" work =)

Thank you, I'll follow your progress... :) In fact, with the other system sounds I had never had problems, the only one is with the logout sound, but you have just explained the reason. I had wrongly understood that your suggestions would have fixed that bug... see you...

---

### Post by onegentleman on 2009-05-29
I don't have the option "Enable Software Sounds Mixing ESD" in ubuntu 9.04 jaunty jackalope. I do all the things ENigma885 describes and I still don't have system sounds. :(

---

