---
title: "Mythbuntu7.10: DVICO/Ultraview Lite Remote Control works but triggers wrong functions"
date: 2007-11-09
forum: Mythbuntu
---

### Post by Glenhawk on 2007-11-09
Hello all,
I have been using Gnome Ubuntu for about a year but tonight is my first go with Mythbuntu (I have previously spent 1-2 days with xubuntu).

I have my Ultraview (DVICO) Lite TV Tuner working, I have the sound working (which took some time and googleing), I even have the remote functioning but sadly it is performing incorrect functions. No matter how hard I google for an answer I can't seem to make sence of my specific problem.

When I use "irw" the remote is producing the correct data as per the buttons pressed but inside MythTV for example "channel up" actually performs a PageUp (instead of an Up).

I found the "lircrc" file and it has channel up listed as PageUp so I thought all I had to do was modify that file. Unfortunatley that did not seem to work.

I am sure it is a simple problem to fix but the Mythbuntu/XUbuntu interface is a little too alien for me (eg. can't use "locate").

Any assistance would be greatly appreciated,
Thanking you,
Glen

---

### Post by afljafa on 2007-11-09
You found the file under /home/mythtv/.mythtv/lircrc ?

---

### Post by Glenhawk on 2007-11-09
Yes, that is where I found it! It was tricky without locate (what is the mythbuntu equivalent?)

When I tried altering it all I did was modify the first "Channel Up" and "Channel Down" from the top of the file to say Up and Down instead of PageUp and PageDown. Then I restarted and tested the remote and there had been no change.

It could be that I was altering the wrong line, or entering the wrong data but when I didn't have any luck I restored the file from my backup and continued hunting for an answer.

---

### Post by afljafa on 2007-11-09
Perhaps. I think (from memory) that if you scroll down the file - you will see the same entries, but for different remotes. I too have the Dvicolite usb remote and I have been able to adjust the key mappings.

---

### Post by afljafa on 2007-11-09
Try changing the file under /home/~home/.mythtv/lircrc where ~home is the user you set up during the initial install.

---

### Post by Glenhawk on 2007-11-10
Thanks, I'll try it out when I get a chance.

---

