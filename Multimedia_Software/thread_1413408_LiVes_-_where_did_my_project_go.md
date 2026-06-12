---
title: "LiVes - where did my project go?"
date: 2010-02-22
forum: Multimedia Software
---

### Post by afrodeity on 2010-02-22
Yesterday I spent a good couple of hours putting together a video. When I shut down, Lives flushed my entire project because it uses a tmp working directory and places it as default in tmp.

Today, I changed the working directory to Video, thinking this would be safe. Instead, the programme quit half-way through editing and I have now lost another good couple of hours.

is there any way of saving my project?

I can still see the .lay file but there doesn't seem to be any way of opening it.

---

### Post by no2498 on 2010-02-22
did you look in the trash bin or the cache files

---

### Post by afrodeity on 2010-02-22
Is Lives failware? It seems the programme is partially disabled and wants a kick in its butt to actually work. There is no way I can trust a video editing programme that deletes my work without bothering to ask me. I've tried opening via terminal

lives -set <name of set>

But no luck, it seems I have suffered yet another unwelcome purge of my files by a programme that looks great but hasn't got any safety features.

---

### Post by afrodeity on 2010-02-22
> **no2498 said:**
> did you look in the trash bin or the cache files

Nothing in trash. Where would the cache be?

---

### Post by lisati on 2010-02-22
This might sound obvious, but did you actually save the project before shutting down the program?

---

### Post by afrodeity on 2010-02-22
Yes I saved it, but it quit. Now I can't find any saved file except monday.lay and I can't seem to open it with lives. The "reload clip set" option in file menu doesn't seem to have any navigation buttons and entering in monday or monday.lay gets the following message:

```

==============================
Switched to clip monday.lay

failed.
Closed file /home/afrodeity/Videos/livestmp/Monday/layouts/monday.lay

==============================
Switched to empty clip
No clips were recovered for set (monday).

```

---

### Post by afrodeity on 2010-02-22
Well at least the developer is open about the problem, Appears to be the dreaded sigbert bug affecting version 1.18

Here is what Gabriel [email]salsaman@xs4all.nl[/email] had to say in email correspondence:
[I]
LiVES has had full crash protection for several versions now. However I
did find a bug in that if LiVES crashes with sigabrt rather than
sigsegv, the recovery process will not work. I am guessing that is what happened
in your case. This bug has been fixed in the latest version (1.2.0).

I quite understand, as a matter of fact I was also
affected by the same bug last week (which is how I discovered it, and I
lost quite a bit of work myself).

Hence I spent quite a lot of time on the new release testing the crash
recovery and making sure it works 100% of the time.


Since 1.2.0 was only released yesterday there are no ubuntu packages as
yet, the normal process is that it goes into debian first, then from there
into ubuntu. It's also likely that this version will only go into Lucid (I
have no control over that).

As an alternative, there will probably be ubuntu builds available on
getdeb.net in the next few days, I would advise you to keep checking
there.
[/I]


Which means we all two versions out of date in Karmic and suffering because of it. Let's campaign for better updates!!!!

---

### Post by afrodeity on 2010-02-22
[http://www.xs4all.nl/%7Esalsaman/lives/current/LiVES-1.2.0.tar.gz](http://www.xs4all.nl/%7Esalsaman/lives/current/LiVES-1.2.0.tar.gz)

---

