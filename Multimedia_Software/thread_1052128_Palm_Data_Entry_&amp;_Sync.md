---
title: "Palm Data Entry &amp; Sync"
date: 2009-01-27
forum: Multimedia Software
---

### Post by Lorac1949 on 2009-01-27
I've been able to sync the data from my Palm Tungsten E to my Dell Inspiron 1520. However, is there software or a module available so that I can make entries into Contacts, for example, from my Inspiron and then sync that into the Palm? It would make life sooooo much easier vs. pecking in all that info one character at a time on the Palm.

---

### Post by rafaelsousa on 2009-01-27
Try

```
sudo modprobe visor
```

and see what happens.

---

### Post by rafaelsousa on 2009-01-27
Ops...

There's a software... 

Try:

#JPilot
#gnome-pilot

---

### Post by Lorac1949 on 2009-01-27
I have gnome-pilot installed, but how do I open a window to view data? The only thing that comes up is the "PalmOS Devices" in the System Preference drop-down list. It doesn't open a window where I can edit/add, etc. information. It only opens the sync feature.

> **rafaelsousa said:**
> Ops...

There's a software... 

Try:

#JPilot
#gnome-pilot

---

### Post by rafaelsousa on 2009-01-28
Did you tried with JPilot?

It has features for sync Contacts, among other things.

There's one thing you must know... Try to hit sync button in your palm first, wait a second or two, before hitting any sync button in desktop. Pilot-link based applications, expects that the device already requested sync. They don't "listen" for connectins. 

I have experienced this kind of trouble when I was developing an Sync Application based in pilot-link (JPilot uses pilot-link for connections).

---

### Post by Linuxdork on 2009-01-28
If you're looking for something like Palm Desktop you'll want to use Evolution mail.  You can set it up to sync with your Palm and you can see all of your contacts and calendar events there.  This is what I do with my Palm T|X.  I hope this helps.

---

### Post by Lorac1949 on 2009-01-28
Thank you. I'm looking for an ubuntu version of the Palm Desktop. I'm currently using Thunderbird and Lightning for E-mail, contacts and calendar. Sounds like it would be worth using Evolution; even if I only use the calendar and contacts portions.

> **Linuxdork said:**
> If you're looking for something like Palm Desktop you'll want to use Evolution mail.  You can set it up to sync with your Palm and you can see all of your contacts and calendar events there.  This is what I do with my Palm T|X.  I hope this helps.

---

### Post by Linuxdork on 2009-01-28
I concur.  It works nicely and I haven't had any problems.  Let me know if you need any help setting it up.

---

### Post by Lorac1949 on 2009-01-28
I've had no problem setting it up; however...

1) When I did my first sync, Evolution duplicated all the phone numbers. Where I had 2 numbers for one contact, I now have 4, etc.

2) The categories [e.g. business. personal, etc.] didn't transfer from the Palm to Evolution.

3) When I tried to sync a third time, the sync failed. I've tried a couple times, but no go. Will look at settings after dinner and try again.

If you've run across these problems and know of solutions, I'd appreciate a shout back. Thanks.

> **Linuxdork said:**
> I concur.  It works nicely and I haven't had any problems.  Let me know if you need any help setting it up.

---

