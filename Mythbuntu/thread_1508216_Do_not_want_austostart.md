---
title: "Do not want austostart"
date: 2010-06-12
forum: Mythbuntu
---

### Post by miststlkr on 2010-06-12
I searched and saw plenty of people who wish they had my problem, but I am trying to get mythfrontend to NOT autostart on my Mythbuntu 10.04 install.  I know that sounds kind of oxymoronic, but hear me out.  I have tried unticking it in the *Settings>Session and Startup* dialog, I have tried unticking it in the Mythbuntu Control Center and even deleted the .desktop from the ~/.config/autostart directory [which removed the option from the Session and Startup dialog] and replaced it with my own launcher called myth.desktop using the command below... and still it comes!  It's like the monster from a bad horror movie!  It won't stay dead!  mwahahahahahaha 

sorry... 

...

anyway.. 

For those wondering why I would want something so silly, I have two displays set to use separate X sessions, and want it to load on display :0.1 rather than the default :0.0, but in order to do that I need to figure out which of the seemingly endless ways to start the frontend is actually being used.  Currently I wait for it to autoload on display :0.0, even though it is unticked from the startup dialog AND MCC says it does not load on startup, exit out and run a launcher for *mythfrontend -display :0.1* and all is good.  Automating the process would, naturally, be better.  

 Naturally, all I *really* want to do is autostart on the proper display, so if there is an easier way to do that than what I am playing around with here, please let me know.  If there are other places to look for an autostart folder, for example a system-wide one rather than my personal user account one, that would help too.  I did a search in Nautilus for "autostart' but if it is within a hidden directory I don't believe Nautilus will find it so the lack of results wasn't surprising there.



And now for the sucking up;  I'm learning a LOT reading this forum, thanks for all the help you guys throw out there!!!


Cheers all!

---

### Post by superm1 on 2010-06-13
> **miststlkr said:**
> I searched and saw plenty of people who wish they had my problem, but I am trying to get mythfrontend to NOT autostart on my Mythbuntu 10.04 install.  I know that sounds kind of oxymoronic, but hear me out.  I have tried unticking it in the *Settings>Session and Startup* dialog, I have tried unticking it in the Mythbuntu Control Center and even deleted the .desktop from the ~/.config/autostart directory [which removed the option from the Session and Startup dialog] and replaced it with my own launcher called myth.desktop using the command below... and still it comes!  It's like the monster from a bad horror movie!  It won't stay dead!  mwahahahahahaha 

sorry... 

...

anyway.. 

For those wondering why I would want something so silly, I have two displays set to use separate X sessions, and want it to load on display :0.1 rather than the default :0.0, but in order to do that I need to figure out which of the seemingly endless ways to start the frontend is actually being used.  Currently I wait for it to autoload on display :0.0, even though it is unticked from the startup dialog AND MCC says it does not load on startup, exit out and run a launcher for *mythfrontend -display :0.1* and all is good.  Automating the process would, naturally, be better.  

 Naturally, all I *really* want to do is autostart on the proper display, so if there is an easier way to do that than what I am playing around with here, please let me know.  If there are other places to look for an autostart folder, for example a system-wide one rather than my personal user account one, that would help too.  I did a search in Nautilus for "autostart' but if it is within a hidden directory I don't believe Nautilus will find it so the lack of results wasn't surprising there.



And now for the sucking up;  I'm learning a LOT reading this forum, thanks for all the help you guys throw out there!!!


Cheers all!

I'm at a bit of a loss why it's still autostarting without the .desktop file there - but I'm guessing it's the xfce cache of running applications when you logged out.  Try to log out 'saving your settings' when mythfrontend isn't running.

As for your parameters:
Try modifying /etc/mythtv/session-settings to add your necessary parameters.  That file is sourced by the mythfrontend shell script that does the startup for the binary.

---

### Post by miststlkr on 2010-06-13
Excellent!  I removed the launcher that I had created, closed the frontend, log-out/log-in, modified that file you pointed out and re-ticked the autostart option in the MCC.  Worked like a charm.  Thanks!

---

### Post by miststlkr on 2010-06-13
I recant my previous statement.   I just did a full reboot rather than a logout/in and I have Myth autostarting on both displays again.  Ideas?

---

### Post by superm1 on 2010-06-13
> **miststlkr said:**
> I recant my previous statement.   I just did a full reboot rather than a logout/in and I have Myth autostarting on both displays again.  Ideas?

Did you try what I said about logging out and saving settings?

---

### Post by miststlkr on 2010-06-13
I did, sir.   I have to run out for a bit, but I have an idea I'll try when I get home and I'll post it here for posterity if it works out.

---

### Post by miststlkr on 2010-06-13
I just disabled autostart  in the MCC, closed the frontend and logged out/in.  the frontend did not autostart.  Rebooted to confirm and now I have the following error:

```

mount: mounting /dev/disk/by-uuid/....... on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys  failed: No such file or directory
mount: mounting /proc on /root/proc  failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

```then I get dumped into BusyBox with a prompt (initramfs)



not a clue what to do from here.  I'll do the obvious and make sure nothing somehow managed to unplug the harddrive or something odd like that.   I'm sure this is an unrelated issue as I have unticked that box several times, but thought I might mention it here just in case.


[EDIT=add] I don't believe there have been any other changes to the system since last reboot [/EDIT]

[edit2] I booted to a liveCD and ran gparted, there were a few flags on the boot drive so I ran a "scan and repair filesystem" and I'm back in business.  Back to the issue at hand after dinner.  not sure what caused the issue there, but the scan seems to have it sorted out. [/edit2]

---

