---
title: "Network device not managed"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by Gnomatron on 2009-07-06
I can not connect to the internet. I suspect that this may be related to the update that i just installed since i had internet prior to. I tried changing a system file to help my cause, but i couldn't get it to do it for me. I tried su root, changing the authorization list, adding me to the root group, and giving me more privileges. none of it worked i still cant get on the internet, and i still can't edit system files.

any help in this matter would be greatly appreciated


I am using the Xubuntu 9.04 on a 80Gb PS3

---

### Post by HavocXphere on 2009-07-06
What method are you using to connect to the internet? Wifi, adsl or smokesignals?

---

### Post by Iowan on 2009-07-06
Network Manager gets pouty when it doesn't get to be boss.  You might try setting up internet connection via NM first - if that doesn't play, you can resort to editing */etc/network/interfaces*. (Comment out or remove any definitions except "lo" in */etc/network/interfaces*).

---

### Post by a_myst on 2009-07-08
I have the same problem in Ubuntu 9.04...on a Fujitsu-Siemens. I had configured both wired(through dsl) and wireless with pppoeconf and I was quite surprised that the wireless was working as well.
 But now, after installing some updates, it's all gone. I tried using the Network Manager but it still didn't work. Editing the interfaces file didn't work. I have also uninstalled some program called apparmor that might have caused trouble. I could really use some help.

---

### Post by antony_css on 2009-10-12
Hoping this closed thread may give a clue to you:
[http://ubuntuforums.org/showthread.php?t=1109585&highlight=device+not+managed+network+manager+wired]("http://ubuntuforums.org/showthread.php?t=1109585&highlight=device+not+managed+network+manager+wired")

---

