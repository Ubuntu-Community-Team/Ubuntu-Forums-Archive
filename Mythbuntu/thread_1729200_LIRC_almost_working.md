---
title: "LIRC almost working"
date: 2011-04-14
forum: Mythbuntu
---

### Post by sudanmas on 2011-04-14
My hauppage pvr 250's bundled grey remote after I did a reinstall last week.

I had to do a reinstall of 10.04 a couple of days ago.  A couple things remain to get sorted out to bring things back to normal.

I have the Hauppage's 250 grey remote almost working - IRW shows codes with key presses from a shell prompt, however, the remote has no effect when I try to use it in the mythfrontend menus.

I checked the mythcontrol center and the Hauppage TV Card is selected under the section, but still no luck.

Suggestions?

---

### Post by azmyth on 2011-04-15
Did you generate a .lircrc file for your remote in your /home/username directory?

---

### Post by sudanmas on 2011-04-15
I'll check that when I get home. I found this other thread based upon your question, which I'll also look into.
 
[http://ubuntuforums.org/showthread.php?t=1065804](http://ubuntuforums.org/showthread.php?t=1065804)

---

### Post by wrectum on 2011-04-15
does the problem persist after a full shutdown, then power on, as opposed to a reboot? I had a problem with my hauppage nova-t500 silver remote not working correctly when the tuner card was initialised in a "warm state"...

---

### Post by sudanmas on 2011-04-15
The remote wasn't working even after a full shutdown / restart

I did get it up and running though:

Copied my lircrc file into .mythtv in my home directory, exited the frontend and
restart lirc with a /etc/init.d/lirc restart

When I reloaded the FE,  the remote worked

---

