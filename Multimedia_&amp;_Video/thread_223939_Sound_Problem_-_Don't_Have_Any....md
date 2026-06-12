---
title: "Sound Problem - Don't Have Any..."
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by JustDon on 2006-07-27
When I boot my Ubuntu machine up the volume control is x'd out. When I double click on it I get:

[COLOR="Blue"]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.[/COLOR]

I have been through the sticky thread "Comprehensive Sound Problem Solutions Guide" and nothing worked. I get the "drum tap" sound at log in but nothing else. Any idea what to do next?

---

### Post by philippe_carlo on 2006-07-27
This is probably a permission problem. The drum tab you hear is caused by gdm, which runs as root. When you login as a user, you have different rights. I suspect you have no write permissions on the corresponding device. Maybe your user is not part of the audio group?

Try
```
adduser <your login> audio
```

If that does not work, post the output of the following commands here:
```

sudo ls -al /dev/dsp
sudo ls -al /dev/snd
groups

```

---

### Post by JustDon on 2006-07-27
> **philippe_carlo said:**
> This is probably a permission problem. The drum tab you hear is caused by gdm, which runs as root. When you login as a user, you have different rights. I suspect you have no write permissions on the corresponding device. Maybe your user is not part of the audio group?

Try
```
adduser <your login> audio
```

Wow, that was simple, thanks a lot. I almost always search for sticky(s) or other threads dealing with my same problem but this is one case in which I should have just posted my problem. I spend 4-5 hours entering code, apt-get intalling, uninstalling, etc. for a simple permission problem, :sad: . 

Thank you so very much my friend!

---

### Post by JustDon on 2006-07-27
This is a minor issue (now that my sound works) BUT does anyone happen to know the name of the default music that plays AFTER you log in, while KDE is loading the desktop? The best description I can give is the (if you can imagine) the sound that perhaps fireflies would make if they could sing.... It is not a boing or beep or anything but is distinctly musical in nature.

In tinkering with all of my sound settings trying to fix the lack of sound, I seem to have messed up my default sounds.

---

