---
title: "nvidia-settings (crashes)"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by Corbin on 2007-08-25
Hey, I have downloaded the package (nvidia-settings) from the package manger. it loads up and works fine. and it allows me to adjust my color (the main reason why i need it). But after i rebot I get an x server error... (I am at a loss) 

Any help would be sweet.

-Thanks

Im running Ubuntu feisty Fawn. on a P4.

---

### Post by tseliot on 2007-08-25
Did you install the legacy driver? Only in such case it would be right to install nvidia-settings.

nvidia-glx and nvidia-glx-new conflict with nvidia-settings because nvidia-settings is already included in the said packages

---

### Post by Corbin on 2007-08-25
Well as i installed the (nvidia-settings) i saw it remove a couple of nvidia things (cant remember exactly what it was tho. 

So what do you suggest i do?

-Thanks

---

### Post by Corbin on 2007-08-25
o wait, i got it (thanks allot man)

only problem now is that its not saving my setting changes in the (nvidia-settings)


EDIT: Er.... well it does SAVE the settings. It just does not activate them on start up. 
I have to go into the terminal and type nvidia-settings. and then it works...

---

### Post by Corbin on 2007-08-25
Alrighty... well now i have it starting up every time (WOOT) I just went into sessions and then added a new "start up program" But now every time i start up that boxes opens... anyway i can run that process with out that box opening up every time i restart..

---

### Post by tseliot on 2007-08-25
have a look at point 15 of the Problems Section of my guide:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#PROBLEMS_SECTION](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#PROBLEMS_SECTION)

and remove the new "start up program" you added

---

### Post by fenian on 2007-08-25
You could also just remove the new start up program and run nvidia settings with...

> gksudo nvidia-settings

make the ettings you want and click the save to xorg configuration file button.

---

