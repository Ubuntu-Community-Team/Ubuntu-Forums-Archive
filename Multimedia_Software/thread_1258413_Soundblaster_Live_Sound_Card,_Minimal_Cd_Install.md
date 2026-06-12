---
title: "Soundblaster Live Sound Card, Minimal Cd Install"
date: 2009-09-05
forum: Multimedia Software
---

### Post by Tempter on 2009-09-05
I installed Ubuntu 9.04 via the minimal cd and proceeded to install openbox, along with other progs, alsa-base, alsa-utils, linux-sound-base, and even the restricted kernel modules.

However, for some reason I am not able to get ubuntu to recognize my sound card, that is until I issue the command: lspci -v. And then it states correctly that my sound card is creative labs sb live emu10k1 sound card.

At this point all I should have been able to do to resolve this issue was either (1) issuing alsaconfig (but for some reason ubuntu has disabled this command) or (2) sudo modprobe snd-emu10k1 (but this doesn't do anything either), but neither works.

At this point I am at a loss in what to do, and it seems that Ubuntu has strayed from the sound standards that most distributions use (this isn't a bad thing) and because of this I cannot seem to resolve this issue on my own.

If anyone one could help me in trying to figure out how to get my sound working I would really appreciate this.

Thanks in advance,
Tempter

---

### Post by Tempter on 2009-09-05
Well I did a little more poking around and I found a strange thing...

When I issue the command alsamixer, as the user, I get: function snd_ctl_open failed for default: no such file or dirctory.

However, when I issue that command as root, sudo alsamixer, I am greeted with the ncurses alsa mixer and every setting my card has to ofter me is at my finger tips.

So I started thinking that maybe it was because the group permissions were messed up?

So I did cat /ect/group and it seemed I was not appart of the audio group, but when i issue the command: sudo adduser -G audio <my user name> it said: user exits.

So ubuntu can in fact see it, but in order to see it I need to be root... and also maxing out the master and pcm voulme does not seem to help... I get no sound.

This is ever strange behavior, I wonder if its a bug with the minimal cd installer?

If anyone can help, please do!

---

### Post by Tempter on 2009-09-05
Well digging a little bit deeper I turned to IRC, and I was quickly given a soulution which was to sudo chmod 777 /dev/snd/* ...

This does in fact work, but its a huge security problem...

For it gives read, WRITING, and executing permission to everyone...

If this is the only work around for this then this is for sure a bug, or else ubuntu doesn't really care about security.

If you have another way of fixing this situation, please by all means let me know.

If I cannot get an answer soon I most likely will be leaving ubuntu, for I care not have my system compromised just to get sound.

Tempter

---

### Post by Tempter on 2009-09-05
Not willing to give up nor accept the solution given to me in irc (and no one else should either) I reinstalled ubuntu and installed alsa-base, alsa-utils, linux-sound-base, and pulseaudo.  

What this allowed me to do was start alsamixer from command line without X, however, as soon as I went into X (aka openbox) and tried to issue the command alsamixer from a terminal emulator I was again greeted by the message "alsamixer: function snd_ctl_open failed for default: no such file or directory". 

So I can start alsamixer without X, but while in X I cannot... strange.  Also I have no idea if I can play sound yet while not in X... 

There has to be someone out there who knows how to fix this...

"I'm Sending out an SOS, I'm sending out an SOS..." - Sting

Tempter

---

