---
title: "video problem"
date: 2006-02-02
forum: Multimedia &amp; Video
---

### Post by dude of wonders on 2006-02-02
when i turned my computer on with the ati card in it doesnt matter which card i have the monitor plugged into, unbuntu will start up and load then right before it goes to the username and password thing, it stops at a blank screen with an underscore up in the top left corner not blinking. so i have to have the ati card out if i want to be able to start unbuntu up. i read the info on the latest ati card post, but the way he's explaining. i would have to have the ati card in the motherboard to get the drivers for it. 

i'm lost lol i can run it without the video card, but i'd like to have it installed since i have windows on my other hard drive and without the card windows wont play back video correctly.

---

### Post by frodon on 2006-02-02
When you get the blank screen do a Ctrl + Alt + F1 to get the virtual terminal, login and run these commands : ```
sudo /etc/init.d/gdm stop (or kdm for KDE)
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start (or kdm for KDE)
```It will reconfigure xorg and i hope configure your ati card so you will be able to start your session and install the drivers if you wish.

---

### Post by dude of wonders on 2006-02-02
i tried the control-alt-f1 thing when it was at the blank screen and nothing happened.
i tried it right before it hit the blank screen, and then right when it was starting to boot up, and both of those end the end brought me to the blank screen. :( i'm a lost hope.

---

### Post by frodon on 2006-02-02
You could try Ctrl + Alt + F2 (or F3, F4, ...) or start in failsafe mode, the goal is just to get a terminal to run the commands i gave you.

---

### Post by dude of wonders on 2006-02-02
i got to the part where it lets me type stuff in finally and it said
sudo/etc/init.d/gdm stop  file directory does not exist

so i skipped it and did the reconfigure one and it sent me to auto detect my video device so i put in ati , and then there was some kind of bus number it wanted so i took a guess and put 1 then it ran through my keyboard and junk so i skipped through it hitting enter and then it put me back to the dos like screen. 

i tried typing sudo/etc/init.d/gdm start  file directory does not exist. 

so i skipped that , but couldnt figure out how to restart so i just hit the power button.

restarted it back up and this time after unbuntu loaded it acted like it was trying to get to the username and password screen but then gave up and gave me an error message.

failed to start the xserver (your graphical interface), it is likely that it is not set up correctly would you like to view the xserver output to diagnose the problem. 

i restarted once more to see if it would mend itself but it repeated the same process i clicked no on the diagnoses because i dont understand that stuff.
i'm sorry this is getting to be a hassle, but your help is appreciated.

at least it tried this time

---

### Post by dude of wonders on 2006-02-02
i went through trying puting 1-4 numbers in when it ask me what bus but didnt help :( even tried the some kind of option that offered to buffer for me.:-k

---

### Post by dude of wonders on 2006-02-02
thanks for the help man you were telling me to do the right thing. i'm just to much in a hurry to look deeper in the programming. i went back looked at the error log and looked at the output and scrolled down and found my ati card and wrote down where the bus was, and it wasnt 1-4 lol it was 1:8:0 man took forever if only i had been more patient from the get go. well thanks man your advice was right on just my ignorance.:mrgreen:

---

