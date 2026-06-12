---
title: "sound not working for other users"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by HokeyFry on 2006-12-17
i just made an account for my sister on this computer and for some reason i cant get sound to work with that username. it works fine in mine and on the login screen, but for her sessions she does not have sound. the volume properties wont even open, it says something along the lines that there are no devices available. any ideas? thanks in advance.

---

### Post by scrooge_74 on 2006-12-17
go to the users and groups and add her to the sound group that is probably what is going on

---

### Post by HokeyFry on 2006-12-17
which one is the sound group

---

### Post by scrooge_74 on 2006-12-17
The group is audio

---

### Post by HokeyFry on 2006-12-17
there is no group named audio

---

### Post by scrooge_74 on 2006-12-17
Ok, since I am on 6.06 and you on 6.10 maybe some names have change as 
I read somewhere else.  Look at what groups your user belongs to and then use those same groups with the other user.  (I did that when I was starting with Linux)

---

### Post by jjgalvez on 2006-12-17
to add a user to a group just run the next command:
```
sudo gpasswd -a USERNAME audio
```

of course instead of USERNAME you put your username and that's it ;) I hope it helps

Cheers

---

### Post by megabuff on 2006-12-30
hello

is this forum only for linux?

because i have a simpilar problem with XP

my main account has no souns and if i log onto the second accound it does :( 

i have checked all the setting i can think of the try and get it to run without success ](*,) 

any help much appreciated :D 

thanks Kev

---

### Post by scrooge_74 on 2006-12-30
sorry mate, after 9 months only Linux i don't remember to much....are you sure the account with the problems does not have the speakers mute or the sound card disable?

Just a few thoughts

---

### Post by megabuff on 2006-12-31
HEY thanks for uor reply.

when i check it says the device is working properly.

---

