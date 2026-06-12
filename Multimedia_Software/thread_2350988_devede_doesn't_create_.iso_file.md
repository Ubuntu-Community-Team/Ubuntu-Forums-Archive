---
title: "devede doesn't create .iso file"
date: 2017-01-29
forum: Multimedia Software
---

### Post by poltr1 on 2017-01-29
I have an 85-minute-long .dvd file that was created with openshot.  I'm trying to create an .iso file using devede.  I added this as a title, and added chapter break points via the Properties tab.  I click on Menu Options to see if they have the correct information.  And I can preview the disc.  But when I click on Forward, and after prompting me for the location, I get the "Creating Disc..." window, but the project progress remains at 0%, as if it's stuck in a loop somewhere.  Are there any other settings that I may need to tweak?  (The process appears to still be running.)

---

### Post by mc4man on 2017-01-31
Would be useful if you post what package version of devede & what release version of mythubuntu. Also devede as a debug info in it's gui, what's it say. (at least here in 16.04 with devede 4.4.0-1

---

### Post by poltr1 on 2017-02-05
Yes, of course.

```

jim@goldchannel:~/Desktop$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
jim@goldchannel:~/Desktop$ uname -a
Linux goldchannel 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
jim@goldchannel:~/Desktop$ dpkg -l | grep devede
ii  devede                                      4.4.0-1                                            all          simple application to create Video DVDs

```

I'm not getting any stack dumps.  I can't find anything pertinent in /var/log.  After adding and selecting the .dvd file, and selecting the menu options, I select "Forward" (or the command button in the lower right corner)  and it appears to do nothing.  I don't even get a message saying it's on step 1/x.  Would a screen shot help?

Some past runs have encountered. a division by zero, and I've reported that to the developers.

---

### Post by poltr1 on 2017-02-28
Good news!  I fixed the problem I was having with this file.

1) I had chapter breaks past the one-hour mark listed in an incorrect format.  They need to be in h:mm:dd format.  Example: A chapter break at 67:14 should be listed as 1:07:14  I don't believe the documentation covers this.

2) On the menu page, the button for the title was too close to the bottom of the menu.  At a certain point, the title shifts to the right-arrow icon, regardless of what the title is set to.  I moved the title button up and to the right, so as to not cover up any text on the menu graphic.

I'm finally able to create the .iso file.

---

### Post by oldrocker99 on 2017-03-01
That's great! Thank you for using the Thread Tools to mark this thread as [SOLVED] so as to help other users.

---

