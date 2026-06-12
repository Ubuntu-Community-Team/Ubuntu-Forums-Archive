---
title: "raise, lower and mute volume commands"
date: 2009-05-06
forum: Multimedia Software
---

### Post by forum4programs on 2009-05-06
[SOLVED]

Hi,

I need to add three (sound) commands in "applications shortcuts"-tab of "keyboard" to be able to control the volume.

"Application Shortcuts"-tab locate in "Applications" => "Settings" => "Xfce 4 Settings Manager" => "Keyboard" => "Application Shortcuts"-tab.


Three commands :

1. command to raise volume
2. command to lower volume
3. command to mute volume

Thanks in advance.

using xubuntu 9.04 on laptop

---

### Post by glotz on 2009-05-06
Which music player?

---

### Post by forum4programs on 2009-05-06
> **glotz said:**
> Which music player?

I believe any kind video/audio player won't works. I can't even control volume by keyboard's button on youtube =(

I think those three buttons (button to lower, raise and mute volume) are not mapped to mentioned commands.


The original (equal to default) setting. - see a picture below
[IMG]http://img220.imageshack.us/img220/4022/originalr.png[/IMG]



I believe it should look somehow like below picture.
[IMG]http://img217.imageshack.us/img217/5024/shouldbe.png[/IMG]


Each time I want to control the volume, I have to use "xfce4-mixer" and use touch-pad to raise, lower or mute the volume. It is not very convenient.  - very important part, why I didn't say it earlier? ^.^;

---

### Post by glotz on 2009-05-07
I can't find any documentation on xfce4-mixer commands but have you taken a look at **amixer**?```
man amixer
```

---

### Post by forum4programs on 2009-05-07
> **glotz said:**
> I can't find any documentation on xfce4-mixer commands but have you taken a look at **amixer**?```
man amixer
```

Yeah!!! Thanks glotz!! amixer is the solution!

amixer controls xfce4-mixer nicely with command-line.



> **forum4programs said:**
> 
Three commands :

1. command to raise volume
2. command to lower volume
3. command to mute volume

Thanks in advance.

using xubuntu 9.04 on laptop

If somebody don't like reading the manual (man amixer). I will show you my commands:

1. command to raise volume  => "amixer set Master playback 3dB-"
2. command to lower volume  => "amixer set Master playback 3dB+"
3. command to mute volume   => "amixer set Master playback 0%"

Command with postfix, in this case '-' and '+' just lower or raise the volume. In my case, I raise or lower by 3dB.

---

### Post by glotz on 2009-05-07
Glad to help and thanks for posting the solution too! ;)

---

### Post by ObsidianOps on 2009-05-31
First off, I'd like to thank everyone in this thread for helping me out when I was stuck on this same problem. However, I'd also like to add one thing.

I think a better command to bind to the mute key would be
"amixer set Master toggle"
This will toggle on an off the mute, so you can bring the volume back up by hitting the mute key again, not just with Volume up.

Cheers!

---

### Post by calraith on 2009-05-31
I just made a howto for [controlling the volume in Xubuntu with key bindings]("http://ubuntuforums.org/showthread.php?t=1174798").  Here's a screenshot of the end result.

[IMG]http://headcandy.org/rojo/volume_ctl_screenshot.jpg[/IMG]

---

### Post by henriquemaia on 2009-12-22
> **ObsidianOps said:**
> First off, I'd like to thank everyone in this thread for helping me out when I was stuck on this same problem. However, I'd also like to add one thing.

I think a better command to bind to the mute key would be
"amixer set Master toggle"
This will toggle on an off the mute, so you can bring the volume back up by hitting the mute key again, not just with Volume up.

Cheers!

Thanks so much for this, I was trying to use xbindkeys in lxde and I was missing the mute command. That did the trick!

---

### Post by capleton on 2010-03-17
Thanks for this, Perfect!  Here's what my setup looks like now

[IMG]http://i44.tinypic.com/2hdmr08.png[/IMG]

---

