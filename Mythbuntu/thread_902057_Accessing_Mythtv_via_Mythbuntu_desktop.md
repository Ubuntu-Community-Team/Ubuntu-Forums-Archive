---
title: "Accessing Mythtv via Mythbuntu desktop"
date: 2008-08-27
forum: Mythbuntu
---

### Post by Bobo1811 on 2008-08-27
Hello, 
I have been watching mythtv through my normal tv and it has been fantastic.  I also had a monitor attached that displayed the mythbuntu desktop so I could transfer my movies and music over.  I had finished with the monitor and thought i would disconnect because mythtv was already loading to my tv screen.  Now when I turn on my computer the tv screen shows the mythbuntu desktop and I don't where my mythtv has gone and I don't know how to access through the desktop (i am a complete novice).  Can someone help me find my mythtv.  When I repluugged in the monitor it is not working.

Thank you

---

### Post by volkswagner on 2008-08-27
To launch Mythtv from the desktop go to

Applications>Multimedia>Mythfrontend

You should also make sure mythtv is set to launch at start up.

Go to Applications>settings>Autostart or startup progams (I get foggy here)
Anyway Mythtv should be on the list.

Have you performed another restart with just the TV connected?

---

### Post by Bobo1811 on 2008-08-27
Thank you for your reply.

When we tried clicking on frontend nothing happens.  Secondly we could not find the autostart option.

Cheers

---

### Post by DutchLoki on 2008-08-27
In ubuntu (and mythbuntu) you can have multiple desktops. One desktop for each monitor. I might be that your mythtv frontend is running on a other desktop than the one you are currently watching. could you try to switch desktop and tell us wath you see than? 

if that does not help, than go to [applications][system][system monitor] and look if the mythtv frontend is running.

---

### Post by Bobo1811 on 2008-08-28
I am not sure how to check/switch to the second monitor.  Could you please tell.
Thank you

---

### Post by volkswagner on 2008-08-30
> **Bobo1811 said:**
> Thank you for your reply.

When we tried clicking on frontend nothing happens.  Secondly we could not find the autostart option.

Cheers

I have had in the past, problems launching mythfrontend.  This usually indicates an underlying issue.  I was however able to launch mythfrontend by trying several times, eight or more successive clicks.  Sometimes it seemed to help if I opened a terminal when trying to launch mythfrontend.

Also try opening a terminal and tail the log before attempting to launch the frontend.  Post any relevant results here.
```

-tail /var/log/mythtv/mythfrontend.log
```

---

### Post by Bobo1811 on 2008-09-03
I have really mucked it up now.  As I have all the equipment it seems a waste not to use it as it was working so well.

As I don't know what I am doing I was  wondering if anyone knows of a place that will set it up for you in the Perth, WA area.  

Cheers

---

### Post by volkswagner on 2008-09-03
I am sure you can work things out via the forum.  Folks here are knowledgeable and friendly.

Fist do you have a second machine on your network, so the second monitor is not needed?  Most any task can be completed via a remote login via ssh.

What video card are you using?

Can you open up mythbuntu-control-centre and select either ATI's, or Nvidia's utility if you have one of those?  You may be able to select the default monitor there.

Don't give up.  The best reward is, you will end up "knowing what you are doing".

---

### Post by Bobo1811 on 2008-09-03
I only have one monitor and i am not on the network.  would it be easier to set it up so it was on the network.

---

