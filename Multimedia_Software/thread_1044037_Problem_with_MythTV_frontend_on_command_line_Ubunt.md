---
title: "Problem with MythTV frontend on command line Ubuntu"
date: 2009-01-19
forum: Multimedia Software
---

### Post by cliveb on 2009-01-19
I'm planning on building a MythTV frontend-only machine with minimal hardware. For the time being I'm experimenting with an old P4 desktop machine (HP dc7100). First off, I installed the standard Ubuntu 8.10 desktop OS, then the ubuntu-mythtv-frontend metapackage. Everything worked just fine.

I then rebuilt, this time installing the command line version of 8.10 from the Alternate install disk. That went fine, so I added the ubuntu-mythtv-frontend package. Upon reboot, the machine went into the first frontend config screen (where it asks you to choose a language), but did not respond to any keystrokes. I thought the keyboard simply wasn't working, but then hit Ctrl-C and sure enough that killed the mythtv frontend. It then popped up this message: "There was an error loading the theme Human" and "Can't open the file /usr/share/gdm/themes/Human/Human.xml".

After some googling, I found one comment saying that installing the ubuntu-artwork package would fix it, so I tried that but it made no difference. The only difference it did make was that after killing the non-responsive Myth frontend, the standard desktop login prompt appeared, but that too wouldn't respond to the keyboard (ie. I couldn't type in a user name).

Ctrl-Alt-F1 works fine and switches to a console. So the keyboard itself is clearly working. Any thoughts?

---

### Post by Exterminabur on 2009-01-28
Hi,

maybe you are missing some gnome lib that helps to handle the keyboard and/or the mouse.

I've seen last time I have installed the mythtv-desktop meta-package that it installed several libgnomekbd* packages. You should give it a try and see what's going on.

If it doesn't solve the issue, you had better go and see the liste of packages linked to the mythtv-desktop meta-package. The packages you need will be in the list.

I had the same issue than you, and after installing the meta-package, I rebooted and as previously I saw the mythtv setup wizzard but this time the keyboard worked :)

It's a solution for the impatients and a clue for the tweakers ;)

---

