---
title: "nvidia legacy drivers - resolutions unavailable. help!?"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by ollysg on 2007-12-25
hey there! im pretty new to linux, im using ubuntu studio on my main studio pc. It all works fine, except for that since installing the legacy drivers for my geforce 2 ultra, no resolutions past 800x600 are available. Could someone possibly help me with some really easy to understand instructions for remedying this problem? (Yes, i am a really bad linux 'n00b'! :P)

---

### Post by logos34 on 2007-12-25
you used the restricted drivers manager or downloaded it from nvidia?

maybe you're using the nvidia-glx-legacy (-7185)

try 

sudo nvidia-glx-config enable

sudo nvidia-settings

> x server display config > set resolution $ refresh.  save changes to xorg.conf

---

### Post by ollysg on 2007-12-26
thanks for the reply, yes i used the restricted driver manager. I tried the commands you suggested, but on 'sudo nvidia-settings' the terminal returns 'command not found' or something along those lines. should i download a specific version of the nvidia-glx-legacy driver from nvidia?
thanks again!

---

### Post by logos34 on 2007-12-26
If you installed the driver using the restricted manager, it should have come with the nvidia-settings config app...Anything under >Applications>System tools  ?  It will give you a full range of res. and refresh rates.

If not, read[ this]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver")

or install the driver from the website using Envy 
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html).

---

### Post by ollysg on 2008-01-14
no, theres nothing under system in the applications menu.. im running studio, so i have the rt kernel, does that make much of a difference? i tried the settings suggested on the link to open the nvidia x-config, but it ended up with x failing to start and hanging on a caret, and a reinstall necessary.

I also tried envy, it worked fine but again no resolutions past 800x600 were available.

---

