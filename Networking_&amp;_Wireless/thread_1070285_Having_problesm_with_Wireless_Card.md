---
title: "Having problesm with Wireless Card"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by kevin_zhong on 2009-02-15
Ubuntu 8.10 detects the Atheros, at least that's what I think I saw. I had to switch to Vista to ask you guys for help, bummer! The model is Atheros ar5007eg, my computer model is Acer Aspire 5315. I'm not literate when it comes to complex things. I've seen replies to similar things with back modules or something like that, but I don't understand that. Can anyone please help me? So far this is the only problem I have had with Ubuntu. 

Thanks,
A 16-year old in need :)

---

### Post by superprash2003 on 2009-02-15
hope this helps [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by kevin_zhong on 2009-02-15
I am currently downloading something wired, so I'll do what you said. However, I noticed that Vista says it is ar5007eg but Ubuntu says ar242x. Is their a difference?

---

### Post by kevin_zhong on 2009-02-15
I have no luck at all. Does it matter that I have it with Wubi? I just don't know whats going on. Also, it says the Atheros Wireless card is enabled. I don't understand it.

---

### Post by superprash2003 on 2009-02-16
well it should have worked.. go to the terminal and type **lshw -C network** and post output here..

---

### Post by Aarookie on 2009-02-16
try this
Open a terminal and enter these commands:
(this is also assuming like me the target computer has no way of getting to the internet, if you have RJ45 plugged in or some alternate method of connecting to internet you can skip first step.

1. Insert your Ubuntu cd and open terminal
2.sudo apt-cdrom add
3.sudo apt-get install build-essential (Not sure this part is necessary but it sure was for proper tarballing when I was trying to install multiple tar.gz files.
4.sudo apt-get install ndisgtk

5.Open system>administration>Windows wireless drivers menu/program.
6.My computer sort of stuttered at this point but eventually a little window opened up and I was able to browse to my .inf file from winxp driver.
7.For some reason configure network didn't work at this point the unlock button was greyed out, also mouse pointer was skipping a few beats every so often but after a restart I am able to click on my 2 little computers in the gnome task bar and attempt to connect to my network same way I have done on my laptop here. At this point however I was unable to connect to wpa type network, switched router back to wep and hooked right up
I'm on 32 bit computer, not sure if this will work in 64 bit environment, my bro's computer wouldn't accept 32 bit driver with this method, and his card doesn't have 64 bit windows' drivers

---

