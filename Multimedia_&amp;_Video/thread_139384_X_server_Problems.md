---
title: "X server Problems"
date: 2006-03-03
forum: Multimedia &amp; Video
---

### Post by Defector on 2006-03-03
Howdy ya'll, so i am doing the swtich, and installing ubuntu, and goes through fine until it starts to load X Server, and I get this error:

"Failed to start the x server (your graphical interface). It is likely that it is not se up correctly. Would you like to view the x server output to diagnose the problem?"

Then we look at the output:

GDM: Xserver not found: /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm:0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the X server or correct gdm configuration and restart GDM. 

And then: 
"The X server is now disabled. restart GDM when it's configured correctly." 

All i'm really trying to do is get this to work so i can get to a point I am semi comfortable with (the gui) coming from a windows backround I feel more confident there, not to say that I fear the command line, just the mistakes i can make there. 

And the backround info:
mobo: asus P5DGDX-2
Vid: PowerColor X800 GTO16
Ram: 1gb OCZ
HD: 2x160gb maxtor

Other info: i have the drive partitioned up with XP home, and ubuntu, can't think of anything else. But ask if you can. 
Thanks everyone!

---

### Post by davidcrandle on 2006-03-04
hey.. i have the exact same problem and have searched everywhere.. cept my compy is different.. and am also very interested in what help anyone can provide

And the backround info:
mobo: 661fx-MLV
Vid: Gigabyte Radoen 9600 pro 128mb
Ram: 1gb generic
HD: 1 x 80gb wdc ide
      1 x 200gb wdc sata


thanx for you help

---

### Post by davidcrandle on 2006-03-04
i finally did get it to work.. if you haven't already try

sudo dpkg-reconfigure xserver-xorg

and select vesa as the graphics thing.. after all the promts.. restarting worked for me
good luck :)

---

### Post by Defector on 2006-03-05
Thanks, i read this other thread [here]("http://www.ubuntuforums.org/showthread.php?t=128435&highlight=server") seemed to work for those guys.  
Mine gave me another error so i'm in the process of reinstalling, 
because I don't know any better and that's the typical win way to fix things :rolleyes: 
will reply if it works! and well if it doesn't I'll still reply

---

### Post by Defector on 2006-03-06
well that didn't work but i dl'ed this from [ATI]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/fglrx_6_8_0-8.22.5-1.i386.rpm") and burned with my osX L-top, mounted and ran "fglrxconfig" ran through all the setup stuff then "startx" she worked! *victory dance*
Give it a try, and then victory dance

---

