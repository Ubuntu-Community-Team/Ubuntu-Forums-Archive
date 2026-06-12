---
title: "[SOLVED] lirc won't autostart after mythbuntu-generator run"
date: 2007-12-12
forum: Mythbuntu
---

### Post by arjay1 on 2007-12-12
[I]UPDATE - Think I have fixed this problem.  I did a more thorough uninstall of  EVERYTHING to do with lirc including what is described in the original thread, but then removing everything I could find that had lirc in the title.  I then went through a re-install of lirc, mythbuntu-lirc-generator, etc etc, as below.  It then needed a shutdown and a reboot, but my remote is up and running again.
[/I]
OK - this is a new thread about an existing issue, started after advice from superm1.  The original posts were in a thread that had gone off-topic - hence the new thread.

The issue is this.  I installed mythbuntu using the various options in the control centre - one of which was to choose the remote for my system. I have a Hauppauge pvr150 (non-mce) card and the newer grey/silver remote with the four coloured buttons along the bottom).  I chose the appropriate lirc and fired up mythbuntu.

It all worked great and my hats off to the folks who have simplified the setup for mythtv - you have done a great job.

The only problem was that some keys did not work on the remote - most importantly being the back/exit key,  It was suggested that I ran mythbuntu-lirc-generator which I did.  Hey Presto, my remote then had one or two more functioning buttons - including the Back/Exit.

Great says I.  However, on the next reboot, either lirc failed to load, or there was some other problem, because the remote would not work (keyboard still worked fine).  I now have to manually run "/etc/init.d/lirc restart" to get the remote to work.  It then runs faultlessly until the next reboot.

Superm1 suggested that I run "sudo update-rc.d lirc defaults".  When i tried this, it just reported: "system startup links for /etc/init.d/lirc already exist" and the remote would still not work.

I uninstalled lirc using the complete removal option in Synaptic (which meant uninstalling mythbuntu desktop, lirc, and mythbuntu-lirc-generator as well, which seems rather drastic). 

I then re-installed them all but the remote still won't fuction unless I run /etc/init.d/lirc restart as well.

Can anyone help me chase down the problem?  

Cheers

Richard

---

### Post by surfed on 2008-03-03
I am having the same issue with lirc not working unless i do a lirc restart, is there another way then a complete reinstall of lirc to solve this? its great that this is a solution but it does not fix the problem in an elegant way.

---

### Post by arjay1 on 2008-03-03
> **surfed said:**
> I am having the same issue with lirc not working unless i do a lirc restart, is there another way then a complete reinstall of lirc to solve this? its great that this is a solution but it does not fix the problem in an elegant way.

Just to update you.  I recently (in the last 2 weeks) had to re-install mythbuntu and had the exact same problem.  I had to solve it in the same (inelegant) way.

Perhaps it is worth filing a bug report?

---

