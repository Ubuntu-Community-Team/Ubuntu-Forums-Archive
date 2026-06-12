---
title: "im so new to networking"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by fattyx on 2009-11-09
my network wont allow me to connect my desktop pc i do have wep security but i also have the password and all the information and so far its not letting me in at all i used a recently ubuntu installed laptop to see if i could use the wired option on my router and that didnt work either ive had to use a neighbors network just for a little bit of internet. so how can i setup my network to allow my ubuntu computers access

---

### Post by Iowan on 2009-11-10
Capital letters don't cost extra, and make the post MUCH easier to read ;)
The desktop PC is connected via wireless? Wireless drivers are still a bit tricky to get going sometimes and Karmic hasn't been too kind (so far).
Open a terminal (Applications>Accessories>Terminal) and enter:```
lshw -C network > listing.txt
``` Copy the file to floppy, USB stick, etc., and use your backup system to post it here.

---

### Post by Jeramiah on 2009-11-10
Doesn't Ubuntu come with basically plug n' play Ethernet networks? Mine has never done that. But hopefully the Pro's know. Also, are you sure your cable modem is all set up? I always think my browser messes up just from signal loss, or something. Usually I just have to reboot the modem...alot.

---

### Post by SteveHillier on 2009-11-10
> **fattyx said:**
> my network wont allow me to connect my desktop pc i do have wep security but i also have the password and all the information and so far its not letting me in at all i used a recently ubuntu installed laptop to see if i could use the wired option on my router and that didnt work either ive had to use a neighbors network just for a little bit of internet. so how can i setup my network to allow my ubuntu computers access
What release of Ubuntu?  What hardware?  I had a lot of problems with one install using the latest hardware because there was no support for the latest version of the LAN drivers.  It all worked ok once I installed some old LAN card that had been knocking around in the garage for a year or two.  The same problem occurred on that machine with Fedora as well as Ubuntu.
Has your router / modem worked OK with other machines?
The more information you can provide the more help you are likely to get.

---

