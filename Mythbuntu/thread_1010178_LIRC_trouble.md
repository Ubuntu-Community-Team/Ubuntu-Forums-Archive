---
title: "LIRC trouble"
date: 2008-12-13
forum: Mythbuntu
---

### Post by NautiusMaximus on 2008-12-13
Hi All

I'm building an HTPC based on a Silverstone GD02-MT case. This comes with a remote control that I believe is the iMon PAD. 

I'm setting up the PC with Ubuntu 8.10, and plan to install MythTV once I've got some basic stuff working (feel free to tell me if you think this was a really bad idea and I should install Mythbuntu from the start).

I gather I need to install LIRC to get the remote to work. I tried to do so, following the instructions at [http://www.mythtv.org/wiki/index.php/Ubuntu_lirc_install](http://www.mythtv.org/wiki/index.php/Ubuntu_lirc_install)

I got as far as the line

sudo m-a a-i -f lirc

and when I tried that, I got the error message "Build of the package lirc-modules-source failed!"

As a complete Linux newbie, I'm rather stumped about what to do next. Any suggestions?

Thanks
NM

---

### Post by NautiusMaximus on 2008-12-16
Bump

---

### Post by jMon54 on 2008-12-16
Well, first off I would suggest going with a fresh install of MythBuntu.  That said, I would recommend you use the software manager to reinstall LIRC.

---

### Post by Hayesio on 2008-12-16
Yeah, i would recommend starting from scratch with Mythbuntu. It will do most of the configuring for you, particularly with lirc.  If you do have the imod pad, you can just select it from the menu in the Mythbuntu control centre (MCC) and jobs done!  You can alway build towards a standard Ubuntu desktop machine from Mythbuntu anyway. Its a lot easier going this way than from Ubuntu towards Mythbuntu.

Cheers

---

### Post by NautiusMaximus on 2008-12-17
Thanks for the suggestion.

Perhaps I should explain more about why I decided to install MythTV separately from Ubuntu. The case has a touchscreen display on the front, and I've really struggled to find any information on how to get it working. The best I've managed to find is [http://www.mythtv.org/wiki/index.php/Zalman_HD160XT](http://www.mythtv.org/wiki/index.php/Zalman_HD160XT). That's a different case, but I believe it uses the same touchscreen. The instructions there suggest installing Ubuntu on its own before installing MythTV, so I thought that would be a sensible way to go.

Does my reasoning make sense? That was the only reason for not installing Mythbuntu in one hit, so if my reasoning doesn't make sense, then I'll change my mind about that.

I'm also wondering if I could live without the touchscreen functionality in the interests of just getting the damn thing working sometime this decade, in which case going straight to Mythbuntu would make sense, especially if you think it's going to be easier to get the remote to work that way.

Thanks again
NM

---

### Post by Damanther on 2008-12-17
You can tell Mythbuntu post install that you want to run the machine as a desktop, its one of the actions in the system roles section of the mythbuntu control centre. You can try to add the setup for your touchscreen at that point.

But, it is easy enough to install mythtv-backend, mythtv-frontend, and lirc from synaptic. (Sorry Mythbuntu team, your great too!! I love ya)

The lirc install will let you choose what remote you are using and configure your system for that. It works pretty darn well. You will need to get a copy of an lircrc file to put in the home directory. I can post you mine if you like. Its for a MCE remote though.

Mythbuntu would nicely generates one for you though if you went that route.

---

