---
title: "Rythmbox Music Player doesn't import folder"
date: 2009-12-01
forum: Multimedia Software
---

### Post by Wandels on 2009-12-01
It seems that my Rythmbox Music Player does not import my folder or files.

Music > Import file/folder

When i do this nothing gets added in my library.

---

### Post by trytenn on 2009-12-01
It sounds strange. Have u checked the read permission? Do u have it?
Try to run rhythmbox -d from the terminal, scan the music folder and see what the output is in the terminal. Post the output, I don't know if I can help u but maybe someone else.

---

### Post by Wandels on 2009-12-01
Sorry but I'm new to Ubuntu.
How exactly do i start  rhythmbox with Terminal?

```
wandels@wandels-desktop:~$ sudo rythmbox music player -d
[sudo] password for wandels: 
sudo: rythmbox: command not found
```

And how do I scan a folder?

---

### Post by trytenn on 2009-12-01
Okej welcome to ubuntu then! 
First I assume that u are using gnome or xubuntu. I don't know kde but my tips should help on that to. and I don't now how comfortable u are with computers so I will try to take as it basic as I can.
I remember now that the mp3 codec's isn't installed by default! Can u play mp3 files at all? To install codecs do this:
Press Alt + F2. paste in** gksudo software-properties-gtk** and enter. U will be prompted for password. There, check all the boxes and close (not all the boxes are required but I don't know with ones). Then alt and F2 again, paste** gnome-app-install **and search for ubuntu restricted extras in the window that comes up. Check the box and press apply changes. U should be able to play mp3 files now. If u can't play some media files search for gstreamer and look in the descriptions for the media type u want.

Okej now it's way past bedtime in sweden so good luck for now and write back the results!

Ps. to run rhythmbox from the terminal: **rhythmbox** and enter. Newer mind the -d, just for debug info. If u want to start a program in the terminal but u don't know exactly what the command is, guess the two or three first letters and press tab two times. Try it with **rh** and two tabs, it's very useful. Ds.

---

### Post by Wandels on 2009-12-02
[http://allerlei.aoltermassive.be/error1.png](http://allerlei.aoltermassive.be/error1.png)
I get an error when I try to run *gnome-app-install*

I looked in my Rhytmbox library and there are mp3 files present so I don't think that's the problem --> [http://allerlei.aoltermassive.be/mp3.png](http://allerlei.aoltermassive.be/mp3.png)


I runned the debug thing in Terminal and came out with this:
```
wandels@wandels-desktop:~$ rhythmbox -d
(12:13:26) [0x8203028] [rb_debug_init_match] rb-debug.c:213: Debugging enabled
(12:13:26) [0x8203028] [main] main.c:176: initializing Rhythmbox 0.12.5
(12:13:26) [0x8203028] [rb_threads_init] rb-util.c:388: GMutex isn't recursive
(12:13:26) [0x8203028] [main] main.c:184: going to create DBus object
(12:13:26) [0x8203028] [main] main.c:347: THE END

```

---

### Post by trytenn on 2009-12-02
> **Wandels said:**
> [http://allerlei.aoltermassive.be/error1.png](http://allerlei.aoltermassive.be/error1.png)
I get an error when I try to run *gnome-app-install*

Try this in a terminal ```
 sudo apt-get install ubuntu-restricted-extras 
```Any luck now with RB (rhythmbox)?> 
I looked in my Rhytmbox library and there are mp3 files present so I don't think that's the problem --> [http://allerlei.aoltermassive.be/mp3.png](http://allerlei.aoltermassive.be/mp3.png)


I runned the debug thing in Terminal and came out with this:
```
wandels@wandels-desktop:~$ rhythmbox -d
(12:13:26) [0x8203028] [rb_debug_init_match] rb-debug.c:213: Debugging enabled
(12:13:26) [0x8203028] [main] main.c:176: initializing Rhythmbox 0.12.5
(12:13:26) [0x8203028] [rb_threads_init] rb-util.c:388: GMutex isn't recursive
(12:13:26) [0x8203028] [main] main.c:184: going to create DBus object
(12:13:26) [0x8203028] [main] main.c:347: THE END

```After you opened upp rb, what exactly did u do here?

What happens when u add a map in the preferences? open the edit menu inside RB > references > go to the music tab. Copy the text inside the white box in the top. Press the Browse button, find the map u want to add and open. It will look something like this in the white box: **file:///home/YOUR_USERNAME/Elvis_Presley**
Then paste the old Music map and type **", **" with out quotes. Now it will look like this:
```
**file:///home/YOUR_USERNAME/Elvis_Presley, ****file:///home/YOUR_USERNAME/**
```I have never tried to add more than one map, but it worked for me. And it will of course look different for u, depending on witch maps u add. Select the Watch my library for changes box to! Any luck this time?
Also right click on the map u want  in the file browser (should be nautilus) > preferences > Permissions tab. Are u the owner of the map?

---

### Post by Wandels on 2009-12-05
> **trytenn said:**
> Try this in a terminal ```
 sudo apt-get install ubuntu-restricted-extras 
```

It is executed but doens't change anything.

> **trytenn said:**
> What happens when u add a map in the preferences?

So like this:
```
file:///media/LaCie/Music/Albums/Massive Attack - The Best Off,file:///media/LaCie/Music
```

This also doesn't change anything :-?

---

### Post by trytenn on 2009-12-05
Sorry I can't help. If u still have energy left: run rhythmbox -d and add the music-folder. It should print some error message in the console, copy that and send it here. 
Have u tried some other music player? Exaile and listen is similar to RB. Amarok is maybe the most popular one, but a little heavy if u have gnome.

---

### Post by manualqr on 2011-03-06
I hate to revive a long-dead thread, but I recently ran into this issue and realized that it probably isn't a Rhythmbox bug. Hopefully this will save others some pain in the future.

If you explicitly tell Rhythmbox to import a folder and notice no changes, try looking in the "Unknown" artist category. Chances are, your files just didn't have ID3 tag info and Rhythmbox just stuck them in some nondescript location in its database.

P.S: I haven't been on ubuntuforums in years. I learned a lot in the Programming discussion section here [under a couple different accounts, for reasons that I can't rightly remember now]. Anyways, its all had a pretty big impact on me. I'm going to major in Comp. Sci at a top-3 public university here in the U.S this coming fall. Although I'm using Arch now, I'm really glad Ubuntu was my first distro.

---

