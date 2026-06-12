---
title: "disappeared: capture, mic options"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by mprobertson on 2007-09-09
I am on ubuntu 7.04, several months without windows. 

When first configuring everything I spent a very long time messing around with sound options etc. Then it worked, but just now after updating some things and maybe messing around with some other options, several sound input/output options have disappeared. When i run alsamixer there used to be 10 or so bars, now many have gone. Same when I run gnome-volume-control.

Main_front (i think it was) has gone, so has "mic", "capture 2", "front_mic", "line_in" and several others. the most important is mic, because now I cannot use my microphone for important things.

Teamspeak also does not receive any sound.

What might have caused my sound settings to have gotten screwed and to lose all those options? How can I get them back? I have looked through Comprensive Guide but it does not address this issue. MY SOUND WORKS but I have no microphone, input.

---

### Post by linuxwizard on 2007-09-09
If you have installed the latest updates for Ubuntu I would look at Launchpad see if a bug has been reported. I have seen alot of issues with sound & other problems.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20)

---

### Post by mprobertson on 2007-09-09
Right, could be that. Any way to rollback the update? I can't find anything on that link related to this problem specifically. 

What else can I do? I use my computer microphone quite a lot, so I need this fixed. And the last thing I want to do is go back to windows!

---

### Post by linuxwizard on 2007-09-09
Do you still have the 2.6.20-15 kernel install on your system ? If so try booting from that and see what happens.See if your settings come back and mic works. Not sure how you can go about rolling back the updates. I saw another post by someone else who was asking that question also. That link to Launchpad I thought their might be something there on your sound card. Not sure what else to tell you. This is why I stopped taking the kernel updates to many issues.

---

### Post by mprobertson on 2007-09-10
I still have it and just booted onto it now. Now I can get vlc to play sound, which I couldn't before. On the other kernel it would not even play, and only jukebox would do any sound--nothing else.

I still have no microphone, and the options I had on gnome-sound-control and alsaconf are not back. This is what had the mic and everything.

I remember when I was first setting up I followed a guide that changed some configuration files related to the soundcard or sound drivers, putting in new information to make things work. After I did this it worked. Maybe updating the kernel replaced those files and I have to do it again. In any case using the old kernel didn't fix it.

Know what else? When I boot the screen is black with the white 'thinking' circle with beads running around the outside. This goes on indefinitely. I thought my computer was wrecked originally. I worked out that I could get to the login screen by pressing ctrl-alt-backspace. But it won't go to the login screen by itself, and I need to do this every time. I could not find anywhere which explained this nuisance. As long as it works though that is a relatively minor issue. I am more concerned about the microphone!

---

### Post by mprobertson on 2007-09-10
IT WORKS.

I don't know what happened, but all the options for alsa have reappeared. I rebooted and am running kernel 16, with capture 1, 2, mic, front_mic, etc. all now having come back.

No idea why. I hope they stay there. Anyway, can I save the configuration files for the sound card/drivers,so in case something messes up I can just replace them in a snap? It has been a difficult couple of days and would not want to do this again.

---

