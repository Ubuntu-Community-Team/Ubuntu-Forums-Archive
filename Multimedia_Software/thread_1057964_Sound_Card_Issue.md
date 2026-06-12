---
title: "Sound Card Issue"
date: 2009-02-02
forum: Multimedia Software
---

### Post by djpenn612 on 2009-02-02
I'm running Ubuntu and WinXP Pro. In XP the PC recognizes my soundcard, I can play .mp3s and watch videos. In Ubuntu, if I try to open an .mp3 file or video file it will make me do a FORCE QUIT after about fifteen seconds. It wont even recognize the file. I disabled the motherboard's soundcard is the BIOS, installed the drivers for the NEW soundcard (in XP). 

I'm new to Linux so I'm just not sure how to get Ubuntu to find and recognize my new soundcard....

---

### Post by khelben1979 on 2009-02-02
Run the alsa command with root permissions from a text console and choose your sound card.

Then adjust the volume with the alsamixer command.

```
sudo alsaconf
```
then
```
sudo alsamixer
```

Reboot to see if it works.

---

### Post by djpenn612 on 2009-02-02
Thanks for the help. I went to the Creative website (I have a SoundBlaster) and downloaded the drivers I needed and found some threads on here that will hopefully do the trick.


[http://ubuntuforums.org/showthread.php?t=720831](http://ubuntuforums.org/showthread.php?t=720831)

^^^for the help


[B]Well, I can't seem to find the driver for the Soundblaster X-Fi Soundcard anymore...the one provided in the link no longer exists.

Anyone know where I can get one?[/B]

---

### Post by khelben1979 on 2009-02-03
[Look at this page]("http://connect.creativelabs.com/linux/default.aspx").

( I tried the swedish mirror on this place myself and saw that the latest file was released in november 2008 )

---

