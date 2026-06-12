---
title: "Rhythmbox Won't Import Music from Server"
date: 2008-11-15
forum: Multimedia Software
---

### Post by Derspankster on 2008-11-15
I recently did a fresh install of Ubuntu 8.10 on my Acer Aspire laptop.  I now find that Rhythmbox cannot access my music files on my Ubuntu media server.  I can browse to the files OK and Totem will play them but Rhythmbox cannot import them into a playlist.  My path is correct.  This worked just fine in 8.04.

Anyone have a fix for this??

---

### Post by Derspankster on 2008-11-16
I am the ONLY one having an issue with 8.10 like this? Hard to believe.

---

### Post by Laroko on 2008-11-17
No, you're not alone ;o)

Same thing here.

Rhythmbox can neither import, nor play mp3-files living on smb-shares, there's always "Can't open resource for reading".

If I copy them locally, they can be imported and played without problems.

Totem has no problem to play these "remote-files". :o(

Anyone any ideas?

As I experienced no problems with smb in general, I'm not sure about the correlation of this problem and the problem described here:
[http://ubuntuforums.org/showthread.php?t=978798&highlight=rhythmbox+smb+-read+resource](http://ubuntuforums.org/showthread.php?t=978798&highlight=rhythmbox+smb+-read+resource)

lg,
Laroko

---

### Post by Derspankster on 2008-11-17
Thanks for responding.  It's getting a little irritating that with every new version something new is broken.  

The laptop that I installed 8.10 always suffered with overheating problems with 8.04 (cause unknown) but that's no longer an issue with a fresh install of 8.10.  But, of course, now Rhythmbox is broken.

---

### Post by StewD on 2008-11-29
Hi,

Anyone had any luck resolving this? I've just upgraded to 8.10 and am experiencing the same problem - Highly frustrating!!

Stew

---

### Post by StewD on 2008-11-29
Hi

I've virtually resolved this via a workaround. I'm running Ubuntu 8.10, and my music is on a Linux server connected via Samba:

**Option One**
Mount a new directory that will "point" to the music directory on the server: 
```

sudo mkdir /media/music
sudo mount -t smbfs //linuxserver/linuxmusic /media/music -o username=[replace with your linux server username],password=[replace with your password]

```
where linuxserver is the name of your Linux server, and linuxmusic is the directory all your music is in.

**However** you would have to run the above "mount" command every time you log on. So...

**Option Two**
```
sudo gedit /etc/fstab
```
add the following line
```
//linuxserver/linuxmusic /media/music smbfs username=[replace with your linux server username],password=[replace with your password]
```

where linuxserver is the name of your Linux server, and linuxmusic is the directory all your music is in.

then to mount the drive without rebooting: 

```
sudo mount -a
```

**Using the mounted drive**
Once you have used one of the above options to mount your drive, you should then be able to go to /media/music in your file browser and see all your music.

You can then 
- Go into RhythmBox 
- Select all tracks, 
- Right click and select Remove
- Go to Edit, Preferences and select the "music" tab.
- Change "Music Files" are placed in to read "file:///media/music"
- Click "Watch my Library for new files" 
- press close

**PROBLEM PROBLEM PROBLEM :confused:**
Even when I have amended /etc/fstab, /media/music is not populated when I reboot. I have to go back into terminal and run "sudo mount -a" everytime. 

Why?? Can anyone identify what I've done wrong?

Thanks,

Stewart

---

### Post by Derspankster on 2008-11-30
I haven't figured it out yet either.  At least totem will play music via samba and interestingly, so can VLC.  I could never open network files with VLC before 8.10 although it always worked fine in Windows and on a Mac.

With every new release it now seems that something new is broken. That's the main reason I've stuck with 8.04 on my desktop.  Everything's working. I'm running 8.10 on an old laptop that I use as a test bed.

---

### Post by dfme on 2009-01-28
> **Derspankster said:**
> I am the ONLY one having an issue with 8.10 like this? Hard to believe.

no... you're not:
:arrow: [http://www.uluga.ubuntuforums.org/showthread.php?p=6625603](http://www.uluga.ubuntuforums.org/showthread.php?p=6625603)

i hope a solution is found soon

---

### Post by dfme on 2009-03-06
it's a known issue in launchpad for quite some time now :-k
[https://bugs.launchpad.net/rhythmbox/+bug/273294](https://bugs.launchpad.net/rhythmbox/+bug/273294)
wonder why it's taking so long to fix this. this used to work for me before ubuntu 8.04 :???:

---

### Post by Derspankster on 2009-06-14
Well, I checked this out again today and it's still not resolved. Rhythmbox is essentially useless to me as I have all my music on my server. For now, I mount my Music folder and use VLC to select and play my music.

A bit OT but Brasero is also a bit of a pain in that I have to copy any music locally to burn a CD.  

Still, I'm not moving away from Ubuntu any time soon.

---

### Post by acemonvw on 2010-04-29
I've used the Beta 2 10.04 Ubuntu Lynx and I still have problems with Rhythm box over a server.  I decided to just make a hackintosh instead because it does a much better job with server music files.  Also, every time I wanted to listen to my music (which I found I could do with Exaile), it would be a pain in the butt going to the server folder and connecting.  With osx and windows, I just had to open itunes and play the music.  Too many steps is just not fun.  Perhaps they fixed this issue with the LTS release of 10.04, but I doubt it if the problem has persisted this long.

---

### Post by Gaki on 2010-05-02
I'm in the same boat with 10.04 final.  I can see the SMB network share in Rhythmbox, but no music is visible in it (all my music is .flac).  I try to scan it, set my default folder to the one on the share ... nada.  I can't even disconnect the share because the option is visible, but non-clickable.

Exaile, on the other hand, works like a champ, so I just swapped apps in the meantime.  Too bad because I like the way Rhythmbox handles inet radio.

---

### Post by romuald_geo on 2010-05-06
Me too.Similar issue, and I started a new thread about it

---

### Post by romuald_geo on 2010-05-25
Hi guys! On launchpad some users built a .deb so you can download it and install. For me worked like a charm :) Here's a link 
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/273294](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/273294)

---

### Post by canplaythegame on 2010-06-05
i installed updates this morning and it now imports files and flders
they were proposed updates 
so i had to change something so it looked for proposed updates
i cant remember where i changed it atm

daniel d

---

### Post by SoFl W on 2010-06-05
I complained about this a few weeks ago and there was no answer, other music players work fine.  I think there were updates to Rhythmbox aound June 5th but they didn't seem to solve the problem.

I didn't get an error, it just wouldn't import the files.

---

### Post by canplaythegame on 2010-06-05
look for proposed updates they came up this morning 

daniel d

---

### Post by SoFl W on 2010-06-05
I will wait until the new version comes out.  I use it on my laptop and I am not in a rush.

---

