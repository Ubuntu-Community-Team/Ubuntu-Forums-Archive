---
title: "[SOLVED] Rhythmbox preferences not responding"
date: 2008-10-05
forum: Multimedia Software
---

### Post by soldersplash on 2008-10-05
I am having problems with Rhythmbox, mainly that I cannot adjust any preferences because Rhythbox stops responding when I open the preferences window. I have been using Ubuntu for a year or two but only recently installed hardy 32 bit.( I was using hardy 64 bit but found it a bit to much work for little apparent benefit in what I use the PC for).
I don't know where to start with this particular problem, can anyone point me in the right direction? I am quite familiar with the command line so if you need me to show you log files or edit conf files just tell me where to look and I'll be happy to go digging around!
Thanks in advance...

---

### Post by soldersplash on 2008-10-05
This problem is now intermittent. Having re-booted I can begin to change preferences but it still hangs after a few seconds...
I'm really scratching my head now...

Just checked System Monitor whilst Rhythmbox is hung and it thinks it's sleeping. Maybe that means Rhythmbox got bored waiting for something else to respond? Any ideas, anyone?

---

### Post by minky311 on 2008-10-05
Try starting rhythmbox from the terminal by typing rhythmbox and proceed to try and open edit->preferences. If it stops responding check the terminal to see if it displays any errors.

---

### Post by soldersplash on 2008-10-05
Hi minky311,
Thanks a lot for your suggestion, I should have thought to do that myself!
I have now run rhythmbox from terminal and gone into Edit-> Preferences. It has stopped responding straight away and (unfortunately) not sent any errors to the terminal.  :(

Thanks again for suggestion but I am still stuck!
Any more ideas? :)

---

### Post by soldersplash on 2008-10-06
Bump...

This is still not working for me. I want to finish ripping my CD's but need to sort the preferences first. Has no one else had this issue? I can't be the only one...
Or maybe I am just lucky ;)

---

### Post by minky311 on 2008-10-06
Well, you could try reinstalling rhythmbox by going to System->administration->synaptic package manager.
Or you could use a different music player like banshee.

---

### Post by soldersplash on 2008-10-07
Hello again minky311,
I'll try the re-install rb. Would rather not change to banshee as rb was working previously and I rather liked it.
Thanks for suggestion anyhow...
:)

---

### Post by soldersplash on 2008-10-07
minky311's suggestion to re-install seems to have worked. I did complete remove including config files (beware some files were left behind in ~.gnome2/rhythmbox/ and I manually removed then) then re-installed. I am now continuing to rip my CD collection. Thanks.
:guitar:

---

