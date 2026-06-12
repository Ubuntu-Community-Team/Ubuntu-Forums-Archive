---
title: "Slow download speeds"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by Nintendork on 2011-11-01
Before I start, let me just say I am completely new to Ubuntu (or any Linux based platform), so please respond accordingly.

I am getting slow speeds when I try to download anything from anywhere (software center, a .pdf from a website, etc.).  The speeds starts off fast (~1Mb/s), but after a couple seconds drops to slow speeds (~10kb/s or less).  Occasionally the speed will pick back up for a few seconds.


I have tried a few solutions I have seen: 

Went to the software sources --> select best server, but I get "No suitable download server was found: Please check your Internet connection."

Added ifconfig eth0 txqueuelen 50 to some file in /etc...don´t remember which one, but it does it at boot (just ran ifconfig to verify and for eth0 I have txqueuelen: 50, so it is in the right place...also I have no errors when I run ifconfig)


Web pages load slow sometimes as well.  I am using Ubuntu 11.04, and am connected to the Internet through a Linksys WRT54G router and have a SURFboard SB5101 modem.

Any suggestions on how to fix this...?

---

### Post by jmate24 on 2011-11-01
first go into network manager then on the wired interface select it then on the left select edit then where it says MTU set that to 1500.

---

### Post by Nintendork on 2011-11-01
Changed the value and reset the connection.  No improvement.

Restarted.  Still no improvement.

Tried selecting best server again (although I don't think this would affect normal Internet downloads...only ones from the software center...right?)...still get no suitable download server was found.

So that didn´t do it.

---

### Post by Nintendork on 2011-11-02
I am going to tentatively say this is solved...I upgraded my router firmware and now my downloads seem to be running around where they should...going to wait a couple days before I mark this thread as solved just to be sure.

---

