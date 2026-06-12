---
title: "Help wanted on remote on Mythtv with Winfast card"
date: 2006-12-18
forum: Multimedia &amp; Video
---

### Post by gosh on 2006-12-18
Hi everyone,

I managed to get lirc working on edgy with my Winfast card (lirc_gpio).
When I run irw it works properly and shows the keys I pressed on the remote.
However I can't get it to work properly with Mythtv.
Does anyone has a good .lircrc file?

---

### Post by superm1 on 2006-12-18
I don't personally have a .lircrc for this, but you do know that myth uses its own lircrc in ~/.mythtv/lircrc right?

You can just make a symlink to this file and use the .lircrc in ~/.lircrc if you want however.

If you grab the mceusb .lircrc from the help.ubuntu.com/community pages, you can modify this to match the buttons defined in your /etc/lirc/lircd.conf.

---

### Post by gosh on 2006-12-19
Well, actually I'll have to take a step back.
I even can't change channels with the up and down arrows. When I press the up-arrow a small window at the bottom of the screen lights up with the channel information, but it doesn't change to that channel.

BTW, I replaced the original ~/.mythtv/lirc with a link to .lircrc. That file has been changed a lot with various files I found on the internet, but none of them worked. I noticed that some use 

prog = mythtv 

others use 

prog =irxevent

What should be used?

---

### Post by superm1 on 2006-12-19
> **gosh said:**
> 
BTW, I replaced the original ~/.mythtv/lirc with a link to .lircrc. That file has been changed a lot with various files I found on the internet, but none of them worked. I noticed that some use 

prog = mythtv 

others use 

prog =irxevent

What should be used?
Well this is a matter of whether you wan the keystrokes to be interpreted directly by myth or by the X server.  The former allows you to customize keys on your remote for every app you want to use.  So for example your play button can be a play in say xine, but it could be a stop in myth.  The latter allows you to map the 'P' button to your play button on the remote.  Now, you have to make sure that P does the right function in all the remotes that you want to use.

---

### Post by gosh on 2006-12-19
Thanks so far for your help.
I'll guess I'll just have to try things out and see if and how it works for the moment.
Anyway, I like it that way! It's just a hobby for me and i'm learning a lot!

---

