---
title: "HDMI Blue Screen of Blankness"
date: 2011-02-22
forum: Multimedia Software
---

### Post by frankstrudel on 2011-02-22
Hi

I've got a combo TV/monitor that I've had no problems with on VGA, but seeing as I have an HDMI out on my PC, an HDMI in on the monitor, and and HDMI cable, I would like to try using it as an HDMI monitor...

I'm using the NVidia XServer 260.19.06

When I plug in the HDMI cables and auto-detect, my monitor is recognised as "DFP-0-(ProView/EMC/PTS TLU-01911C)" (same as via VGA, only called 'DFP' instead of 'CRT').

I've tried lots of X Screen and TwinView combinations;
-making the HDMI connection the main screen, 
-disabling the VGA connection, 
-making them 'dualscreen', 
-setting them as seperate X screens

but all I ever get when I apply it is a blue screen on the HDMI connection (and whatever you'd expect on the VGA connection), until the time runs out and it reverts to the VGA, when the HDMI connection reports 'no signal'.

The only other thing I can think of is to set X to use the HDMI connection, then reboot the computer with the monitor on HDMI, in the hope a reboot somehow helps. But if it doesn't (and I think it's a long shot), I suddenly have no monitor. Which would be quite disconcerting. 

Any better ideas?

---

### Post by frankstrudel on 2011-02-22
Update: I set both connections at the same absolute position in TwinView, and rebooted, connected to HDMI.

Saw it all boot up nicely, until the log-in screen, when it went all blue again. Any ideas what's going on? I guess that's when the Xserver becomes involved, so how comes the GRUB bootloader is doing fine? 

And more importantly, how do I get the XServer to do the same?

---

