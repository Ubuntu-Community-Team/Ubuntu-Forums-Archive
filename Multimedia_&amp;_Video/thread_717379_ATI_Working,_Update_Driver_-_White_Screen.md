---
title: "ATI Working, Update Driver - White Screen"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by Farenheit on 2008-03-07
I have searched the forums for fixes of ATI drivers producing a white screen, but haven't seen any definitive answers.  Here's the rundown:

I have a Radeon 2900 Pro (Athlon X2 running Ubuntu 7.10 32bit, 2GB RAM, dual-booting with Vista 64) and I followed some guides to install the AIGLX driver.  For awhile I couldn't get it to work, but I loaded Envy and that got the driver to install.  I knew it was working because I was able to play UT2004 and Enemy Territory: Quake Wars rather nicely.  As driver updates came out, I installed them with the standard ATI installer and they worked.  Then Catalyst 8.2 came out and I installed those.  Rebooted, and I got to the login screen.  When I logged in, I saw the desktop briefly, then it changes to a white screen.  I can hit CTRL-ALT-F1 and get to the terminal, but I have no idea how to get back to the desktop (startx wouldn't work).  One thing I noticed is that when there is a white screen, the mouse cursor is there.  I had compiz running before, and had multple desktops running.  I can hold CTRL-ALT then hold the left mouse and drag, and I can see the desktop cube rotating (although its VERY slow).  When I let go, back to the white screen.  I saw some ideas about disabling compiz and enabling metacity, but I didn't see how I could do that from the terminal.  

Are there any ideas/fixes out there?  Like I said, I was up and running with AIGLX before, not sure why it decided to break this time.  Thanks all!

---

### Post by empthollow on 2008-03-07
first, to get back to X you press CTRL + ALT + F7.  Not sure about the white screen although i have run into that problem with beryl and xgl back when ati didn't support aiglx - which was not too long ago actually... there was an export LD_LIBRARY_PATH command i used to fix the error but i had to run it manually from metacity and then start beryl manually and i could not get it to run automatically from sessions or .profile.  In my case it was fixed by enabling different beryl repositories.  i got aiglx to work on my x200, i had to blacklist the fglrx module - this means it doesn't use the ubuntu packaged fglrx- so that it would see my newly compiled fglrx module correctly.  it did that in the /etc/default/linux-restricted-modules-common file.  my aiglx worked but it has issues with open gl and the newest at driver it seemed to get worse because google-earth would not display images.  i downgraded to the ati-7.11 driver i downloaded previously.  hope this is useful.

---

### Post by Farenheit on 2008-03-07
Ah, I think that was it!  When I reinstalled the driver, I think it removed fglrx from being blacklisted.  I re-added it, and now I'm back in.  Thanks!

---

### Post by markoloka on 2008-03-07
There's also brand new driver. 8.3 try it.

---

### Post by empthollow on 2008-03-07
Cool, glad it worked for ya! by the way, that 8.3 driver is the one i had  to downgrade from because i couldn't see the world on google-earth.  Not saying it won't work for you, just a heads up.

---

