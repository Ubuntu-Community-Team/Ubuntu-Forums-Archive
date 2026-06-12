---
title: "Create script to set wifi interface's power lower"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by Tumbilambi on 2010-09-30
Hello all, I am new on this. I am Spanish so my English might be not as good as you want but here is my question. 
I am a noob in Ubuntu and I would like to create and script or file which when clicked sets my WiFi interface's power lower, down to 7dBm. I already know how to do it by typing on the terminal, I just write:
#sudo -s
#my password
#iwconfig wlan0 txpower 7dBm

That is all. Then, I would like not to have to do all this shitty process, is it possible to create a file which when clicked just do or launch it by itself?

In general, how can I make a file which contains many different gnome-terminal orders as if I were typing them one by one and then turn this file into a launcher?

Thank you all in advance!

---

### Post by Tumbilambi on 2010-10-04
C'mon I cannot believe none of the 48 viewers  do not know how to do what I am asking... I just heard the Ubuntu Community was the best place for free software and everybody is pleased to help others. It does not seem so.

---

### Post by trundlenut on 2010-10-04
Sounds like you want to create a shell script and you can set it to run at boot or when you want it to.  There's plenty of information available on shell scripts, try searching.

---

