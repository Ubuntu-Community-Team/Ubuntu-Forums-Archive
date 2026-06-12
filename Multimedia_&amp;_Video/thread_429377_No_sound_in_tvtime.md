---
title: "No sound in tvtime"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by mojoman on 2007-05-01
Hi,

I got an Asus TV/Tune-card (Asus My Cinema P7131 Dual) and it seem to be detected alright by Feisty (I'm running Xubuntu 64-bit). I installed TVtime and I got a good connection and it finds the channels but there is no sound. I've googled around and surfed this forum and there are some info on this and it's fixed by entering this command in the terminal:

```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,0
```

Sure enough, that turns the sound on (from what I gather, it arecord plays the sound and pipes it through sox to the alsa driver which then plays it in the integrated soundcard. I found it on this [page:]("http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa") 

Now, it cannot seriously be meant that I should have to enter this command everytime I want to have sound while watching TV and surely there must be a fix for this. Any ideas, anyone?

Thanks
/mojoman

---

### Post by mojoman on 2007-05-10
*bump*

Anyone? I discovered that I hade to do the same when I used the radio (the card got a fm tuner too).

---

### Post by hmann on 2007-05-10
if you found a solution please let me know..
have the exact same problem!

i'll let you know if i come up with anything

---

### Post by fenian on 2007-05-10
Add that line to to your rc.local file and it should run when you boot the computer.To do this open a terminal and enter...

> sudo gedit /etc/rc.local

paste that line (arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,0) before the last line (exit 0) save the file and exit.Restart and see if it worked.

---

### Post by fenian on 2007-05-10
Another Idea would be to change the startup command of TVTime itself.To do this right click the applications menu and choose edit menus , double click tvtime and under command replace what is there with...
> 
tvtime | arecord D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,0

---

### Post by mojoman on 2007-05-11
I played around with the idea to have the commando auto-run in startup too but I noticed that it conflict with other applications that uses ALSA, for example xine and mplayer won't run when the commando runs. Anyway, I didn't wan't to leave any stone unturned so I did try it and I'm afraid it doesn't work. I'll have a look at the menu option as well (I'll have to edit the menu, it's somewhat more work in Xfce then in Gnome I think), that might be a way to go but it would presuppose that the arecord/sox commando quits when tvtime quits, otherwise I wouyld have to find the process and kill it manually, which a bit too much, isn't it?

Is it possible to have a commando run by starting an application and have it stoped at the same time as one exits the application?

Thanks
/mojoman

---

### Post by RayVad on 2007-07-22
[http://ubuntuforums.org/showthread.php?t=476263&highlight=tvtime+sound]("http://ubuntuforums.org/showthread.php?t=476263&highlight=tvtime+sound")

---

### Post by kopinux on 2007-07-22
have you checked, the sound manager? i think the line-out is muted by default.

---

### Post by mojoman on 2007-08-26
A bit late for me to reply but I have really had my hands full for the last month and have barly turned my computer on. Still, the problem persists so I'll try to kick some life into this thread.

Kopinux: I already tried setting the line out to max sound level but it makes no difference.

RayVad: bttv and bt878 modules are not loaded at all in my kernel, only tuner. However, are these modules really requiered for my card? Because I can get the sound working without them using arecord and sox. Nevertheless, I did try removing tuner and then adding all three modules in that order but the sound still doesn't work.

Any other ideas on this?

---

### Post by OisinT on 2008-01-29
> **mojoman said:**
> Hi,

I got an Asus TV/Tune-card (Asus My Cinema P7131 Dual) and it seem to be detected alright by Feisty (I'm running Xubuntu 64-bit). I installed TVtime and I got a good connection and it finds the channels but there is no sound. I've googled around and surfed this forum and there are some info on this and it's fixed by entering this command in the terminal:

```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,0
```

Sure enough, that turns the sound on (from what I gather, it arecord plays the sound and pipes it through sox to the alsa driver which then plays it in the integrated soundcard. I found it on this [page:]("http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa") 

Now, it cannot seriously be meant that I should have to enter this command everytime I want to have sound while watching TV and surely there must be a fix for this. Any ideas, anyone?

Thanks
/mojoman


hey i have the exact same problem and none of the other fixes listed on this page or the linked page seem to work.
Did you ever get this fixed?

---

### Post by mojoman on 2008-01-31
> **OisinT said:**
> hey i have the exact same problem and none of the other fixes listed on this page or the linked page seem to work.
Did you ever get this fixed?

No, I didn't. I've tried everything I could think of but I'm considering compiling a custom kernel to see if that might do the trick. If I ever find a solution, I'll post it.

---

### Post by OisinT on 2008-04-26
this fix no longer seems to work in Hardy.

---

