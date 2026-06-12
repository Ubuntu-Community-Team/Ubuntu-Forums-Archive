---
title: "When wired remove the computer freezed"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by white_devil on 2010-06-26
Hello, 

i just installed ubuntu netbook in my hp mini and everything is ok, wireless wasnt working but a quick search in this forum solved the problem.

But now if i'm connected wired and disconnect the wire (to see if the wireless connects automaticly) the computer freeze, is there any solution for this?

And if i am connected wireless and disconnect and then plug in the cable the computer just doesnt recognized it stay offline, is there any icon i should click or something, so the pc could know that i wanna go wired??

Thank you

---

### Post by matt-fender on 2010-06-26
What happens when you hit CONTROL , ALT + DELETE when the mini freezes?

Can you right click on your network icon on your panel, go to "Edit conections".
Click on wireless, then make sure that the Automatically connect is selected.

---

### Post by white_devil on 2010-06-26
when the mini freeze CONTROL ALT DELETE doesnt work, the whole pc doesnt make anything, even the mouse stop moving.

The wireless is automatically so it connects as soon as i turn the mini on.

I saw that when the computer is turned on with the network cable unplugged the eth0 doesnt even appear in the networks list, is like if it disable the driver :S, any recomendation please? i think it must be a configuration error or something, because drivers are working great.

The main problem is that in my work the wireless sometimes kinda fail and i must go wired, but do i really need to restart the whole pc for wired to work?

Thank you

---

### Post by white_devil on 2010-06-26
This is the exactly same problem i have:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/466325](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/466325)

---

### Post by white_devil on 2010-06-26
Ok, i just tested that if the mini is on battery mode the ethernet just disappear, that might be the problem, with the battery charger is plugged in everything works fine, any help please? i readed some where it is a bios related issue, but what can i do?? thank you

---

### Post by matt-fender on 2010-06-26
> **white_devil said:**
> Ok, i just tested that if the mini is on battery mode the ethernet just disappear, that might be the problem, with the battery charger is plugged in everything works fine, any help please? i readed some where it is a bios related issue, but what can i do?? thank you


HP Mini by any chance?

You could try removing your battery when the netbook is shut down and leave it out for ten minutes or so and try again ( i read somewhere about the wireless that this can sort a lot of problems ) OR ceck your BIOS for like power saving modes, it could be disabling your ethernet when you are running on battery.. just a possibility.

---

### Post by white_devil on 2010-06-26
Yes, HP Mini, i'll try removing the battery :) i searched all over the BIOS but couldnt find any option about power saving.

Thank you

---

### Post by IceDoE on 2010-06-26
Which HP Mini? HP Mini 210 by chance? 

I just installed UNE 10.04 on 15 of them a few days ago and have been working through some issues. Most have worked fine, but a few odd ones have just had random and different issues, none of which have been like yours.

My suggestion and thoughts? 

1. Get all the updates and try to find some broken packages and reinstall.

2. (Recommended) If you haven't put much data on it, or can back up, try a new clean install of the latest UNE 10.04 you can find (assuming you even are using 10.04 now). I have a suspicion for some of the ones having odd errors I have that there was a problem with the install and a few ghost breaks somewhere or other which I clean install should fix.

That might not be terrible helpful, and the latter is obviously just a brute force method, but if you are using an HP Mini 210 then my experience would indicate you should be fine in UNE if there isn't a corrupt file somewhere. Someone else might have more luck identifying what the file is so you only need to reinstall that though.

---

### Post by white_devil on 2010-06-26
Solved!! =) the solution was on this page:

[http://www.ubuntu-es.org/node/121932](http://www.ubuntu-es.org/node/121932)

Basically just edit the file /etc/default/grub and change:

GRUB_CMDLINE_LINUX=""

to

GRUB_CMDLINE_LINUX="acpi_os_name=Linux"

then

sudo update-grub 
sudo apt-get update

shutdown (not restart) and start the pc again, problem solved!!! :D no crash, and everything works like a charm!! thank you matt-fender for your help!

---

### Post by matt-fender on 2010-06-26
> **white_devil said:**
> Solved!! =) the solution was on this page:

[http://www.ubuntu-es.org/node/121932](http://www.ubuntu-es.org/node/121932)

Basically just edit the file /etc/default/grub and change:

GRUB_CMDLINE_LINUX=""

to

GRUB_CMDLINE_LINUX="acpi_os_name=Linux"

then

sudo update-grub 
sudo apt-get update

shutdown (not restart) and start the pc again, problem solved!!! :D no crash, and everything works like a charm!! thank you matt-fender for your help!


Glad you have it sorted!!

 the HP Mini runs Ubuntu pretty nicely, (better than my aspire ZG5 anyway)

---

