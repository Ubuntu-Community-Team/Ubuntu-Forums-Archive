---
title: "Cant copy to SD card"
date: 2009-01-16
forum: Multimedia Software
---

### Post by Dumbestcrayon on 2009-01-16
I'm trying to copy some music to my SD card. 
I tried drag and drop, the window closes and it reopens the SD card. 

I tried to drag and drop with nautilus and I got the same thing.

I tried it with terminal and I got this..

```
brett@brett-laptop:~$ sudo cp -r /media/Stuff/Music/A\ Static\ Lullaby/And\ Don\'t\ Forget\ to\ Breathe/ /media/disk/My\ Documents/My\ Music/
cp: cannot create regular file `/media/disk/My Documents/My Music/And Don\'t Forget to Breathe/A Sip of Wine Chased With Cyanide.mp3': Input/output error
cp: cannot create regular file `/media/disk/My Documents/My Music/And Don\'t Forget to Breathe/04-a_static_lullaby-lipgloss_and_letdown-fnt.mp3': Input/output error
cp: cannot create regular file `/media/disk/My Documents/My Music/And Don\'t Forget to Breathe/03-a_static_lullaby-withered-fnt.mp3': Input/output error
cp: cannot create regular file `/media/disk/My Documents/My Music/And Don\'t Forget to Breathe/09-a_static_lullaby-annunciate_while_you_masticate-fnt.mp3': Input/output error
cp: cannot create regular file `/media/disk/My Documents/My Music/And Don\'t Forget to Breathe/08-a_static_lullaby-a_song_for_a_broken_heart-fnt.mp3': Input/output error
 
```


I believe my SD card is fat16 because its a mini card for my cell phone.

---

### Post by mc4man on 2009-01-16
none withstanding any issues with copying to the sd card itself, I find when copying or using odd locations with spaces, symbols,  ect. it's best to forget the \'s and just use ' or "
You bound to make typing mistakes like you did. (look at Don\'t

What makes life really easy is to install nautilus-open-terminal (then restart.

That way you can right click on an odd named directory -> open in terminal and get the proper path to copy and paste for your command, script, ect.

Ex.
r. click on dir.
> 
doug@doug-desktop:/media/music/Funk Brothers/Standing In The Shadows Of Motown (Soundtrack)$

Copy the path and add '...' where needed into a new terminal (or ctrl+c from existing
> cp -R /media/music/'Funk Brothers/Standing In The Shadows Of Motown (Soundtrack)' /home/doug/


copies perfectly.

---

### Post by Dumbestcrayon on 2009-01-16
I've tried that. The reason is because with I started to type it I hit TAB and let the terminal complete it. I tried both ways. Theres no typing error because while typing I would start the name of the directory and press TAB and the terminal would finish it therefore the terminal knew what I was talking about and knows that it is a directory.

---

### Post by mc4man on 2009-01-16
Found a SD card that I've never used, was preformatted vfat (fat16). Didn't have any issues dragging and dropping files into it. (properties -> mount options on the volume are the same as any vfat flash device 

Did notice there is a little lock tab on the side, but if locked you get should get a warning about mounted read only.

Even added some files from vista and didn't 'safely remove', still no problems using in ubuntu, acts just like a usb flash drive.

Wouldn't know if your phone has created an issue, seems possible.

---

### Post by Dumbestcrayon on 2009-01-16
There's nothing wrong with my phone or the card. I can do it all with a friends computer using windows. I would just do it there but I don't feel like calling my friend every time I want to copy something to my SD card. The tab is not locked either. Thats the first thing I checked. Don't know if this is relevant but I have a Tmobile Dash with Windows Mobile 6.1 kavana. Everything is working perfectly fine on my phone and when I use it in a Windows computer. I do not own a computer with Windows. I just don't understand what Input/Output error is.

---

### Post by Dumbestcrayon on 2009-01-18
Any more ideas?

---

