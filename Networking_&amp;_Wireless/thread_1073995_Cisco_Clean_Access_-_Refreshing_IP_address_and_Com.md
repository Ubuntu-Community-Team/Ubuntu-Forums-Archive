---
title: "Cisco Clean Access - Refreshing IP address and Computer Freeze"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by ScrantonSka on 2009-02-18
This is my first post on Ubuntuforums so if there are some problems with the format of my question i apologize in advanced and would appreciate any help for future reference.
So I am a newer Linux user, I have only had This OS installed on to my HP laptop for about 4 months now, and have been solving my problems by reading other posts on this website, however I have not been able to find anything to help me with the problem at hand.
My problem is 2 fold, first is that my university uses Cisco clean access agent, as a network access control. When I connect my computer to the network through the Ethernet cord and then start up my browser, I am prompted by a webpage to enter in my User Id and Password. I do both and submit and then a new page begins to load. I am then prompted by a terminal pop up that asks me to enter my root pass word so that clean access can refresh my ip address. I do so and then my web browser tries to load a page, but after some time it returns that the page cannot be found. Upon entering any other site from then on out returns the same message.
The second problem is with my wireless. When I go through the same motions as stated in the previous problem, except with wireless i am able to log on to the network and access web pages, however after a small variable amount of time, my computer freezes, and there is nothing I can do to unfreeze it apart from manually turning off the computer and restarting it. I believe that the freezing problem has something to do with my logging onto the network, because in all other cases where I have used my wireless to connect to a net work, I have had no problems.
Any help with either of these problems would be greatly appreciated.

---

### Post by pops-saito on 2009-03-02
For your first problem, if you are using Konqueror or Firefox, you may want to try changing your "Browser Identification" as described in this thread -

[http://kubuntuforums.net/forums/index.php?topic=3091091.0](http://kubuntuforums.net/forums/index.php?topic=3091091.0)

I'm not sure about your second problem, where your computer is locking up.  You mention that it only happens when you are on the "network".  Are you referring to the wireless network or the Clean Access network?

---

### Post by pops-saito on 2009-03-03
I have now also experienced a "freeze problem" when connecting to Clean Access via a wireless network on an Acer Extensa 4630-Z notebook.  It sometimes takes an hour but it is fairly consistent.  The system usually freezes completely (mouse cursor frozen, cntrl-alt-F5 doesn't work, cold boot required).

However, when connected to Clean Access via a wired network (with my wireless disabled), everything is fine, with no "freeze problem". 

I am suspicious that something has changed with my campus Clean Access system as last week my Clean Access login/password stopped working. I had to provide my MAC addresses (wired and wireless) to the campus techs before I could login again.  It was right after this that my wireless "freeze problem" started.

Perhaps there is a recent Clean Access update that is the culprit?

---

### Post by ScrantonSka on 2009-06-08
I was able to fix my first problem by refreshing my connection when i am prompted for my root password.
However the second problem is still present and I am thinking it may be that the packets it receives from cisco and the network. So I was thinking that I might need to update my wireless drivers. Im going to try to fix it my self, but if any one know a solution im open to it. Im running on a hp compq nx 7400. Thanks for the help

---

