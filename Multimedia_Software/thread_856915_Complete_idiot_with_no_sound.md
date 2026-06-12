---
title: "Complete idiot with no sound"
date: 2008-07-11
forum: Multimedia Software
---

### Post by NozirohLacitrev on 2008-07-11
I was told how Ubuntu is "the God of the OS's" so I decided to dual boot it with my XP, everything went great and I got it.
The only problem I have is that sound doesn't work.
Now I understand there are 1000s of posts like these on here but none of the solutions on the countless threads I've seen work, either they don't work or I have no idea what they're talking about because I am **completely useless** when it comes to programming, so please help out a complete idiot by making what you say as mind numbingly simple as possible.
I will provide ANY information needed to help.

---

### Post by Truedream on 2008-07-12
look for your sound card [here]("http://www.alsa-project.org/main/index.php/Matrix:Main") and follow the guide.

PS; use ```
lspci -v
``` to find out your chipset.

---

### Post by NozirohLacitrev on 2008-07-12
My card is an Intel ICH7, now what guide do you speak of?

---

### Post by Truedream on 2008-07-12
[here]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel")

there are two different ICH7's listed. click on the details next to the right one.

---

### Post by NozirohLacitrev on 2008-07-12
It says I already have those drivers, also that tut is inexplicably hard to follow.

---

### Post by Truedream on 2008-07-12
Open up a terminal and type;

```
sudo apt-get install libasound2 alsa-utils alsa-oss
```


once that is done type:

```
alsamixer
```

see if you get a screen like this one.

---

### Post by NozirohLacitrev on 2008-07-12
I have that menu just not that many controls, only two.

---

### Post by Truedream on 2008-07-12
well that means you've drivers installed. go to preferences ---> sound and select different drivers from drop down menu and test. keep the ones that works. hope that helps.

PS: make sure volume is not muted :D

---

### Post by NozirohLacitrev on 2008-07-12
None of them work. :\

---

### Post by Truedream on 2008-07-12
can you post the screenshot of "alsamixer" just like I did?

---

### Post by NozirohLacitrev on 2008-07-12
Here.

---

### Post by NozirohLacitrev on 2008-07-12
Sorry for double posting but I really need sound back, anyone have any more ideas?

---

### Post by BLTicklemonster on 2008-07-13
I saw the name of this thread and thought right off that someone had figured out how to make my first wife shut up, and had to come see how they did it, but I see it's something totally non related. I'm sorry.

---

### Post by Yellow Pasque on 2008-07-13
Try this: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

If that fails, try the OSS4 howto in my sig.

---

### Post by NozirohLacitrev on 2008-07-13
Thanks for the reply Temujin.

I tried both, Alsa didn't work, but OSS seemed to install fine.
When I played music, the ossxmix said sound was being detected, but there was no sound from the speakers, now after clicking something (I forgot what) the ossxmix wont open any more.

---

### Post by BLTicklemonster on 2008-07-13
You've been here, right

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

?

---

### Post by Vadi on 2008-07-13
I hope something works out for you. This unusual.

---

### Post by NozirohLacitrev on 2008-07-15
> **BLTicklemonster said:**
> You've been here, right

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

?

What exactly on the page are you trying to point out?

---

### Post by BLTicklemonster on 2008-07-15
The whole page in general, actually.

See if you may see something that you think may help?

Try going to System, Preferences, Sound, and in the window that shows up, try first of all changing the Default Mixer Tracks _D_evice settings, then click the test button on Sound Events. See if any configuration there helps you.

It may be a simple (you probably don't want to hear this) as going out and buying an inexpensive audio card, but I really think this problem is just something overlooked.

So there's no way your sound is turned off in the bios, I presume? I would assume that, but you seem like a nice fellow, and I don't want to go making an *** out of you and me out here in public...

Also, if you double click on the sound icon on the tool bar, then go to File, Change Device, check each one, and see which one comes up with the most options under Edit, Preferences, then go try different settings in Preferences and see if any of them work.

---

### Post by BLTicklemonster on 2008-07-15
Also:

[http://ubuntuforums.org/showthread.php?t=838852](http://ubuntuforums.org/showthread.php?t=838852) look at the audio portion of the post.

or

[http://ubuntuforums.org/showthread.php?t=497595](http://ubuntuforums.org/showthread.php?t=497595)

---

### Post by NozirohLacitrev on 2008-07-15
I tried rebuilding Alsa and now when I put Autodetect and hit test, it gives me this:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

What is that all about?

---

### Post by Truedream on 2008-07-15
Sorry for the late reply. I had the same kind of problem when i was using 7.10. in my case my chipset wasn't supported and had to recompile the sound drivers.

Your case is really weird because you seem to have the drivers installed and everything. why don't you reinstall Ubuntu 8.04?

PS; like i said before double check your speakers if they're connected/working/mute or not.

---

### Post by NozirohLacitrev on 2008-07-16
I'm gonna try reinstalling.

Exactly what partitions do I delete in the installer? They all have weird names like dev/sb or something, I really don't want to accidentally delete my Window partition, I need it.

---

### Post by NozirohLacitrev on 2008-07-16
Sorry for double post, but now I can't boot XP, it just comes up with the blue screen and restarts.

It was working fine before, but after explorer.exe stopped responding one time and I restarted, it hasn't booted since.

---

### Post by Truedream on 2008-07-17
Partitions are basically different hard drives within a hard drive. For example if you've 250 GB hard drive you can separate it into different partitions of variable sizes so that you can dual boot.

Boot into your Ubuntu Live CD and startup terminal.
Type

```
sudo fdisk -l
```

and post your output.

---

### Post by Cone on 2008-07-17
> **NozirohLacitrev said:**
> Sorry for double post, but now I can't boot XP, it just comes up with the blue screen and restarts.

It was working fine before, but after explorer.exe stopped responding one time and I restarted, it hasn't booted since.

..did you play with any partitioning prior to this happening? o-o

---

### Post by Duranxl on 2008-07-17
are your speakers connected?:p

---

