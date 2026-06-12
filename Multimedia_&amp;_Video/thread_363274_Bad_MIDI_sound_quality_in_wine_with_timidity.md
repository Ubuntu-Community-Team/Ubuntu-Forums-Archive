---
title: "Bad MIDI sound quality in wine with timidity"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by old_toby on 2007-02-16
Hello

I'm running sibelius 4 in wine, and I got midi working with timidity. Though the sound is there, there's a lot of noise and crackling in the midi sound. If I save a score and run it normally with timidity, it's totally smooth. The Problem is the same if wine works with either alsa or oss drivers.

Does/did someone have the same problem? Is there a solution to it?

Old_Toby

---

### Post by sgx on 2007-02-17
I'd say you're lucky a windoze audio app works, so note and save all your wine system, in case a new one doesn't work as well. I have a few dozen vsti that work with wine, but only a few consistantly work across the last 6 or 7 wine releases, some of the rest come and go, and the newest wine is not necessarily best suited to what any one user needs...the task is so monumental, and the wine devs do a great service with the limited rescources available 

You might look into piping the sibelious output to a separate running timidity, or  testing the new windoze version of jack/qjackctl, and seeing
just where you can virtually patch your output to...I have tested neither method, but I  bet you'll  get something flowing!

also, two free good sounding GM soundfonts, Unison (small) and fluid (big) can be found to download, and can be used in timidity, fluidsynth/qsynth  etc, in case your sound source is misbehaving...google for tips installing and using soundfonts with linux midi as needed...hope this helps...

---

### Post by Macoa on 2007-03-11
> **old_toby said:**
> Hello

I'm running sibelius 4 in wine, and I got midi working with timidity. Though the sound is there, there's a lot of noise and crackling in the midi sound. If I save a score and run it normally with timidity, it's totally smooth. The Problem is the same if wine works with either alsa or oss drivers.

Does/did someone have the same problem? Is there a solution to it?

Old_Toby

Hi Old_toby,

I have been triying to install Sib 2/3/4 in wine for years, but no success at all.

Could you tell how you did it?

Thanks

---

### Post by old_toby on 2007-03-19
I just installed it normally, like I would do it in windows. I also tried it many times before, and it never worked, and when I saw in the appdb on winehq that it works, I installed it and I didn't have problems.

Just when you start for the first time, the registration form will be hidden behind the splash. I managed to move the form a bit, hit cancel, and then I clicked on "register" in the sibelius menu.

---

### Post by DrNutella on 2007-06-06
I had the very same problem and i solved it increasing the buffer and fragment size in 
/etc/default/timidity
by
```
sudo gedit /etc/default/timidity
```

You should change a line to make it looks something like this

```
TIM_ALSASEQPARAMS="-iA -B5,10 -Os1l -s 44100"

```
You have to play with B values (buffer size and fragments size) to find the best values for your system, 
Now vanbasco works flawlessly on my system!
hope it helps!
Gabriele

---

### Post by Jonasty on 2007-06-09
May I ask you with version of wine you use and wich version of vanbasco karaoke player

Greets Jonas

---

### Post by DrNutella on 2007-06-09
VanBasco is now playing :D and it's the 2.53...
Wine is version 0.9.33
Everything is working almost flawlessly: I have only a really small delay in the volume control (due to the increased size buffer) and occasionally i have some problem with the refresh of the lyrics window but since it's an occasional problem i just don't care! 
The overall sound quality is quite good since I installed fluid sound font!
I hope it helps.
Gabriele

---

### Post by fmonjaraz on 2007-07-30
Im using vanbasco with wine.  Everything seems to work alright except that I have no sound.  Any advice?

---

