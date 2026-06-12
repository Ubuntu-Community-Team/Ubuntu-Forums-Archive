---
title: "I broke it (started with that upgrade)"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by wordsmythe on 2006-08-22
So before I found the thread on how to roll back the upgrade and everything, I must have panicked (spent a lot of half-remembered time adding and deleting X11 stuff in aptitude, for sure), because now I have rolled back to 2, but still have these symptoms going on:

[LIST]
[*]X won't start, and says there's no monitors
[*]bash now won't give me job control at login (from the command prompt)
[*]when i tell it to reboot, it shows a xubuntu screen
[/LIST]

So I really don't want to have to scrap the entire Ubuntu install.  Is there any way I can avoid that?

I've been ](*,)  for a good 5 hours now, and would really like to take a lunch break, but that looks like a pretty high hope now...

Oh, and I've got an ATI card.  So my guess is that I shouldn't then be installing the nvidia stuff late like TSEliot said (i didn't do that yet anyway, because that seemed like something I could do from within the GUI, which I never got back to).  I've done the dpkg-reconfigure xserver-xorg too.  No dice.

---

### Post by wordsmythe on 2006-08-22
Can someone just tell me what needs to be installed for X to run on a PC with an ATI card?

---

### Post by Scythe!? on 2006-08-23
Try this to get X back.
sudo apt-get update
sudo apt-get upgrade
OR if upgrade doesnt work,
sudo apt-get install xserver-xorg-core


To get ubuntu picture back on boot, I'm not 100% sure on this though
sudo apt-get remove xubuntu-artwork-usplash
If that doesn't get your ubuntu splash back try
suao apt-get install usplash

---

### Post by tseliot on 2006-08-23
read this thread:
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

### Post by wordsmythe on 2006-08-23
Yeah, I'd read that thread, TS (nice name, btw).  Thanks, though.

I think I've got it running now.

But was there an update in the past day or two (or over the weekend) that broke MySQL or PHP?  Because my phpbb is dead now.  :frown: 

Man, I'm having some good luck these days!

---

