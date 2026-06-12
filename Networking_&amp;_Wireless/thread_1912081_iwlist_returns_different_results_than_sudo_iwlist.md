---
title: "iwlist returns different results than sudo iwlist"
date: 2012-01-20
forum: Networking &amp; Wireless
---

### Post by cdaringe on 2012-01-20
Hi all:

I'm trying to write an app and extract network data from iwlist scanning.  However, when I pass iwlist to the terminal for my wifi adapter, i only get the current connected network returned.  when i run iwlist scanning as root, i get all networks in view.

I want to be able to get all networks in view w/out root privileges.  or, have a way for my python app to pass a super user command and allow a pw entry.

let me know your thoughts!

Thanks,

-Chris

---

### Post by SteveDee on 2012-01-20
> **cdaringe said:**
> ...I want to be able to get all networks in view w/out root privileges.  or... pass a super user command and allow a pw entry.

I had this issue with the scanner I wrote using Gambas. Here are two possibilities (I'm sure there are more):-
 - modify the launcher for your app to include "gksu"
 - modifier sudoers file

So in my case I change the launcher command to:-
```

gksu /usr/bin/WifiScanner.gambas

```
...or modify sudoers, something like:-
```

%admin ALL = NOPASSWD: /usr/bin/WifiScanner.gambas

```

---

### Post by cdaringe on 2012-01-22
it's very bizarre.  it used to work--no joke! :$  thanks for the tip.  I'm interested to see how your method compares with mine.  willing to share your code?

---

### Post by SteveDee on 2012-01-22
> **cdaringe said:**
> ...willing to share your code?

The basic code is still here: [http://www.linuxbasic.net/applicationscode-snippets/](http://www.linuxbasic.net/applicationscode-snippets/)
...I'm happy to give you more.

Some notes on wifi channel selection here: [http://ubuntuforums.org/showthread.php?t=1768125&highlight=wifi](http://ubuntuforums.org/showthread.php?t=1768125&highlight=wifi)

---

### Post by SteveDee on 2012-01-25
> im interested in giving GAMBAs a go. i'm decent in vb6 & .net [they make ya learn it in school!], if they make GAMBAS cross-platform, boy howdy, that'd make my day.
Yeah, give Gambas a go! Back in the days when programming was a part of my day job, I use to enjoy VB.classic because you get results quickly (RAD) and the Help system was brilliant with examples for almost every command. VB.net Help I found much less friendly, as you have to sort through tons of stuff to find what you want. And as for C++...I'm glad all that's behind me!

Gambas is great for rapid design, and has a good IDE allowing you to quickly package your application as a DEB, ready to deploy to your Debian or 'Buntu system.

---

### Post by SteveDee on 2012-01-25
> **cdaringe said:**
> it's very bizarre.  it used to work--no joke!...

I've seen something similar. You are doing loads of stuff and use sudo for one operation, then you run another command and it seems to work without sudo because you still have elevated privileges.

---

