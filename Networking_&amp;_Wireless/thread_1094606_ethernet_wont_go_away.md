---
title: "ethernet wont go away"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by leemckelvey on 2009-03-12
hi all, i have recently installed ubuntu 8.10 on my macbook 5,1 and in order to minimise the power consumption i have been trying to tailor my startup to serve my needs.

now the first thing to note is that i know very little about ubuntu, i would like first off to figure out how to get my eth0 connection to not start on boot. 

after searching the net i found that i can disable it using "sudo ifconfig eth0 down" in the terminal but is there a way to get it to do this on booting?

I have also tried to add it to /etc/network/interfaces but it didnt seem to work and my eth0 connection is not configured and so doesnt appear in network manager.

i know that it is draining power since powertop has it listed.

please help

many thanks

Lee

---

### Post by leemckelvey on 2009-03-12
anyone have any ideas?

(secret bump)

---

### Post by leemckelvey on 2009-03-13
bump.

someone must know a solution to this :(

---

### Post by jimv on 2009-03-13
Maybe this?

[http://ubuntuforums.org/showthread.php?t=160480](http://ubuntuforums.org/showthread.php?t=160480)

---

### Post by leemckelvey on 2009-03-15
this part didnt work either :(

INTERFACES="eth0"
HOTPLUG_INTERFACES=""
ARGS="-q -f -u0 -d10 -w -I"
SUSPEND_ACTION="stop"

Lee

---

### Post by lastfrontier on 2009-03-15
do you have nm-applet running because if you do then you can right click on it and disabble the network before you turn off the computer and it should not turn on when you boot up until you right click it again and inable it at least that is how it works for me i am currently using ubuntu ultimate hardy herion based....

---

### Post by leemckelvey on 2009-03-17
will that only disable the ethernet? or does it disable wifi too?

im sorry im lost when it comes to networking.

ill try later when i get home from work

Lee

---

