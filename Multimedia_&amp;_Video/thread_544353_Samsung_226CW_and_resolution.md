---
title: "Samsung 226CW and resolution"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by luzu on 2007-09-06
Hi all,

today I bought a Samsung 226Cw monitor that can run at 1680x1050 resolution(already runs at windows at this resolution).
My graphics card is nvidia geforce 7300.
Is there anyone how can advise me who to get 7.04 run at this resolution?
At this time the higher option that I have is 1024x768.

Thanks In Advanced

---

### Post by luzu on 2007-09-07
I found the solution and its name is

sudo dpkg-reconfigure xserver-xorg

it took me some time but it worked...now I am working with 1680x1050 resolution...the only thing that you have to do it is to follow the very good instructions and choose the resolution that you want (all the values of resolutions that I know is included)...
The bad thing is that you have to reconfigure many things,like keyboard mouse etc.,but if you run the application carefully I believe that you will not have any problems...For example, I made a mistake and I changed the keyboard language layout.Don't worry if you make something like that...all this thinks can easily be changed by editing the xorg.conf file...

after that I believe that xorg.conf can change my name,my phone number...  :)

---

