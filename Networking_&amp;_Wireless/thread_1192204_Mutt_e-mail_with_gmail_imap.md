---
title: "Mutt e-mail with gmail imap"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2009-06-19
I'm not sure if this is the right section to post this in, but I thought I'd give it a shot nevertheless. I just installed mutt, and I'm trying to get it working with my gmail imap. I found instructions with a short google search ("mutt imap gmail") but they talk about editing the .mutt/muttrc file and adding code to it. For the life of me, I can't find this file!
I updated my local search database, then tried using locate, but that didn't give me anything either. Does anyone know where I can find the settings for mutt? This is the link I was planning on using:

[http://juanjosec.blogspot.com/2007/11/using-mutt-for-gmail-via-imap.html](http://juanjosec.blogspot.com/2007/11/using-mutt-for-gmail-via-imap.html)

If you see a problem with these instructions or know a better way to set this up, I'd be grateful for that too. Thanks in advance!

---

### Post by andrew.46 on 2009-06-20
Hi pythonscript,

> **pythonscript said:**
> I'm not sure if this is the right section to post this in, but I thought I'd give it a shot nevertheless. I just installed mutt, and I'm trying to get it working with my gmail imap. I found instructions with a short google search ("mutt imap gmail") but they talk about editing the .mutt/muttrc file and adding code to it. For the life of me, I can't find this file!


This file can simply be created and mutt will find it. A more standard location would be:

```
touch $HOME/.muttrc
```

BTW don't forget to have read of the amazing Woodnotes:

```
wget http://therandymon.com/papers/using-mutt.pdf
```

And just consider before you launch in if you really want IMAP or whether POP3 over SSL would be enough:

[Howto] Use Mutt with Gmail
[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

Mind you, feel free to pillage the muttrc given in this guide and simply add in the IMAP stuff if that is the way you want to go :-).

All the best,

Andrew

---

### Post by pythonscript on 2009-09-06
Thanks for the tips! This really helped me.

---

