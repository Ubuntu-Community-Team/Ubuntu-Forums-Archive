---
title: "Firestarter and UFW security questions"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by robbied on 2010-06-26
Please forgive any ignorance as I have been reading but am still far from conclusions...

I really like Firestarters gui much more as it has tons more configuration options compared to Gufw.

I hear gripes that Firesstarter is not as good/secure as Gufw (gui for UFW).  I know both are just ways to manipulate Iptables.  But whats the problem here?  This is what I have found so far.


There are two gripes about Firestarter:

1.  It is not developed for anymore.  Last update was long ago it seems.  So, my question is so what.  Are there known bugs and known security issues here?  Is this actually a problem or more of a gripe?

2.  People often complain that Firestarter needs root permissions to run.  This is kind of true I guess.  To open the Firestarter gui and actually make changes to Iptables you do need to sudo. However, if you reboot and do a /etc/init.d/firestarter status you can clearly see it's running despite never sudo-ing anything.  So it doesn't need sudo to run, just make change then right?

This is also the case with UFW.  I can open it without sudo but when you try to make a rule it says there is an error.  So, to get it to add a rule, you must open UFW with root privileges.  That's the exact same things as Firestarter... Runs w/o root... Needs root to changes Iptables settings.  Same thing.


Please let me know if/where I am wrong.  I want to get this figured out.

Thanks in advance!

---

### Post by robbied on 2010-07-09
:popcorn:  Anyone? Please...

---

### Post by CharlesA on 2010-07-09
Firestarter is no longer under development and 10.10 will no longer support it. GUFW is a decent frontend to iptables.

When I've run gufw from Alt+F2 it always asks for my password, so it will run with root privlages.

---

