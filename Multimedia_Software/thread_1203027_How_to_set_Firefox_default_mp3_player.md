---
title: "How to set Firefox default mp3 player"
date: 2009-07-02
forum: Multimedia Software
---

### Post by edwinkcw on 2009-07-02
When I click some mp3 link in the firefox, it will start a unknown player as shown in the attachment. However, I suspect this player use old sound architecture OSS such that my device is locked if I use launch this player. I would like to change to use mplayer plugin. So I invoke "sudo apt-get install mplayerplug-in", but it still doesn't work. 

How can I know what player I am using? And how to change the firefox default player?

Thanks :p

---

### Post by starcraft.man on 2009-07-02
> **edwinkcw said:**
> When I click some mp3 link in the firefox, it will start a unknown player as shown in the attachment. However, I suspect this player use old sound architecture OSS such that my device is locked if I use launch this player. I would like to change to use mplayer plugin. So I invoke "sudo apt-get install mplayerplug-in", but it still doesn't work. 

How can I know what player I am using? And how to change the firefox default player?

Thanks :p

Edit > Preferences > Applications > Search or simply scroll until you see MP3. On the right of the entry you can select the player used. I'm partial to VLC for almost everything nowadays (it has a plugin in the repos as well).

An even easier way is an awesome plugin called media player connectivity. It basically scans a linux box for all usable media players and provides a nice GUI to pipe the video/aduio not just to the plugin, buc actually pipe it onto your desktop player (i.e. it will stream the media right through to an app outside the browser, like VLC or totem) thus letting you do other things than sit on the page while still seeing video.

I think it's only 32 bit though, doesn't quite seem to work on my 64 bit workstation, maybe I'm doing it wrong though.

That should do it, enjoy.

---

### Post by edwinkcw on 2009-07-02
> **starcraft.man said:**
> Edit > Preferences > Applications > Search or simply scroll until you see MP3. On the right of the entry you can select the player used. I'm partial to VLC for almost everything nowadays (it has a plugin in the repos as well).

An even easier way is an awesome plugin called media player connectivity. It basically scans a linux box for all usable media players and provides a nice GUI to pipe the video/aduio not just to the plugin, buc actually pipe it onto your desktop player (i.e. it will stream the media right through to an app outside the browser, like VLC or totem) thus letting you do other things than sit on the page while still seeing video.

I think it's only 32 bit though, doesn't quite seem to work on my 64 bit workstation, maybe I'm doing it wrong though.

That should do it, enjoy.

Thanks, let me try it

---

### Post by edwinkcw on 2009-07-02
> **starcraft.man said:**
> Edit > Preferences > Applications > Search or simply scroll until you see MP3. On the right of the entry you can select the player used. I'm partial to VLC for almost everything nowadays (it has a plugin in the repos as well).

An even easier way is an awesome plugin called media player connectivity. It basically scans a linux box for all usable media players and provides a nice GUI to pipe the video/aduio not just to the plugin, buc actually pipe it onto your desktop player (i.e. it will stream the media right through to an app outside the browser, like VLC or totem) thus letting you do other things than sit on the page while still seeing video.

I think it's only 32 bit though, doesn't quite seem to work on my 64 bit workstation, maybe I'm doing it wrong though.

That should do it, enjoy.

I only can see "Preferred Application" but there is only a multimedia tab with a pull down menu for me to select a player. I only find Move Player and Totem..Do I do something wrong?

---

### Post by starcraft.man on 2009-07-02
> **edwinkcw said:**
> I only can see "Preferred Application" but there is only a multimedia tab with a pull down menu for me to select a player. I only find Move Player and Totem..Do I do something wrong?

Can you take a screenshot of the tab, and I'll check. I'll be back momentarily, driver upgrade.

---

### Post by starcraft.man on 2009-07-02
This is the tab you should see in firefox (this is 3.5, also in 3.0 I believe). 

If it's not in your firefox version, woops. Check version under menu Help > About.

I just checked 3.0 and it's there too.

---

### Post by edwinkcw on 2009-07-02
> **starcraft.man said:**
> This is the tab you should see in firefox (this is 3.5, also in 3.0 I believe). 

If it's not in your firefox version, woops. Check version under menu Help > About.

I just checked 3.0 and it's there too.

Thanks, I have found many content type, but there is no one named "MP3". Then I search it in other computer, I can found it. What is happened? Should I reinstall the firefox? but how

---

### Post by starcraft.man on 2009-07-02
> **edwinkcw said:**
> Thanks, I have found many content type, but there is no one named "MP3". Then I search it in other computer, I can found it. What is happened? Should I reinstall the firefox? but how

I think your missing the codecs then. Did you install restricted package?

Open a terminal (applications > accessories > terminal) and install them with:

```
sudo aptitude install ubuntu-restrcited-extras vlc vlc-plugin-pulse
```

That will also ensure VLC is installed. Something's gotta show after that. Or else somethings really off.

---

### Post by edwinkcw on 2009-07-03
> **starcraft.man said:**
> I think your missing the codecs then. Did you install restricted package?

Open a terminal (applications > accessories > terminal) and install them with:

```
sudo aptitude install ubuntu-restrcited-extras vlc vlc-plugin-pulse
```

That will also ensure VLC is installed. Something's gotta show after that. Or else somethings really off.

umm.... I have followed you guide. but...no mp3 in the firefox application dialog. anyway, thanks

---

