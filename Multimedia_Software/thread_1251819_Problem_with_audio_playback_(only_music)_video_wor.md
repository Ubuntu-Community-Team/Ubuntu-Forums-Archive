---
title: "Problem with audio playback (only music) video works fine"
date: 2009-08-28
forum: Multimedia Software
---

### Post by Radhavictory on 2009-08-28
Hello,
Ubuntu 9.04
Acer 5620

Since a few days now, I have a problem with audio playback. If i watch a video on youtube and then try to open a music player, the player doesn't play music. The two players that I have tried are rhythm box player and exaile. The same is the case with skype, the audio does not work. If I try playing a video though, it works perfectly fine, both the video and audio.
This problem doesn't occur if I don't use youtube. If I try listening to music without using youtube, it works fine...same for skype.
The only way for me to get skype and the music going is by restarting the computer.
Can someone please help out with this problem? Any help will be greatly appreciated,

Thanks in advance!

---

### Post by pedro_orange on 2009-08-28
You're issue is sharing of the sound mate.

Basically, when you use YouTube - there is sound. Therefore flash within firefox is essentially locking the sound mutex, stopping other applications from using the sound.

If you close firefox, and then open a music player - you will see that it will work.

To share sound over multiple applications you need to install the package alsa-oss.

Here is a nice how to: [https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20more%20than%20one%20application%20to%20use%20the%20soundcard%20at%20the%20same%20time](https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20more%20than%20one%20application%20to%20use%20the%20soundcard%20at%20the%20same%20time)

---

### Post by Radhavictory on 2009-08-28
thanks for the workaround pedro_orange,

but does this mean that everytme I want to open the music player, I gotta do it from the terminal?

---

### Post by pedro_orange on 2009-08-28
> **Radhavictory said:**
> thanks for the workaround pedro_orange,

but does this mean that everytme I want to open the music player, I gotta do it from the terminal?

Are you referring to opening each application with aoss before it? Well there are a number of alternatives including:

1 - Configure the application so it runs using aoss (In it's internal settings)
2 - Edit your launchers to include this

---

### Post by Radhavictory on 2009-08-28
Hello pedro-orange,

OK so I have modified all the launchers by adding aoss before the command line for the said application but no change. I have to close the web browser for the music player to work. Sometimes even that doesn't work until I restart the PC, as I just did now....don't know, guess I will to manage this way until my next re-install of ubuntu?

---

