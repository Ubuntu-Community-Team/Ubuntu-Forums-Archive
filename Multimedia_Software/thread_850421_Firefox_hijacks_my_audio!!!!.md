---
title: "Firefox hijacks my audio!!!!"
date: 2008-07-05
forum: Multimedia Software
---

### Post by animaniac on 2008-07-05
Sometimes when i have a radio stream going in rhythmbox, and pause the playback to browse a website with integrated content, then try to resume playback and no sound.

Rhythmbox behaves as if the playback is working fine.

I have to turnoff Firefox and i think i have had to restart rhythmbox to get playback working again.

Any idea to the cause:confused:

---

### Post by scragar on 2008-07-05
almost certainly pulseaudio, kill pulse audio and see if the problem still occurs:
```
killall pulseaudio
```

---

### Post by dje on 2008-07-05
try:
```
sudo apt-get install libflashsupport
```

---

### Post by animaniac on 2008-07-05
if its pulsaudio, is it safe to uninstall. or does anything depend on it.

dje: ill try yours first:)

---

### Post by scragar on 2008-07-05
it's perfectly safe to kill pulse audio, it is used to allow sound to be piped through virtual desktops, it is known to cause things to be unable to use audio though if another program is using it at the same time(which would explain how firefox could steal your audio). you cannot uninstall pulse audio, but it can be disabled long term if required.

---

### Post by animaniac on 2008-07-05
after having installed libflashsupport i havn't been able to recreate the error, so 75% possibility of it being fixed since i have not tried too many things yet.

also @ scragar: cool, post the long term way of dissabling it, just incase i need it:). I assume since these things seem to be known i have no need of filing a bug report.

Thanks both of you.

edit: also why have pulseaudio by default? id understand having it in the studio version of ubuntu, but it seems rather pointless on the normal version.

---

### Post by scragar on 2008-07-05
it's expected to not be as buggy as it can be at the moment before the end of hardy's life(3 years), so it's included because otherwise it would proberly never make it in, and ofcourse without people using it to file bugs it wouldn't know of some of the stranger bugs it offers.

easiest method of disabling it is to simply add a new startup program to kill it (System>Preferences>Sessions - add - type: **killall pulseaudio** in as command).


After looking at the ubuntu wiki it does look like pulse audio has problems with firefox(although I havn't read the details yet, just scaned the page quickly), which may be related.

---

### Post by magiver on 2008-07-05
libflashsupport did the trick for me.
Thank you dude

---

### Post by shamusl on 2008-07-09
> **scragar said:**
> it's expected to not be as buggy as it can be at the moment before the end of hardy's life(3 years), so it's included because otherwise it would proberly never make it in, and ofcourse without people using it to file bugs it wouldn't know of some of the stranger bugs it offers.

easiest method of disabling it is to simply add a new startup program to kill it (System>Preferences>Sessions - add - type: **killall pulseaudio** in as command).


After looking at the ubuntu wiki it does look like pulse audio has problems with firefox(although I havn't read the details yet, just scaned the page quickly), which may be related.

Thanks, this did the trick.

---

### Post by leachyboy2001 on 2008-08-01
Kill the pulse processes worked for me too! Thanks

---

### Post by ming0 on 2008-10-06
> **scragar said:**
> 
easiest method of disabling it is to simply add a new startup program to kill it (System>Preferences>Sessions - add - type: **killall pulseaudio** in as command).


Cool, worked for me -- thanks! (btw, is there a "thanks" feature on these forums, or does the software just scan for the word "thanks" in the text?)

---

### Post by scragar on 2008-10-06
> **ming0 said:**
> Cool, worked for me -- thanks! (btw, is there a "thanks" feature on these forums, or does the software just scan for the word "thanks" in the text?)

little medal style button on bottom right of each post.

---

### Post by techflat on 2008-10-17
> **dje said:**
> try:
```
sudo apt-get install libflashsupport
```

Thanks, this did the trick for me. Niiiice!

---

### Post by minimals on 2008-10-18
sudo apt-get install libflashsupport****
thats good solution.....thnks **dje**

---

### Post by Michal77 on 2009-05-18
In Juanty there is no more libflashsupport. Instead of it, it has to be installed flashplugin-nonfree-extrasound

```
sudo aptitude install flashplugin-nonfree-extrasound
```

It works for me.
M.

---

