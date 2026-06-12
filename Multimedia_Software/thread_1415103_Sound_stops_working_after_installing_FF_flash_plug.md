---
title: "Sound stops working after installing FF flash plugin"
date: 2010-02-24
forum: Multimedia Software
---

### Post by syg6 on 2010-02-24
I am a newbie to Linux desktop, but I know quite a bit about using the command line.

I recently installed Ubuntu 9.10 / GNOME and all was well upon reboot, sound worked no problem.

The I installed the FF flash plugin and sound disappeared. I tried uninstalling then re-installing the flash plugin, and basically have tried all the steps in the Comprehensive Sound Problem Solutions guide, including un-installing and then re-installing sound:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop

aplay -l shows my sound card is detected and working. alsamixer shows my levels are all maxed. I put my user in the audio group in /etc/group.

It can't be a driver problem since with a fresh install of Ubuntu sound works.

What could be the problem?

Thanks,
Bob

---

### Post by thundre on 2010-02-24
I have a similar problem and a workaround.

Flash and regular apps don't play well together.  When I want to run the music player, if Firefox is running I go to Tools->Add-ons->Plugins and disable Flash.  Then start the music player (Gnome MPlayer).

If I don't disable Flash as the first step, the music player locks up.  Then I have to "ps ax | grep player" and kill the player process(es) before anything will work.

When I want to run Flash again, I have to exit or at least stop (not pause) mplayer, then re-enable Flash and hit reload.  If I re-enable it without stopping the player, Flash video works but sound doesn't.

---

### Post by syg6 on 2010-02-24
Well that's not exactly my case. I don't even have sound in Flash, for example watching youtube. But just for giggles I disabled the Flash plugin and it didn't fix anything; I am without sound in all of Gnome. :(

Any other ideas?

Bob

---

### Post by VertexPusher on 2010-02-24
> **thundre said:**
> Flash and regular apps don't play well together.
They play together PERFECTLY if you remove PulseAudio.

---

### Post by syg6 on 2010-02-25
Well, I tried un-installing Pulse Audio but it didn't fix anything.

By default when you install Ubuntu, Pulse Audio is installed as the sound server, correct? As I mentioned, sound works fine with a clean install. So I doubt Pulse Audio is the problem. It may be the reason I don't have sound with Flash videos, but I don't think it's the problem with system sound not working.

I tried un-installing the Flash plugin as well, no go.

I'll keep reading the Pulse Audio wiki page, but I think my problem lies elsewhere ...

Thanks,
Bob

---

### Post by thundre on 2010-02-25
> **VertexPusher said:**
> They play together PERFECTLY if you remove PulseAudio.
Oh wow, that helps me, thanks!  Aptitude was going to remove ubuntu-desktop, so I just killed the pulseaudio process and replaced /usr/bin/pulseaudio with an empty script, leaving the rest of the package intact.

Syg6, you didn't say if you did anything to get rid of the locked-up processes, such as reboot.  But I guess it must be a different problem if sound isn't working in Flash or in the regular apps.

p.s.  I'm still leaving Flash disabled most of the time because I hate ads that move when I'm trying to read.

---

### Post by VertexPusher on 2010-02-26
> **thundre said:**
> Aptitude was going to remove ubuntu-desktop, so I just killed the pulseaudio process and replaced /usr/bin/pulseaudio with an empty script, leaving the rest of the package intact.
Excuse me, but this is totally backwards. Removing ubuntu-desktop does not break system integrity. Bypassing the package manager by replacing /usr/bin/pulseaudio does.

You don't seem to understand the meaning of the ubuntu-desktop package. It's a system restore point. It helps you revert any changes to Ubuntu's default software configuration.

If you don't allow it to be removed, you defeat its entire purpose. Think of a ship's anchor: If you don't allow the anchor to leave the ship, what's the point of having one in the first place?

Please read this: [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

