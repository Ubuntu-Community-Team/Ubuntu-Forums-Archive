---
title: "Wireless driver"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by Nardone on 2010-03-18
Hello everyone on Ubuntu fourm. I just have a question. I am having problems with my acer extensa 5620z wireless. I went on a few fourms and tried a few things they told me to do and It did not work. My question is this If i install wine can I grab the exe file off of acer website and install it that way?

---

### Post by mcoleman44 on 2010-03-18
Probably not, thats not a safe way to install a windows driver.
Go to system>admin>hardware drivers
If there is a wireless driver listed, install it and restart.
If not then try this:
sudo apt-get update
sudo apt-get upgrade
When you restart go to system>admin>hardware drivers and see if the driver is listed now.

---

### Post by Nardone on 2010-03-18
thank you I will try that

---

### Post by mcoleman44 on 2010-03-18
Im actually in class right now, so if I dont answer right away, sorry.

---

### Post by Nardone on 2010-03-18
> **mcoleman44 said:**
> Probably not, thats not a safe way to install a windows driver.
Go to system>admin>hardware drivers
If there is a wireless driver listed, install it and restart.
If not then try this:
sudo apt-get update
sudo apt-get upgrade
When you restart go to system>admin>hardware drivers and see if the driver is listed now.

Thank you, syste>admin>hardware driver work

again thank you

---

### Post by uRock on 2010-03-18
Please do not forget to use the thread tools at the top of this thread to mark it as solved.

Thanks,
Ronnie

---

