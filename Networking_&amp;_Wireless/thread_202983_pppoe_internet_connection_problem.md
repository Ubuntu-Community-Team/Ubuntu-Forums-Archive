---
title: "pppoe internet connection problem"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by Vlatko on 2006-06-24
2 days ago installed dapper and i used the "sudo pppoeconf" command to set up my dsl connection.it was succesful and i said yes when asked if i want to start this connection at boot time. however whenever i reboot my internet doesn't work. i have to"sudo pppoeconf" all over again and then i have to restart to make the connection work. then it works untill i reboot again. after another reboot i have to "sudo pppoeconf" again!!

i'm new to linux and few months ago when i played around with breezy i didn't have such troubles.

can anyone help me out?

is there a tool of some sort which can connect or disconnect a internet connection from a taskbar?

---

### Post by jasil on 2006-07-11
I had the same problem. I tried several solutions, including installing pppoe package from Ubuntu repository, but nothing worked. At the end I lost the Internet connection totally. Then I tried to disable the ethernet card from the Gnome Networking tool and run the pppoeconf again. That brought Internet connection back and it has worked since then right after boot too.

---

### Post by knud on 2006-07-19
is there a solution? after booting my pppoe defined connection does not work, too. in ubuntu 5.10 it does. ps -ef and ifconfig say there is a connection. i always have to poff -a and then pon dsl-provider. whats wrong?

---

### Post by jasil on 2006-07-19
Did you try disabling the ethernet card (eth0)? For me it worked. Running pppoeconf adds necessary lines to /etc/network/interfaces that bring up your card when ppp0 is started. Anyway, I have found that it doesn't work every time I boot up my computer. Don't know why.

---

### Post by knud on 2006-07-27
after i managed to let the auto-updater finish with about 130 updates, the problem exists no longer. when booting and logging-in is over, the dsl connection is up and works fine. i think, an update solved the problem. are there some release-notes about the updates available ?

---

