---
title: "Wifi connection before login to gnome"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by jeyros12 on 2009-03-23
Hi there!
I have another problem : I'd like to remote login (SSH) to my Ubuntu before starting a gnome session. However, Ubuntu won't connect to my wifi network before logging in a gnome session.

Is there some way to handle that?

Thanks

---

### Post by rolandrock on 2009-03-23
I think the wifi needs access to a keyring which is not unlocked until you enter username and passwd.

There are people who have published 'solutions' on this forum that involve setting auto login and having a blank default keyring password.  This leaves you computer very exposed and is highly unrecommended but does work.

Many on this forum don't like these things to be discussed in case niaive users blindly apply 'fixes' without understanding consequences.  In fact, I agree with them so please disregard everything I just wrote.

There are more discussions here:
[http://ubuntuforums.org/showthread.php?p=2776815](http://ubuntuforums.org/showthread.php?p=2776815)

---

### Post by jeyros12 on 2009-03-23
Thanks for taking the time to answer.

Actually I'm one of those people who want to know what they're doing and what risks they're taking.

So I was wondering, how exactly is the linux root password secure? Is it stored in a secure hash or as a key to decrypt something?
Of course i guess the keyring itself is encrypted?

Once a user is logged in, is the password stored in any form anywhere (including RAM)?

Is there a way to store only the WPA key in plain text somewhere and using it to automatically loggon on the wifi network? It seems to me more secure than letting the whole keyring with a blank password...

---

### Post by rolandrock on 2009-03-24
Hi, I hate putting up messages when I have nothing to say but just in case some guru is waiting to see if I reply... Sorry this is out of my league.  Though I suspect that any kind of manipulation like this would be deemed a security risk.

Cheers

---

