---
title: "Problem with network-admin"
date: 2009-01-13
forum: Networking &amp; Wireless
---

### Post by fireballnelson on 2009-01-13
Ok, first of all, I am new to ubuntu so I don't know exactly what I am doing (Just kidding -- sort of). I am currently running Ubuntu 8.10 and have been trying to set up a dial-up modem. However the first instructions I see in the help pages are telling me to open "Network" in the pulldown menu at the top of the screen(I can't remember exactly what it's called). This "Network" option is not there and when I type "network-admin" in a terminal it tells me that it isn't installed but I can install it by typing such and such a command. So I copy and paste and it tells me that it can't find the directory or something like that.
I was thinking about just getting an internet connection through the RJ-45 port but then I thought "how am I ever going to learn anything if I just take the easy way out?" HA ha, the story of my life.
Anyway, thanks for the help.

---

### Post by 2hot6ft2 on 2009-01-13
> **fireballnelson said:**
> This "Network" option is not there and when I type "network-admin" in a terminal it tells me that it isn't installed but 
It's network-manager not network-admin and to restore the applet to the top toolbar do this.

System->Preferences->Sessions

Go to "+ Add"

Then fill in the fields as follows:

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

And click "Save"

Then logout and log back in to and see if you have the applet on your tool bar.

If that does not work run "nm-applet" from the command line and post the output.

---

