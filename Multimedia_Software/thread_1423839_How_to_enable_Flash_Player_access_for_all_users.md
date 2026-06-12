---
title: "How to enable Flash Player access for all users?"
date: 2010-03-07
forum: Multimedia Software
---

### Post by monarchheels on 2010-03-07
I'm using UNR (9.10) and flash player works fine for me, the admin, but not for the other user on the computer. 
when the other users goes to YouTube, he gets a message that Flash Player is not installed or Javascript is turned off. I checked and JavaScript is on.

Any suggestions?
Thanks!

---

### Post by monarchheels on 2010-03-13
Anyone have any ideas?
Thanks

---

### Post by Yellow Pasque on 2010-03-13
Find libflashplayer.so on your system and check its permissions. Should be:

```
cd <directory where you have libflashplayer>
sudo chmod 755 libflashplayer.so
```

---

### Post by monarchheels on 2010-05-13
Turns out I had to install Flash player for the other user on this system- it doesn't install across profiles?

I just gave that user admin rights, logged on as him, ran 

[FONT=Courier New]sudo apt-get install ubuntu-restricted-extras

[FONT=Arial]and now he's good to go. then I turned off his admin rights.[/FONT]
[/FONT]

---

### Post by mnavasuk on 2010-05-17
> **Temüjin said:**
> Find libflashplayer.so on your system and check its permissions. Should be:

```
cd <directory where you have libflashplayer>
sudo chmod 755 libflashplayer.so
```

That did it for me. I'm using Lucid 32 bit. Thanks.

---

