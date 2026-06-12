---
title: "Where is gmpalyer input.config?"
date: 2009-10-28
forum: Multimedia Software
---

### Post by evar on 2009-10-28
I found input.config in ~/.mplayer and /etc/mplayer but it only affect mplayer. How to change hotkeys for gmplayer?

---

### Post by vinutux on 2009-10-28
gmplayer is basically mplayer with gui [graphical menu] 

what i think all hot keys u change affect to gmplayer as well...

---

### Post by evar on 2009-10-28
Oh, I've tried to change other buttons in ~/.mplayer/input.conf and it worked, you right vinutux. But I can't bind mouse buttons for gmplayer, this is what I need.

---

### Post by vinutux on 2009-10-28
**[URL="http://www.mplayerhq.hu/DOCS/HTML/en/control.html"][B]I dont have any experience here but fount this one**

[I][COLOR="DarkRed"]MPlayer allows you bind any key/button to any MPlayer command using a simple config file. The syntax consist of a key name followed by a command. The default config file location is $HOME/.mplayer/input.conf but it can be overridden using the -input conf option (relative path are relative to $HOME/.mplayer).

You can get a full list of supported key names by running mplayer -input keylist and a full list of available commands by running mplayer -input cmdlist.

Example 3.1. A simple input control file

##
## MPlayer input control file
##

RIGHT seek +10
LEFT seek -10
- audio_delay 0.100
+ audio_delay -0.100
q quit
> pt_step 1
< pt_step -1
ENTER pt_step 1 1
[/COLOR][/I]


From this link : http://www.mplayerhq.hu/DOCS/HTML/en/control.html[/URL][/B]

---

### Post by vinutux on 2009-10-28
And here is a wikibook **[http://en.wikibooks.org/wiki/Mplayer#OSD_Menu]("http://en.wikibooks.org/wiki/Mplayer#OSD_Menu")**

Another one [http://howto.wikia.com/wiki/Howto_configure_MPlayer#Input_Keyboard.2Fjoystick.2Fmouse.2FLIRC_bindings]("http://howto.wikia.com/wiki/Howto_configure_MPlayer#Input_Keyboard.2Fjoystick.2Fmouse.2FLIRC_bindings")

---

### Post by andrew.46 on 2009-10-28
Hi evar,

gmplayer is pretty much abandoned by the MPlayer developers. You could try SMPlayer which is a much superior front-end for MPlayer. I attach a screenshot to demonstrate how easy it is to alter mouse-binfings with theis program.

All the best,

Andrew

---

### Post by vinutux on 2009-10-28
> **andrew.46 said:**
> Hi evar,

gmplayer is pretty much abandoned by the MPlayer developers. You could try SMPlayer which is a much superior front-end for MPlayer. I attach a screenshot to demonstrate how easy it is to alter mouse-binfings with theis program.

All the best,

Andrew

and there is gnome-mplayer also```
sudo apt-get install gnome-mplayer
```

---

