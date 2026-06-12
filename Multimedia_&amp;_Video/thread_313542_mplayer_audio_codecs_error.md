---
title: "mplayer audio codecs error"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by adc on 2006-12-06
I'm a Ububtu Edgy user.
Whenever I want to play a video file in MPlayer I get the followin error:

"Requested audio codec family
[mp3] (afm=mp3lib) not available.
Enable it at compilation."

The sound is played but this error really bugs me since it always appears.

Does anyone know how to fix this?

---

### Post by tbroderick on 2006-12-06
Try changing the video driver in preferences.

---

### Post by adc on 2006-12-06
And how exactly will this help me? Aren't the video preferences for the video output channel?

Anyway I tried (maybe the problem was there). Changing the video preferences only didn't help with the error (it still appeared) it just lead sometimes to another error related to not being able to open the video output channel.

So the question still remains. Is there a way to fix this?

---

### Post by tbroderick on 2006-12-06
> **adc said:**
> And how exactly will this help me? Aren't the video preferences for the video output channel?


Well, did you try changing the Video Codec family? Try changing it to FFmpeg.

---

### Post by adc on 2006-12-06
I changed the Video Codec family and did nothing. After I changed the Audio Codec family to FFmpeg the error stopped appearing.

Thanks.

---

### Post by Handssolow on 2006-12-06
Sorry, can I have a bit more information where you change the codecs. I'm having similar errors to those that others have reported. I often get errors with Mplayer despite removing and reinstalling with Automatix. The names don't help either -Totem/Mplayer/Movie Player/Mplayer Movie Player, they sound like all the same program.

one of the errors I get includes the line “[mp3] (afm=mp3lib) not available”

another error I get is similar to one I've just cut and pasted from another post,"couldn't resolve name for AF_INET6"

Sometimes two or three other windows appear. Sometimes the video will play once but attempting to repeat the video leads errors with extra windows appearing.

Can I make a start to understand why I'm getting these errors and their possible solutions?

---

### Post by shin on 2006-12-06
Had this problem. For me it was just damaged mplayer package. Check for updates. If there aren't any do this:
```

echo "deb http://download.tuxfamily.org/3v1deb/ edgy 3v1n0" | sudo tee -a /etc/apt/sources.list
```

Very nice repo (with flash 9 and some other packages) - I use mplayer from this one and now it's working like a charm. Havent changed anything since I had exactly the same problem like you with edgy eft packages.

---

### Post by Handssolow on 2006-12-06
Thanks for your reply shin but please forgive my concerns, my knowledge of Ubuntu is still rather limited.

Attempting to download from the tuxfamily I get various warnings in the terminal about there not being a public key, also thinking about using synaptic to reinstall Mplayer, there's a further message about it not being authenticated.

What do others think about these warnings and should I wait until the official updated packages are available?

---

### Post by shin on 2006-12-06
My bad. Forgot about gpg key.

Type this:
```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

Now again
```
sudo apt-get update
```

There should be no errors now.
So
```
sudo apt-get upgrade
```
After that update your mplayer and you may safely update anything else. I used Trevino's debs for quite a while now and I assure you - they do you no harm ;)

---

### Post by ubageek on 2006-12-07
[COLOR="navy"]*I'm a new xubuntu user and i had the same problem as 'adc' and the replys he recieved realy helped me with my MPlayer.*[/COLOR]

---

### Post by lucky_chouhan on 2006-12-07
hi shin i try your steps but i am get this.

root@root-desktop:/home/lakhan# sudo apt-get upgrade
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing timidity (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

](*,) ](*,)

---

