---
title: "VLC freezes system"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-04-11
VlC and the whole system freezes whenever I try to open music files in another partition: start VLC, click "play" and then "add". If I choose the folder in a different partition then the whole thing freezes and I have to do a hard reboot.

---

### Post by Harry33 on 2011-04-11
> **beew said:**
> VlC and the whole system freezes whenever I try to open music files in another partition: start VLC, click "play" and then "add". If I choose the folder in a different partition then the whole thing freezes and I have to do a hard reboot.

Nope, can't say I have experienced anything like that.
I have a separate home folder and VLC plays well both music (flac) and video (flv, mp4, wmv) files.
What file types are you trying to play, mp3?

---

### Post by beew on 2011-04-11
> **Harry33 said:**
> Nope, can't say I have experienced anything like that.
I have a separate home folder and VLC plays well both music (flac) and video (flv, mp4, wmv) files.
What file types are you trying to play, mp3?

It freezes before I choose the file to play. Just  play > Add and then freeze.

Possibly because the music file is on a different partition (the /home partition in Maverick since I have a dual boot) , but I have done this with Maverick many times (dual boot with Lucid, Windows  and another Maverick,--one install internallly and another in an external hard drive)

---

### Post by Harry33 on 2011-04-11
> **beew said:**
> It freezes before I choose the file to play. Just  play > Add and then freeze.
Possibly because the music file is on a different partition (the /home partition in Maverick since I have a dual boot) , but I have done this with Maverick many times (dual boot with Lucid, Windows  and another Maverick,--one install internallly and another in an external hard drive)

Well test this.

Open Nautilus.
Find the appropriate music file.
With mouse right-click, choose to open with VLC.

Does that wotk?

---

### Post by mc4man on 2011-04-11
No problem here either playing from other partition (mav
Does it do the same if going from Media > Open File ...

Is there any report created in /var/crash?

You could try 
vlc --ignore-config
if any better than 
vlc --reset-config --reset-plugins-cache

---

### Post by beew on 2011-04-11
> **Harry33 said:**
> Well test this.

Open Nautilus.
Find the appropriate music file.
With mouse right-click, choose to open with VLC.

Does that wotk?

That works. There is a problem only when I try to open files the way I described above.

---

### Post by beew on 2011-04-11
> **mc4man said:**
> No problem here either playing from other partition (mav
Does it do the same if going from Media > Open File ...

Is there any report created in /var/crash?

You could try 
vlc --ignore-config
if any better than 
vlc --reset-config --reset-plugins-cache

Will check the log later. I am away from the Natty machine now.

The freeze doesn't happen all the time, but maybe 8/10 of the times. I am not sure if it has anything to do with graphic driver (it is the open source ATI driver). Tested Natty on a different machine with the nouveau driver and it is much worse there, even firefox freezes randomly (Same Natty installed in an external drive and I plug it in different machines for testing. It was installed using a third machine so the playing field is even)

---

### Post by beew on 2011-04-11
Another thing is that the sound is really horrible when VLC starts (mp3). Skip to the next track or replay the same track then it sounds normal.

---

### Post by beew on 2011-04-12
> **mc4man said:**
> No problem here either playing from other partition (mav
Does it do the same if going from Media > Open File ...

Is there any report created in /var/crash?

You could try 
vlc --ignore-config
if any better than 
vlc --reset-config --reset-plugins-cache

Hi, 

vlc --ignore-config indeed seem to solve the problem.

Is there a way to make this permanent by setting an option in VLC?

Tried "vlc --reset-config --reset-plugins-cache" and got this error
> (process:7721): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.





What do these commands do and why they work?

Thanks.

---

### Post by beew on 2011-04-12
> **beew said:**
> Another thing is that the sound is really horrible when VLC starts (mp3). Skip to the next track or replay the same track then it sounds normal.

I think this has to do with the 2.6.38 kernel. Installed  Linux kernel 2.6.38-02063802 in Maverick and VLC exhibited the same behaviour. Uninstalling  2.6.38 from Mav and VLC was back to normal.

P.S. I deleted the vlc configuration file yesterday but the problem persisted so it wasn't because of that.

---

### Post by mc4man on 2011-04-12
vlc generally produces warnings from cli, but they are just that, not errors (and for most part can be  ignored

If you wanted to reset completely to as installed then delete the vlc folders in 
~/.config/
~/.cache/

What you may want to look at is the Privacy/Network interaction setting (see screen
The default is manual, 'as soon as track is added' is preferred for some things like audio cd's
See if one of those settings in causing any issue (remember to click save after changing
Edit:
I use the 'as soon as' option here, seems the best for me

---

### Post by MadCow108 on 2011-04-12
is it really freezing the system or just eating all memory until it swaps?
I have experienced the latter several times already but I cannot really reproduce it.

---

### Post by beew on 2011-04-12
> **MadCow108 said:**
> is it really freezing the system or just eating all memory until it swaps?
I have experienced the latter several times already but I cannot really reproduce it.

I can't tell. It freezes whenever I click ADD (see my first post). Maybe it will get out of it eventually and I just haven't waited long enough.

---

### Post by beew on 2011-04-12
I haven't done anything but there was an update for the bamfdaemon and after that the problem disappears. According to Synaptic the bamfdaemon matches desktop files to applications, this doesn't seem to be related to my issue here. I would appreciate it if someone can explain to me what happened. Thanks. 

I will mark the thread as "solved" even though I have no idea what goes on and have not done anything. :)

---

### Post by mc4man on 2011-04-12
the update concerned this bug, but if you look there are a ton of dups, many with different scenarios,(triggers),  one of those things that happens to some, not to others
Maybe that was what was happening to you
(I've never had such a crash here ( at least not  in quite some time

[https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/754225](https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/754225)

---

### Post by gyaneshwar on 2011-04-13
I have experienced similar problem.

Usually I double click on the file to open it and vlc works fine but sometimes it just eats memory. It managed to come to 3.2 (out of 4) GB RAM before I managed to kill the process. 
Problem is that it does not happen every time and also it happens if there is some error in the video.

I have ATI (X1650) on Natty on 2D settings.

Now, I have system monitor parallel to VLC so as soon as I see memory problem I kill VLC and restart it. After restart it works ok.

---

