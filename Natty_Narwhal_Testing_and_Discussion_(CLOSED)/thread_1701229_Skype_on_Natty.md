---
title: "Skype on Natty:"
date: 2011-03-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kuvanito on 2011-03-06
Open a terminal and type these commands one at a time according to your version 32 or 64 bit

32 bit
wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
sudo apt-get install libqt4-dbus libqt4-network libqt4-xml libasound2
sudo dpkg -i getskype-linux-beta-ubuntu-32
sudo apt-get -f install



64 bit
wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-64](http://www.skype.com/go/getskype-linux-beta-ubuntu-64)
sudo apt-get install libqt4-dbus libqt4-network libqt4-xml libasound2
sudo dpkg -i getskype-linux-beta-ubuntu-64
sudo apt-get -f install

---

### Post by VMC on 2011-03-06
Thanks. I'll give this a go. I have never had any luck with Skype on Linux. 
That's one of the main reasons I use Windows - It always works, and I like the interface better. Also, for some reason, Skype for Linux is stuck in the past. They have that version 2 for a long while now.

---

### Post by rtalcott on 2011-03-06
The Skype beta works fine on my 10.10 machines (64 bit) and hopefully it will work as well on 11.04. I just tried making a call from gmail to a POTS phone....and that worked...so that's a great free option for domestic US calling from a PC.
rt

---

### Post by cariboo on 2011-03-06
Skype is in the partner repositories, it work great on Maverick, I haven't tried it yet in Natty.

---

### Post by rajeev1204 on 2011-03-25
I dont see this in the partner repository in natty.

---

### Post by donalgodon on 2011-03-25
I've had zero luck with Skype on Natty. Is there a way to install it? The software center rejects the package as poor quality. How can I manually install from the .deb?

---

### Post by cariboo on 2011-03-25
Skype is there, have a look at the screenshot.

---

### Post by rajeev1204 on 2011-03-25
> **cariboo907 said:**
> Skype is there, have a look at the screenshot.


It is there in all versions of ubuntu but it is not there in natty repos.You can check yourself.

---

### Post by rajeev1204 on 2011-03-25
> **donalgodon said:**
> I've had zero luck with Skype on Natty. Is there a way to install it? The software center rejects the package as poor quality. How can I manually install from the .deb?


Just install from command line : sudo dpkg -i  <packagename>

---

