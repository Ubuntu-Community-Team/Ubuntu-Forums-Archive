---
title: "Nvidia Drivers"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by Earth_djinn on 2007-04-09
I am having problems installing the nvidia graphics driver on my computer, everytime I go to install it, it says it has failed intall because of an x server. Now I have read many posts on how to disable it using ctrl+alt+backspace, sometimes that takes be back to the login screen and sometimes I am presented with a black screen and I have to enter my password. I have used init 3 or is it init 1? 
Also when the black screen appears do I have to enter the root password for it to keep the x server down or does ctrl+d work too? Seeing as I cannot enter my password for some reason on this screen, so I press ctrl+d.
Anyway I have tried both methods and I still can't install my nvidia drivers. Please help!

---

### Post by PurplePenguin on 2007-04-09
[Here's a link]("http://ubuntuforums.org/showthread.php?t=398590") to both stopping X completely, as well as an even [easier way ]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")to install nvidia drivers.

---

### Post by chewearn on 2007-04-09
Press CTRL+ALT+F1 should brings you to console login.  Use the username/password which you key in during installation to login.

You can then stop Xserver/gdm by:
```
sudo /etc/init.d/gdm stop
```
From here you can run the nvidia installation; I used the Envy script:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
To run envy in text mode:
```
sudo envy -t
```

---

### Post by Earth_djinn on 2007-04-09
Thankyou for all the help I will try out these tips you have given me.

---

### Post by Earth_djinn on 2007-04-09
It did not work unfortunately. I tried both methods and they did not work for me.
The envy program would not run and gave me a message saying dependancies not satisfied, buid dependant. And like I said when I have to enter a password in the terminal or with the black screen the characters just won't enter. It simply refuses to allow me to enter a password.

---

### Post by bdamon on 2007-04-10
Try running sudo apt-get install -f   that should install the dependencies and you should be good to run envy

Ben

---

