---
title: "internal speakers took over"
date: 2012-04-29
forum: Multimedia Software
---

### Post by lazylew on 2012-04-29
Installed Xubuntu 12.04 last night and sound came through the external speakers as expected.
Next day only the computer's internal speakers work.
I have done what's here: 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) 
for medibuntu, but it didn't change anything.
 
In the volume icon I tried several settings, but the one that I thought it should be (some card number and digital) is silent.
So only the first one, analog stereo output works, but on the wrong speakers.
  
EDIT: I also have an error about /usr/bin/blueman-applet
don't know if it's related to the problem?

---

### Post by Rodney9 on 2012-04-29
I turn the 'Built-in Audio' off in 'Configuration'

Rodney

---

### Post by lazylew on 2012-04-29
> **Rodney9 said:**
> I turn the 'Built-in Audio' off in 'Configuration'

Rodney
I would too, if only I saw where/how :-)

---

### Post by Rodney9 on 2012-04-29
Left click on the volume icon, select 'Sound Settings'

See screenshot

---

### Post by lazylew on 2012-04-29
> **Rodney9 said:**
> Left click on the volume icon, select 'Sound Settings'

See screenshotI only have one line there, where you have usb audio.
The external speakers btw are not with usb but a little plug (mini jack).[ATTACH]216826[/ATTACH]

---

### Post by shantiq on 2012-04-29
lazylew   install


> sudo apt-get install pavucontrol


then set it for your needs


like this  [of course for you not me:KS]

[ATTACH]216828[/ATTACH]

---

### Post by lazylew on 2012-04-29
> **shantiq said:**
> lazylew   install




then set it for your needs


like this  [of course for you not me:KS]

[ATTACH]216828[/ATTACH]already the latest version installed, it tells me.
I do notice that, after setting internal off in configuration, there's Dummy device now as in the screenshot.

---

### Post by lazylew on 2012-04-29
I found out what happened (still don't know why)
It's a Medion laptop with 2 outputs for audio, yesterday after the fresh install of Xubuntu the one on the right worked, but since this morning only the one on the left. 
So it was some hardware thing I don't see the logic of, but am glad it's solved :-)

---

