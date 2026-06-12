---
title: "Sound stops working after quitting a game"
date: 2012-09-09
forum: Multimedia Software
---

### Post by Magzimum on 2012-09-09
I run Ubuntu 12.4 (64 bit). After a long struggle, I managed to get a game running: Settlers 7. It requires that I use Gnome, somehow... In Unity, the frame rate is horrible (about 1 fps). It's a workaround, but it is good enough. (Weirdly, Gnome itself runs awfully: it lags and is just really slow - but Settlers 7 runs smoothly in Gnome... and Unity is crisp and quick to use, but the game is slow.)

Anyway, my main issue at the moment is: once I quit the game, the sound stops. Rebooting does not help, changing to Unity also doesn't change anything. So in the game, I have sound, but after I quit the game, I cannot play mp3, or get sound from any flash players on websites (e.g. youtube). 

I can start the game as often as I like. In the game, I have sound. Quit the game, and sound is gone.

I already went through the Alsamixer, and muted/unmuted everything. Nothing changed, so I put everything back to its original settings and closed it.

Any ideas?
p.s. Yes, I am a newbie to Ubuntu and may have overlooked something obvious.

---

### Post by kostkon on 2012-09-09
Are you using Wine to run the game? If yes, try installing the latest version of Wine, by following the instructions [here]("http://www.winehq.org/download/ubuntu"). Just add the line in your software sources and then check for updates in the update manager.

---

### Post by Magzimum on 2012-09-09
Alright, that was useful. Thanks. I was under the assumption that if I install Wine from the software center, it would also be included in the updates. Also, I thought that the software center would install the latest versions (I only installed Wine yesterday). What's the point of this software center if it does not install the latest version, and if it does not update it either? 

Anyway, let's not complain too much now. I have updated to Wine 1.4. 

But I still have no sound. And since my update of Wine, the game has also gone mute. Right now, I have no sound at all. :)

[edit] I just did a system test (Applications > System tools > Administration > System Testing), and that must have reset some of the original settings. Sound is back.

---

### Post by kostkon on 2012-09-10
> **Magzimum said:**
> I was under the assumption that if I install Wine from the software center, it would also be included in the updates. Also, I thought that the software center would install the latest versions (I only installed Wine yesterday). What's the point of this software center if it does not install the latest version, and if it does not update it either?
Many don't (the packages that are imported from the debian repositories), but some do get updated ([the ones published directly to the software centre]("http://developer.ubuntu.com/publish/"), at least most of them).

The situation will slowly change in the future, gradually more and more applications will always be up-to-date. For the reason, check these posts [here]("http://www.iloveubuntu.net/ubuntu-developers-published-new-automatic-third-party-app-uploading-process-ubuntu-software-center") and [here]("http://www.jonobacon.org/2012/09/06/opening-ubuntu-up-to-the-world/").

---

