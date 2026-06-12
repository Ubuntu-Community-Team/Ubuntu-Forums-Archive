---
title: "Lircmd will not work---DRIVING ME CRAZY!"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by danman862 on 2007-03-19
Good afternoon,

I have spent most of the winter playing with LIRC (off and on).  It took me sometime to finally get irw to work and give me an output.  But in the end I have a remote--Yahoo!  It was a long battle to get to that point mostly becasue I'm a Linux newbe (learning quickly).  My final hurdle is Lircmd.  I follow all the directions I can find and it just does NOTHING.  There is not Debug tools, so I can't tell if Xorg.conf is the problem or Lircmd.conf is.  Can someone please help me?

I need to find out which area my problem is, I know the remote works fine.
Remote: ATI remote wonder USB

Thanks Danman

---

### Post by danman862 on 2007-03-21
Not that is matters as nobody has replied to this thread, however I found that my LIRCMD loads after Xserver tries to create the LIRC-Mouse.  Of course it won't find /dev/lircm yet....I posted another question to find out how to move it up in priority.

---

### Post by bdogg64 on 2007-03-21
Did you look at your syslog ? And what program are you trying to get working with your remote?

---

### Post by seeitall on 2007-03-23
I've spend half day trying to make lircmd to work with ati today.  you
can try:

strace -p pid

where pid is a pid of running lircmd 

to see what's going on. I had to switch to ps2 protocol. this is my working 
conf:

lircmd ========

 
PROTOCOL IMPS/2

MOVE_N ati_remote mouse-up
MOVE_S ati_remote mouse-down
MOVE_W ati_remote mouse-left
MOVE_E ati_remote mouse-right
MOVE_NW ati_remote mouse-left_up
MOVE_NE ati_remote mouse-right_up
MOVE_SW ati_remote mouse-left_down
MOVE_SE ati_remote mouse-right_down
BUTTON1_CLICK ati_remote mouse-button_left
BUTTON3_CLICK ati_remote mouse-button_right



xorg =========

Section "InputDevice"
        Identifier  "LIRC-Mouse"
        Driver      "mouse"
        Option      "Device" "/dev/lircm"
        Option      "Protocol" "IMPS/2"
        Option      "SendCoreEvents"
        Option      "Buttons" "2"
        Option      "ZAxisMapping" "4 5"
EndSection

==============

---

### Post by alcarola on 2008-06-01
Hi!

I got lirc started before xorg by making the following steps:

cd /etc/rc2.d
sudo mv S51lirc S10lirc

This makes lircmd start before xorg (gdm i guess) when you go into runlevel 2, which seems to be the standard one in Hardy. (You can check by running the command runlevel.) Then xorg has no problem finding /dev/lircm and the lirc mouse works (for me at least). :)

Hope this helps,
Mikael

---

