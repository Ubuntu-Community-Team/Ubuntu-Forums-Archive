---
title: "How-to manually restart Xorg in 2011?"
date: 2011-04-30
forum: Mythbuntu
---

### Post by neutron68 on 2011-04-30
I've searched for how to "restart Xorg" and all the old methods I've found don't work in 2011.  (Mythbuntu 11.04)

[from inside Mythtv]
Ctrl > Alt > Backspace...doesn't work

[from a tty window]
sudo startx...doesn't work
sudo pkill xinit...doesn't work
sudo restart gdm...doesn't work

What is the current method in 2011, please?

Eric

---

### Post by klc5555 on 2011-04-30
Old-style zapping went away with 9.10. This sort of thing gets done in xkb nowadays:

setxkbmap  -option terminate:ctrl_alt_bksp

and then zapping will function as it did historically for the duration of the x-session.

To make it quasi-permanent for a standard Mythbuntu setup with XFCE4, add this command to Application Autostart in the Session and Startup panel under Settings/XFCE4 Settings Manager. Then, when the desktop environment initializes, so does zapping.

---

### Post by kja999 on 2011-05-01
get to a terminal session ctrl,alt,F1 ....

sudo service gdm stop

---

### Post by neutron68 on 2011-05-09
> **kja999 said:**
> get to a terminal session ctrl,alt,F1 ....

sudo service gdm stop
```
sudo service gdm restart
```
also seems to work.  Sound reasonable?

Eric

---

### Post by neutron68 on 2011-05-09
> **klc5555 said:**
> Old-style zapping went away with 9.10. This sort of thing gets done in xkb nowadays:

setxkbmap  -option terminate:ctrl_alt_bksp

and then zapping will function as it did historically for the duration of the x-session.

To make it quasi-permanent for a standard Mythbuntu setup with XFCE4, add this command to Application Autostart in the Session and Startup panel under Settings/XFCE4 Settings Manager. Then, when the desktop environment initializes, so does zapping.
Thanks for the tip.  I made a new entry in the Session and Startup panel as instructed.

This seems like such a handy thing to have in Ubuntu!  Why was it removed?

Thanks,
Eric

---

### Post by tgm4883 on 2011-05-09
What is the reason you want to restart xorg?

---

### Post by neutron68 on 2011-05-29
> **tgm4883 said:**
> What is the reason you want to restart xorg?
Yes, there is.  

With certain recorded videos, after you try to skip forward or backward in time during playback (with the right or left arrow keys) the Mythtv player freezes playback and stops responding to controls.  You are locked out of doing anything in Mythtv and the only way I found to get control back is CTRL-ALT-F1 and restart GDM/xorg or reboot the machine.  

This has been going on since late summer 2010.  The problem only seems to occur with over-the-air (mpeg2) recordings, not from recordings made with the Hauppauge HD-PVR (h.264 recordings).

I had hoped that the Mythbuntu 10.10 update would fix it...nope.
Then, I had hoped that the Mythbuntu 11.04 update would fix it...nope.

Is this not happening to everyone?  
For reference, I record over-the-air signals in the Minneapolis tv market, using a Silicon Dust HD Homerun dual tuner.  The first channel I noticed it on was KMSP (Fox, 720p DTV standard)

Eric

---

### Post by tgm4883 on 2011-05-29
> **neutron68 said:**
> Yes, there is.  


It was a question, not an argument?

> **neutron68 said:**
> 
With certain recorded videos, after you try to skip forward or backward in time during playback (with the right or left arrow keys) the Mythtv player freezes playback and stops responding to controls.  You are locked out of doing anything in Mythtv and the only way I found to get control back is CTRL-ALT-F1 and restart GDM/xorg or reboot the machine.  

This has been going on since late summer 2010.  The problem only seems to occur with over-the-air (mpeg2) recordings, not from recordings made with the Hauppauge HD-PVR (h.264 recordings).

I had hoped that the Mythbuntu 10.10 update would fix it...nope.
Then, I had hoped that the Mythbuntu 11.04 update would fix it...nope.

Is this not happening to everyone?  
For reference, I record over-the-air signals in the Minneapolis tv market, using a Silicon Dust HD Homerun dual tuner.  The first channel I noticed it on was KMSP (Fox, 720p DTV standard)

Eric

I've never seen a bug on this and never had it happen to me. I used to record OTA, but now I just do HDPVR and pcHDTV 5500 (digital only) from Comcast. I don't use FF or Rew, but I do use the skip forward and back buttons.

---

### Post by neutron68 on 2011-05-29
> **tgm4883 said:**
> It was a question, not an argument?
It was just an answer, not an argument.  Thanks for the reply.  :)

[QUOTE=tgm4883]
I've never seen a bug on this and never had it happen to me. I used to record OTA, but now I just do HDPVR and pcHDTV 5500 (digital only) from Comcast. I don't use FF or Rew, but I do use the skip forward and back buttons.[/QUOTE]
I'm using a standard keyboard to control Mythbuntu.  During playback, I'm using Right-arrow to jump forward, and Left-arrow to jump backward.  That's when the OTA recordings lock up.

What keyboard keys are you using to "skip forward" and "skip back"?  Page-UP/Page-DOWN?
I could try those and see if it Mythtv also locks up with those keys also.

What useful data should I gather before making a bug report?

Thanks,
Eric

---

### Post by tgm4883 on 2011-05-29
> **neutron68 said:**
> It was just an answer, not an argument.  Thanks for the reply.  :)


"Yes, there is." isn't a usual response to "What is the reason you want to restart xorg?", so I hope you can see where you caused the confusion. :D

> **neutron68 said:**
> 
I'm using a standard keyboard to control Mythbuntu.  During playback, I'm using Right-arrow to jump forward, and Left-arrow to jump backward.  That's when the OTA recordings lock up.

What keyboard keys are you using to "skip forward" and "skip back"?  Page-UP/Page-DOWN?
I could try those and see if it Mythtv also locks up with those keys also.

What useful data should I gather before making a bug report?

Thanks,
Eric

I use an MCE remote and the 30 second skip forward and 5 second skip back buttons. Not sure what those are in the keyboard though.

As for logs, are you using the latest MythTV version? (are you up to date using Mythbuntu-repos) Use the Mythbuntu-log-grabber to gather all of the logs and submit them in a bug report. It would help if you can regenerate the issue right before gathering the logs.

---

