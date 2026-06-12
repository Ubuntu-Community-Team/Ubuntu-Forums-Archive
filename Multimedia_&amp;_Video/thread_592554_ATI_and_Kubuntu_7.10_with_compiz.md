---
title: "ATI and Kubuntu 7.10 with compiz ???"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by Kwolbert on 2007-10-26
I am using Kubuntu 7.10 
I have a Ati Radeon 2600 HD graphics cards
I used the following web site to install the driver
ati-driver-installer-8.42.3-x86.x86_64

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The drivers seem to work fine and reports back no errors
and my OpenGl screen savers now work great.

glxinfo reports back all correct information
everything look ok with the driver
except when I run compiz the screen goes black and freezes
also install compiz-kde as well.

Am i missing a step or can't this version of Linux with KDE 
run with this type of Graphics card. 

Any help would be great !

---

### Post by prshah on 2007-10-26
Try adding the following line to your relevant device section in your /etc/X11/xorg.conf:

 Option "UseFBDev" "true"

Make it the last-but-one line (Just before "EndSection"), and put it on a line by itself.

Let me know if it helps?

Cheers,
PRS

---

### Post by Kwolbert on 2007-10-26
:confused:

Thanks for the help

added it to xorg.conf file but still get same results

when running compiz I get black screen and nothing else.

Ready to format my drive and load MsDos 6.0 :lolflag:

any other ideas ?

---

### Post by prshah on 2007-10-27
Adding 
"VideoRam" 131072
before the UseFBDev line

also worked to clear that same error when I faced it... your mileage may vary...

MSDOS 6.0? Really? That bad?

Cheers,
Priyasen

---

### Post by Kwolbert on 2007-10-28
Gave it a try but reject the new configurations  ](*,)
just load up in kernel no GUI interface so I had to remove the command

Yeah I seem to be losing the control over the GUI battle, think its best to go back
to the  command line.  :lolflag:

Thanks for the Help , still looking for answers , 
Should I buy a new graphic card ?

---

### Post by Kwolbert on 2007-12-10
Got it to work, was forgetting the aiglx setup

---

