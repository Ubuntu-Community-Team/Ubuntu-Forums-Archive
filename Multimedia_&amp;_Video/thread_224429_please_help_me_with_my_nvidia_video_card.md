---
title: "please help me with my nvidia video card"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by verthandi on 2006-07-27
hi! am a newbie to ubuntu and linux, hope you guys can help

my video card is a tornado geforce mx4000 64 mb. i looked for answers in the thread started by tseliot entitled "Post the way you got the Nvidia driver to work" but i couldn't find anyone whose card was the same as mine.

anyway, my problem is that the screen resolution cannot be set beyond 800x600. i thought it was a driver problem, consulted the Guide and did what it said. that is, i added repositories and ran the two commands. the first command (the "apt-get...")ran fine but when it came to the second command "sudo nvidia-glx-config enable", an error showed up. here it is verbatim:

"Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia."

what do i do next? any suggestions?

the wierd thing is that i have another identical pc with windows xp (same video card, same hard disk etc...). i installed ubuntu over it, and wierdly, the resolution can be maxed beyond 800 x 600. why did it happen? 

i apologize for the length of the post. :)

---

### Post by Ziox on 2006-07-28
its a short post, so don't apologize, and see if this can solve your problem:

sudo dpkg-reconfigure xserver-xorg

it'll rewrite your xorg.conf file to default...pay special attention to the part where it asks you for the resolution. Just choose the ones you like, or don't (do) choose all of them...you'll see what I mean...

post back if you have any more problem...

---

### Post by verthandi on 2006-07-28
thanks for the reply ziox

did what you said and i selected resolutions in excess of 800 x 600, still no change when i looked in the system/preferences/screen resolution. 
800 x 600 is still the maximum. is there something i didn't do?

oh, and ubuntu said that what i did was dangerous so it backed up the old config file. is that normal?

i don't get it, when i ran the command, i saw that Ubuntu identified my video card correctly so its supposed to work porperly but it doesn't.:confused:

---

### Post by verthandi on 2006-07-28
cancel that, all it needed was a restart

its working now, YAAAY!

thanks ziox! :D

---

### Post by Ziox on 2006-07-28
oo..nevermind that..glad that it works for you now...dont know how/if i helped, but still glad on problem is solved...:)

---

### Post by Ziox on 2006-07-28
i now know what i did wrong, i forgot to tell you to restart "X", next time if you are editing X in anyway, such as the above, just log out and then hit ctrl+alt+backspace. that restarts X...sorry for that mistake

---

