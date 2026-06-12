---
title: "No Method works for Geforce4 420 Go on Feisty"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by marioquark on 2007-04-23
hi guys,
i've upgraded to ubuntu feisty, but the driver nvidia doesn't work...
i installed it correctly and greatly functioning on ubuntu breezy (i used envy and tseliot's guide!), but on feisty envy fails... (i downloaded the latest envy script, the one for feisty)

i tried these, but **no one worked**:
1. envy script
2. editing the xorg.conf file, as described in [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) in several modes (there are also specific settings for my **Geforce4 MX 420 Go**)
3. the non legacy nvidia driver
4. the legacy nvidia driver
5. the synaptics packages for nvidia

i had 1 of these 2 behaviours:
1. blinking black/console screen and then appears the dialogue (unable to load the nvidia module)
2. black screen, but i hear the greeting sound of ubuntu (it's not freezed, but i can't see anything)

any suggestion?

---

### Post by markthecarp on 2007-04-23
I got my nVidia GeForce4 420 Go working following this site...
[URL="http://www.nvnews.net/vbulletin/showthread.php?t=84773"]http://www.nvnews.net/vbulletin/showthread.php?t=84773
[/URL]

Posted to these forums here...
[http://ubuntuforums.org/showthread.php?t=417188]("http://ubuntuforums.org/showthread.php?t=417188")

Your mileage may vary.

hopefully helpful

-mark

---

### Post by marioquark on 2007-04-23
no, there's something else not working... thanks anyway.

now my Xorg.0.log says:
```
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

i think envy (for feisty) had not worked well... any suggestion?

---

### Post by nunomp on 2007-04-23
i am having problems with that graphic card also. on previews versions of ubuntu (and other distros) i had to install the driver manually, but it was ok. now it doesnt work. i tried Restricted Manager but it says "your hardware does not need any restricted drivers". *******.


keep in touch ..

---

### Post by marioquark on 2007-04-26
mmm, no solution found.
i'll try to clean the more is possible, then i'll try anvy again...

---

### Post by nunomp on 2007-04-26
i managed to make it work. i removed everything that had to do with nvidia and than manualy installed the driver, version 9631 (i believe it is the last one that works with this card). then (and because i'm using a laptop) i added to xorg.conf the line 

```
Option         "UseDisplayDevice" "DFP"
```

after "DefaultDepth". And it worked :)

---

### Post by marioquark on 2007-04-26
everything removed and driver installed successfully, but on the gdm start it doesn't find the nvidia kernel module. why? where is it located?

---

### Post by marioquark on 2007-04-30
solved!
[B]/lib/linux-restricted-modules/.nvidia_new_installed
had to be removed[/B]
thanx to hyperair...

---

### Post by DarinB on 2007-09-24
I have the same nvidia NV17 [GeForce4 MX 420]
i sometimes have my screen resolution go to 60Hz i then go to my system>administration >restricted drivers manager>i enable restricted drivers then without reboot it installs restricted drivers then  remove them then reboot for some reason it works. If i reboot with the enhanced drivers i can't reboot have to reinstall etc from the live cd. i also only have the nvidia common kernel installed. anything added and it wont boot.
i would love not to have to do this nonsense any more 
any suggestions?
Or maybe i have it good compared to others.

---

