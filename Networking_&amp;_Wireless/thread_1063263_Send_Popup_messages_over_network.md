---
title: "Send Popup messages over network?"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by ShamanSTK on 2009-02-07
Me and my fiance both live on campus and we both have ubuntu intrepid. I want to konw if theres a way to have a message pop up on her desktop with an alert sound and stay there till she reads it. I was hoping for a little privacy, but i'll survive if its a broadcast.

---

### Post by dirk_k on 2009-02-28
You could use linpopup, the linux variant of winpopup, that is also compatible with other windows systems. But I think this could be overkill because you will also be running the Samba server that is intended to share files with windows clients. Maybe it is easier to just use a instant messenger application over the internet, such as Pidgin (using google talk, msn, etc.).

[http://manpages.ubuntu.com/manpages/gutsy/man1/linpopup.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/linpopup.1.html)
[http://www.linuxquestions.org/questions/linux-networking-3/is-it-possible-to-send-and-receive-net-send-messages-in-linux-267067/](http://www.linuxquestions.org/questions/linux-networking-3/is-it-possible-to-send-and-receive-net-send-messages-in-linux-267067/)
[http://www.pidgin.im/](http://www.pidgin.im/)

---

### Post by ranjit. on 2011-10-26
thou the sounds and other alerts are not possible, there seems to be a way in which u can install SSH on both ur systems and also libnotify using the command[FONT=monospace] [/FONT]sudo apt-get install openssh libnotify-bin, then login to the other computer via SSH through your terminal and then type [FONT=monospace]
[/FONT]export DISPLAY=:0.0
notify-send "Title of message" "message text
i hope this works :guitar:

---

### Post by lintoon on 2011-10-27
Google talk is very good for me.
Just need a google mail account.
I use Pidgin on Ubuntu as a Google Talk client.

Highly recommended.

---

### Post by lintoon on 2011-10-27
Settings for pidgin to use googletalk.

Username - Your gmail user (Dont need @gmail.com just the username)
Password - Your googlemail password
Domain - googlemail.com
Resource - talk.google.com
Connection security - requires encryption
File transfer proxies - proxy.eu.jabber.org
Connect port - 5222


Remember to add your friend/partner as a buddy.

---

### Post by Tulainas on 2012-05-04
> **ranjit. said:**
> thou the sounds and other alerts are not possible, there seems to be a way in which u can install SSH on both ur systems and also libnotify using the command[FONT=monospace] [/FONT]sudo apt-get install openssh libnotify-bin, then login to the other computer via SSH through your terminal and then type [FONT=monospace]
[/FONT]export DISPLAY=:0.0
notify-send "Title of message" "message text
i hope this works :guitar:

AMAAAAAAAZING!!!! You just created a monster!!!

 I'm using this command in my shell scripts!!! :-D

Thanks!!!

---

### Post by lisati on 2012-05-04
Back to sleep, [s]Pennywise[/s] thread.

---

