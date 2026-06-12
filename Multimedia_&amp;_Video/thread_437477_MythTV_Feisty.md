---
title: "MythTV Feisty"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by McHenry on 2007-05-08
I'm using the following guide and all is going well:
[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

The problem is I now need to reconfigure the cards but I cannot get into mythtv-setup

Whenever the box boots it logs in as the mythtv user and automatically goes into the mythtv frontend, what I need is a terminal prompt for me to type mythtv-setup..

How can I get into the mythtv-setup program ?

Thanks

---

### Post by newlinux on 2007-05-08
You can probably exit out mythtv and by pressing escape, and there should be a desktop behind it where you can access a console.

---

### Post by McHenry on 2007-05-08
When I exit MythTV using escape it logs me out and tankes me back to the login prompt and logs in again after 5 secs.

It's as if the mythtv frontend is being used as the desktop environment.

---

### Post by newlinux on 2007-05-08
can you log in as a different person at the login prompt or with different options at the login prompt?

---

### Post by newlinux on 2007-05-08
Also do you have access to another machine with an X session (linux, VNC, etc.)? You could remotely login and run mythtv-setup

---

### Post by McHenry on 2007-05-08
Cannot login with another user as it logs in and presents a blank screen. Looks like only the mythtv user has a gui environment...

I can access the machine remotely using ssh but no idea how to obtain a remote x session.

---

### Post by newlinux on 2007-05-08
ssh -X machineIPorNAME -l mythtv

That gives you an X session (forwards it to the remote computer). Then you can run mythtv-setup remotely.

---

### Post by McHenry on 2007-05-08
What states that the mythfrontend is to be run upon login ?

Where could I specify this to be mythtv-setup instead ?

I tried the ssh -X without success. Could you give me and example. The ip is 192.168.1.13

So from a remote terminal session I would type:

ssh -X 192.168.1.13 -l mythtv ?

---

### Post by newlinux on 2007-05-08
> **McHenry said:**
> What states that the mythfrontend is to be run upon login ?

Where could I specify this to be mythtv-setup instead ?

I tried the ssh -X without success. Could you give me and example. The ip is 192.168.1.13

So from a remote terminal session I would type:

ssh -X 192.168.1.13 -l mythtv ?

Yes, that ssh command should work. what happens when you run it? Are you running it from a terminal that is in an X environment? Can you ssh in without forwarding X (take out the -X in the command)?

I didn't run my install of mythtv that way (I installed mythtv separately, as I also use my machine as a regular machine, thus I don't have any autologins and I run mythfrontend from terminal when I want to use myth).
I take a look at the instructions you used, and see what's what..

---

### Post by McHenry on 2007-05-09
Yes it works however it is very very slow... 10 mins and still wating so far after typing mythtv-setup

---

### Post by Titus A Duxass on 2007-05-09
Exit mythtv and at the logon screens in the lower left hand corner you have the open of change sessions or something like click on that and then select "openbox".

You have to be quick as you have only 5 seconds.

---

### Post by McHenry on 2007-05-09
Thanks for the help.

I tried this and logged in as as the default user (not mythtv) but all I get is a solid coloured screen and nothing else...

---

### Post by Titus A Duxass on 2007-05-09
The solid coloured screen is your desktop, right clicking on it will bring up a menu where you can select the terminal.

I think this is explained in the community How-To.

---

### Post by newlinux on 2007-05-09
> **McHenry said:**
> Yes it works however it is very very slow... 10 mins and still wating so far after typing mythtv-setup

Wow, that's slow. I do this from a wireless connection in my home network and it is plenty fast. What kinds of speed does your home network run on?  Anyway, a solution has already been posted. If you are running openbox you should be able to click on the background and get access to a terminal.

---

### Post by McHenry on 2007-05-13
I need to update some frequencies as per:
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/580190.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/580190.html)

However I have found the mythtv-setup prog to be quite unstable and often crashes.

What is the best way to update these frequencies ?

Thanks

---

### Post by nickblame on 2007-05-21
i am really glad i can help!!!

just log in as root and go to /home/mythtv/.mythtv/ path and delete backend_configured dummy file
then next time you reboot or restart gdm the mythtv-setup will launch :))


now if i may i have some inquries myself.. did anyone convince a backed-server installation to use nvidia graphics driver? ( I think it has not recognized nvidia and I get choppy mpeg2 output) i installed nvidia-glx from aptitude but no accelaration :(

anyway it would help a bunch to have some more options during watching tv. i had a mythdora box and i even had a keyboard shortcut to get the console up on top of mythtv video.

anyway it is really good effort with fiestly and mythtv :) nice work
cheers

---

### Post by nickblame on 2007-05-21
hey i found the nvidia-xconfig and now it is using accel :KS
i have some chops now and then i'm pretty sure it is something with the cache it keeps of live tv to scroll back and forth, i guess if i find that too i get to keep my low end ubuntu myth box :)

---

### Post by superm1 on 2007-05-22
> **nickblame said:**
> i am really glad i can help!!!

just log in as root and go to /home/mythtv/.mythtv/ path and delete backend_configured dummy file
then next time you reboot or restart gdm the mythtv-setup will launch :))


now if i may i have some inquries myself.. did anyone convince a backed-server installation to use nvidia graphics driver? ( I think it has not recognized nvidia and I get choppy mpeg2 output) i installed nvidia-glx from aptitude but no accelaration :(

anyway it would help a bunch to have some more options during watching tv. i had a mythdora box and i even had a keyboard shortcut to get the console up on top of mythtv video.

anyway it is really good effort with fiestly and mythtv :) nice work
cheers
Exactly what I was going to chime in.

On FE/BE boxes, the first time you start the automatic session, a file is created in
/home/mythtv/.mythtv/backend_configured

You don't need to be root to necessarily remove it, but just a user with sudo permissions.  

The easiest way is to ssh into the box as the other user account that you created, and remove the file via ssh.  The next time you start the box, it will ask you to run mythtv-setup before starting the frontend.

---

