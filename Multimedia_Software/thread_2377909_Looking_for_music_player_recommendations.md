---
title: "Looking for music player recommendations"
date: 2017-11-17
forum: Multimedia Software
---

### Post by socorob on 2017-11-17
I'm new to Ubuntu and am trying to find a music player with the same functionality I had in Windows. I used winamp with time restore, and  when I hit the power button on my pc, it would auto open winamp, pick a random song and start playing. I didn't have to turn on my monitor or anything. Is there a music player in Ubuntu that can:
1. Open soon as Ubuntu loads
2. Start playing when it opens
3. Allow me to queue songs.
That's what I'm looking for, It doesn't matter what it looks like, as it usually plays music and the monitor is off. Thanks in advance.

---

### Post by shantiq on 2017-11-18
[Audacious]("https://en.wikipedia.org/wiki/Audacious_%28software%29") is your best bet
also [xmms]("https://ubuntuforums.org/showthread.php?t=2348859") [more involved to install] but ace sound

here xmms running original Winamp skin on 16.04

[[IMG]https://s23.postimg.org/5sfjps713/image.png[/IMG]]("https://postimg.org/image/5sfjps713/")    audacious >> [[IMG]https://s20.postimg.org/io9pm30kp/image.png[/IMG]]("https://postimg.org/image/io9pm30kp/")


PS    to start Audacious automatically  

save this in a text editor

```
[Desktop Entry]
Type=Application
Exec=audacious -t
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_GB]=audacious


```

to /home/YOURNAME/.config/autostart


then it will open when you open the computer and start playing from where you last stopped the music   and you can cue trax


also excellent and you can do same to autostart
 [Clementine]("https://www.clementine-player.org/")

clementine -p   in autostart file


**PS2**   also you should use hotkey combination to --play-pause etc ...  i do that on mine and do not need to use monitor

  ```
-h, --help                Show command-line help
  -v, --version             Show version
  -p, --play                Start playback
  -u, --pause               Pause playback
  -t, --play-pause          Pause if playing, play otherwise
  -s, --stop                Stop playback
  -r, --rew                 Skip to previous song
  -f, --fwd                 Skip to next song
  -e, --enqueue             Add files to the playlist
  -E, --enqueue-to-temp     Add files to a temporary playlist
```


setting depends on your Desktop Environment ...    so simply look for hotkeys + name of your DE and set them ...   I use LXDE and know howto for that one if you need it

---

### Post by socorob on 2017-11-18
Thanks! I have it starting when Ubuntu opens, but for some reason it's not saving my music folder, which is located on a separate drive in the pc. It pulls up the list of all the songs, then gives an error that songs can't be found. On a side note, which one of the 2 do you prefer?

---

### Post by shantiq on 2017-11-18
i love both of them  [Audacious more recent and more formats but xmms has an incredible sound but involved to install
comes as default on Slackware tho]....    *the drive thing needs to be made automatically seen too*; so do >>


*modify my fstab to automount my internal HDD*



&#10122; ```
 mkdir /media/extradrive
```
&#10123; ```
sudo gedit /etc/fstab
```
&#10124; unmount the extradrive manually
&#10125; to find the full address of your drive run ```
sudo blkid
```   you will see the one you are seeking to add
 &#10126; add to the fstab   >>   IT WILL Look something like this
    ```
UUID=739e22d6-04f7-42f0-89e9-7e99603d63b3   /media/extradrive ext4     errors=remount-ro       0       1
```   
 &#10127; Then test the automounting by re-reading the fstab.

```
mount -a
```

Then see the mounted drives again.

```
df -h
```


now it should be there each time and therefore music files seen   [hope I got this right :]

---

### Post by socorob on 2017-11-18
Thanks for the help. I think I did something wrong. My music is in a ntfs drive named M1 in a folder called MUSIC. I think I did something wrong. Everything in your instructions seemed to run correctly, but maybe I put the entry into the fstab file incorrectly. This is what I put:

UUID=025CFA655CFA5341 	/media/M1	 ntfs	 errors=remount-ro	0	1

Did I do that correctly?

---

### Post by shantiq on 2017-11-18
ok was not entirely sure what to write in that line but if you read [here]("https://askubuntu.com/questions/769974/how-to-automatically-mount-2nd-internal-hard-drive")  also [here]("https://help.ubuntu.com/community/InstallingANewHardDrive") they suggest this line


```
UUID=0AED64E911A2FB1E [COLOR=#000000]/storage[/COLOR][COLOR=#b22222] ntfs defaults 0 2[/COLOR]
```

so in your case

```
UUID=025CFA655CFA5341 /media/M1 [COLOR=#b22222]ntfs defaults 0 2[/COLOR]
```


try that maybe it probably will fly this time ..


* after do not forget*

```
 mount -a 
```

Then see the mounted drives again.

```
 df -h
```

---

### Post by socorob on 2017-11-19
It works now! I'm not sure what made it work because I did 2 things at once.
i followed this command from your 2nd link with my info: [COLOR=#333333][FONT=UbuntuMono]  /dev/sdb1    /media/mynewdrive   vfat    defaults     0        2[/FONT][/COLOR]and I reloaded my music directory. I'm thinking it was probably the reloading of the music directory that did it after unmount ing and remounting. Thanks for the links, they helped me understand a little of what I was doing. You have been a great help, and made my weekend better!
[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]

---

### Post by shantiq on 2017-11-19
Excellent!  Those lines are very confusing :]  Happy Ubuntu-ing ...

---

