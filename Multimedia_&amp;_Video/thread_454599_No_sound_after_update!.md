---
title: "No sound after update!"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by herbster on 2007-05-25
I just updated today, can't recall which files exactly but something linux headers and such, if there's a way to paste what the update consisted of please tell and I will.

I rebooted as it requested a system restart, and my volume icon is muted and amarok couldn't find any audio drivers at startup. So I click on the volume icon I get this:

```
No volume control GStreamer plugins and/or devices found.
```

Then I went to system>prefs>sound prefs and when I hit the TEST button on sound playback, it gave me this dialog box:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

What the heck happened? This is tickin' me off, please help!

---

### Post by aicrono on 2007-05-25
I as well have no sound after rebooting after updating. When I go to my sound preferences and click the test button, it just hangs with about 25% of the bar full. When I click the volume icon in the task bar, it detects my sound card just fine and nothing is muted that I didn't have muted already.

I recall having the same problem a few updates back and running the command: 
```
sudo gpasswd -a <your username> audio
```

to get it working again, which it did. This time the command did nothing at all.

---

### Post by herbster on 2007-05-25
I have it fully restored, I simply went and reinstalled alsa via the method in post 1 of this HowTo:

[http://ubuntuforums.org/showthread.php?t=400268](http://ubuntuforums.org/showthread.php?t=400268)

---

### Post by jwelsh405 on 2007-05-25
Aicrono try this

Look i am not a linux guru but i struggled with this problem for a while and what fixed it was this.

Edit the alsa-base file:
*Enter without quotation marks*
"sudo pico /etc/modprobe.d/alsa-base"

and add this to the bottom of the file *without quotation marks*
"options snd-hda-intel model=3stack"

I am running a toshiba A135-S4447 laptop and had no sound for three days until I found this somewhere can't remember where though.

---

### Post by aicrono on 2007-05-26
jwelsh405,

I had tried your fix first, as it seemed pretty quick and easy to undo if it didn't. Sadly, it didn't work for myself, and if I am interpreting the  "options snd-hda-intel model=3stack" part correctly, I think that is for the on-board Intel sound card, which I do have, but do not use (I am currently using a Chaintech AV-710 sound card, which had worked out of the box in Dapper). I greatly appreciate your help though, it's why I really like this community. Everyone here is nice and tries to help each other out. :)


herbster,

I went ahead and followed the how to and got the latest ALSA driver and what-not. Everything installed smoothly, except according to the how to, all you had to do was just start using whatever had sound. This was not the case for me, as soon as I finished installing, the sound did not work. I restarted my computer, and upon reaching the log-in screen, I heard the usual noises and alas my sound problem is fixed. I greatly appreciate your help too. :) If you are anything like me, you can't stand silence for long. :lol:

---

### Post by jwelsh405 on 2007-05-26
aicrono

To much amazement i did not think it would work for you seeing how this is linux. And since i have been using linux it seems as if no two computers are the same. However i must admit that i would rather deal with a linux problem then a windows problem

---

### Post by herbster on 2007-05-26
aicrono,

Yup, you had to reboot, that's all. Same for me. I'm really glad you have your sound working, enjoy it! :)

---

