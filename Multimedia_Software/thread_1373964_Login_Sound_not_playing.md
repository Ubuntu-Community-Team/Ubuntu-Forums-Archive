---
title: "Login Sound not playing"
date: 2010-01-06
forum: Multimedia Software
---

### Post by bilalakhtar on 2010-01-06
When I start my computer, my comp is set to require password everytime I start the computer. I am using Karmic with all the latest updates. One day, from the Login Screen itself, I selected the Power icon at the bottom right and selected Shut Down. But, from next boot, the login drum sound wouldnt play and even the african sound that comes after logging in wouldn't play. The african sound problem was solved when I noticed that my sound was muted by the GDM on shutdown. However, the drum sound still does not come. I think the solution it to change the volume before logging in. How do I do this? Can I do this from a terminal? :guitar:

---

### Post by bilalakhtar on 2010-01-06
Bump?

---

### Post by bilalakhtar on 2010-01-07
Hello?

---

### Post by Yellow Pasque on 2010-01-07
Make sure the sound is enabled:
```
sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool true
```

---

### Post by bilalakhtar on 2010-01-08
> Make sure the sound is enabled:
Code:
```

sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool true

```

It didnt work. No change

---

### Post by bilalakhtar on 2010-01-08
When I type
```
sudo -u gdm gconftool-2 -a /desktop/gnome/sound
```
I get:-
```
 enable_esd = true
 event_sounds = true
 theme_name = ubuntu
 default_mixer_device = 
 default_mixer_tracks = []
 input_feedback_sounds = false

```
I notices that the default_* keys are empty. How to I solve the problem?

---

