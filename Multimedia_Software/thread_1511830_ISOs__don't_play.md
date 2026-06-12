---
title: "ISOs  don't play"
date: 2010-06-17
forum: Multimedia Software
---

### Post by rtz2rbbl on 2010-06-17
Ok, so I back up all my movies to my computer once I get them. Some of them rip and play just fine as ISO images, but some will get to the menu, and when I click play they just die. I've tried playing them through VLC and even tried to mount the ISO image through GMount and still no luck. I rip with Brasero or K3B. Any help would be appreciated greatly. I'm on the move a lot and don't want to have to carry all my DVDs with me in order to able to watch them. 

I have already istalled libdvdread4.

---

### Post by cchhrriiss121212 on 2010-06-17
Try opening them up in a terminal with vlc, and post what kind of error is displayed.

---

### Post by mkylman on 2010-06-17
Get Furius ISO Mount, I had a similar problem and that cleared it up. I *think* that it's in the repositories if you go into Synaptic and search there, but if not go here: [http://www.marcus-furius.com/?page_id=170]("http://www.marcus-furius.com/?page_id=170") There's instructions to get it there, as well as an overview of the software.

---

### Post by rtz2rbbl on 2010-06-18
Here are the errors that VLC gave me. I just took screenshots because I wasn't sure what all you'd need to see.

No luck with the furious ISO mounter, :(

---

### Post by cchhrriiss121212 on 2010-06-18
Could you try browsing the dvd and opening the video_ts.ifo in the video_ts folder?
Also try opening one of the .vob files.

Edit: Upon research (googling your error), it seems this is down to [copy protection]("http://bbs.archlinux.org/viewtopic.php?id=78124"). In other words this is an intentional feature put there by the movie production company, and it seems that the libdvdcss library for linux has not caught up yet.

Found possible solution [here]("http://forums.fedoraforum.org/showthread.php?p=1261819"):
> In the end i've found the trick. I post it in order to share it with other people experiencing the same difficulty. Encrypted dvds are css scrambled according to three main 'flavors': 'key' encryption, 'disc' encryption and 'chapter' encryption. Libdvdcss uses by default 'key' encryption, so if the dvd uses another type of encryption vlc, kaffeine & Co. will report an error complaining that it's not legal for you to use libdvdcss in your country (in spite of all the money spent for buying an original, brand new dvd movie ...)
The trick is to change the encryption method used by libdvdcss. For Kaffeine, for example, go 'Kaffeine-xine engine settings', then click the advanced tab, then browse to the combo box 'CSS encryption method' and then chose the one used by your 'ORIGINAL' dvd. 'The Lord of the Rings' for example, uses 'chapter' instead of 'key'.
If you have xine, then go to Setup>gui and chage your experience level to the highest setting. Then restart xine and go to Setup>media scroll down to find the CSS decyption method mentioned above.

---

### Post by rtz2rbbl on 2010-06-19
Xine can't play ISO images. Copyright laws suck.

---

### Post by cchhrriiss121212 on 2010-06-19
I forgot to quote an important part of the fix:
> Once applied, this setting is valid for everything using libdvdcss, so you will then be able to play encrypted dvds with all other players, not only kaffeine.

---

### Post by rtz2rbbl on 2010-06-20
Thats's still a negative. It just seems that it's a problem with the ISO image. I imagine I'll just have to wait till Linux CSS decrption catches up.

---

### Post by cchhrriiss121212 on 2010-06-20
Thats a shame. You could just use a program like handbrake to rip the movies to .avi or .mkv files, which would save you a bit of HD space.

---

### Post by rtz2rbbl on 2010-06-21
Yea, that's what I'm gonna end up doing. I'm just a bit of a snob I suppose you could say when it comes to video quality. There's not a screen in my house that isn't 1080p. Lol

---

