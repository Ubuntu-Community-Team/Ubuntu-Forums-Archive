---
title: "Ubuntu iPod Genius"
date: 2010-11-17
forum: Multimedia Software
---

### Post by mosa01 on 2010-11-17
Hi,
I own an iPod classic and i was wondering if I could enable the Genius-function (which I really liked ;)). With Windows / iTunes, that worked perfectly, but now Rhythmbox even deleted my old genius DB, so i can't even use genius with the songs i already had on my ipod.

Is there any way to use genius with ubuntu? I don't care about the Program which realizes that, the main point is that it should work ;)

Thanks a lot,
mosa01

---

### Post by Bradj47 on 2010-11-17
Might wanna try libimobiledevice:
[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

I don't know if it has the feature you're looking for but it seems to be the most functionable iPod/iPhone program out there.

---

### Post by mosa01 on 2010-11-18
Hey Bradj47,
Thanks for your help but that wasn't what I was looking for. I can fill my iPod with Music and Stuff, but there is a special function called genius which makes automatically playlists of songs similar to the one youre listening to. 
Of course, this information isn't calculated on the iPod, it's saved in the DB with the songs i guess.
But Rhythmbox doesn't store this information on the ipod, so genius doesn't work.
Is there anybody who uses ubuntu and genius on his ipod?
Thanks,
mosa01

---

### Post by Chronon on 2010-11-18
Never tried it but found this by googling:
[quote=http://wiki.answers.com/Q/What_software_for_Linux_supports_iPod_Nano's_Genius_feature]MIRAGE!!!! It's a Banshee extension. Good luck!
[/quote]

---

### Post by udey.rishi on 2011-04-07
Hey mosa01!!! Finally I've found someone with the same problem I've been facing from the last 2 yrs!! I so much wanted to shift over to Ubuntu, but I love Genius way too much! So I could never leave Windows...Have you found a way yet??? Please let me know, I'm desperately looking for a solution....Ubuntu 11.04 + iPod with genius would be heaven!!! You can even mail me at [email]udey.rishi@gmail.com[/email]

Please if you've found a solution, do let me know...

---

### Post by nothingspecial on 2011-04-07
guayadeque music player does this using lastfm

You play a track and it makes a playlist based on similar artists from your library.

I don't really do playlists but I'm sure it would work with an ipod.

I don't think the version from the official repos has ipod support, you would have to do it from the guayadeque ppa

```
sudo add-apt-repository ppa:anonbeat/guayadeque
sudo apt-get update
sudo apt-get install guayadeque-svn
```



That is a development version, there may be bugs in updates. Just pop over here [http://guayadeque.org/forums/index.php?p=/docs](http://guayadeque.org/forums/index.php?p=/docs) and report them and they are usually fixed within a day.

---

