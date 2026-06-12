---
title: "Flash Player 13.10 - Fullscreen exit problem"
date: 2014-01-31
forum: Multimedia Software
---

### Post by White_Star on 2014-01-31
First Post
Fresh 13.10 install, fully updated. Only one system problem which is unrelated (unexpected resume/suspend error)
When streaming fullscreen videos through flash player everything is fine, but when I exit the last video frame is stuck in the background behind my browser window. It covers up the unity launcher and taskbar too. Really annoying as can't switch windows or tabs quickly as system has to refresh itself to erase the stuck frame. Example of this is attached 

In addition some webforms (all buttons browse local to search for files to upload ) and other video player panels have a scrambled thumbnail instead of the correct one - more examples attached
If watching a 4:3 video on some video players which are nearly always 16:9 , normally the player would have a black border around the video but what happens is parts of the frame get stuck and hang around the playing video[ATTACH=CONFIG]249962[/ATTACH][ATTACH=CONFIG]249963[/ATTACH][ATTACH=CONFIG]249964[/ATTACH]

---

### Post by monkeybrain20122 on 2014-01-31
This is chrome, correct? Did you try Firefox or try to switch to the system's flash plugin?

---

### Post by White_Star on 2014-02-01
Both chrome and firefox.
Also divx player just loads a big no entry sign on all players.
I have restricted extras installed and gstreamer extras too.

---

### Post by monkeybrain20122 on 2014-02-01
> **White_Star said:**
> Both chrome and firefox.
Also divx player just loads a big no entry sign on all players.
I have restricted extras installed and gstreamer extras too.

Can you post a link where divx player just loads a no entry sign?

---

### Post by White_Star on 2014-02-02
like this [ATTACH=CONFIG]250018[/ATTACH] and here is another example of the button problem I have when the thumbnail is replaced with a scrambled mess [ATTACH=CONFIG]250019[/ATTACH]

---

### Post by monkeybrain20122 on 2014-02-02
Not having a link I guess the first problem is due to the fact that Totem is unable to play the divx link (Totem has always been a hit and miss with divx) If you are using Firefox I suggest you install the gecko-mediaplayer and then disable the totem plugins in Firefox by going to Tools > addons > plugins and set all the totem entries to "Never Activate". Of course I assume that you already have install ubuntu-restricted-extras.In Chrome you can go to about:plugins and disable Totem. In any case you may be out of luck with streaming formats other than flash if you use chrome. In April google will stop supporting all NNAPI plugin for Linux that includes pretty much every media plugin other than flash, so those won't play in chrome after April anyway. (Edited: in the list of plugins there is something called Vlc something compatible with Video, that is not VLC, but Totem, so disable that as well)

Another possible reason that you are seeing the no go sign in FF is that the browser now blocks active mixed contents by default, so you may have to unblock it at the url bar (the left most corner there is a lock thing, click it) and reload the page. Alternatively you can install an addon [https://addons.mozilla.org/en-us/firefox/addon/toggle-mixed-active-content/](https://addons.mozilla.org/en-us/firefox/addon/toggle-mixed-active-content/)

Sorry, I have no idea what causes you second problem (with the buttons)

---

### Post by d-cosner on 2014-02-02
To fix the flash problem in Firefox I turn off hardware acceleration in the browser first. I open a youtube video in full screen, right click on it and turn off hardware acceleration in the settings for flash itself. I have used this method on three computers with completely different graphics cards and flash has worked fine. All 3 computers are using the stock open source graphics drivers too.

---

### Post by White_Star on 2014-02-03
Flash problem fixed thank you d-cosner
divX still having issues - thanks monkeybrain for the ideas, I do think it this is the source but that particular solution didn't work. I will spend time uninstalling all, updating and checking no conflicts between packages.

---

### Post by monkeybrain20122 on 2014-02-03
It would be good if you can provide one of these divx links that don't work.

---

