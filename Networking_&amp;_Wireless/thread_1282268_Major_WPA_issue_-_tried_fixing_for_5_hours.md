---
title: "Major WPA issue - tried fixing for 5 hours"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by wiseguy12851 on 2009-10-04
Okay upfront I am a software programer in most all web languages and selective windows computer languages, I am also a system and network administrator for my job the only problem is I have never used linux before, I have ended up staying up all night from 12:00 to currently 5:00 without realizing it trying to fix this issue.

I burned ubuntu to a CD to get a breathe of fresh air from the ever narrowing walls of windows xp, vista, and 7 and get some control back in my pc. I did a test boot into live mode to see if everything worked hardware wise and found WPA not connecting with given password.

The previous articles said add support something, it finds the network okay and all WPA packages as well as network related packages are up to date and installed correctly.

I have also tried the alternative software package wicd but hat a reconnecting issue that I can't fix either. The computers ready to clean reformat when I can get the live CD to work normally. The main reason that initiated this switch was the fact that I wanted to have a PHP server to develop sites locally before upload and not have to worry about never ending problems in Windows, I am still at step 1 in Ubunto wich is connecting to the network and 5 hours later still at step 1

further info:
WPA is installed and up to date
Ubuntu 9.4 (non-beta version)
Keeps saying password is not taken

if this has anything to do with it the password is a long strand of symbols, numbers, and letters mixed case beginning with &#2

when it comes back denied the password is replaced by a different encrypted string probably nothing important.

---

### Post by slakkie on 2009-10-04
With this information there is nothing much we can do.

1) What packages are you using for your wireless, list them:

apt-cache policy <package1> <package2> ... 

2) What did you configure?

cat /path/to/configuration file

3) What do you have listed in your interfaces file?

cat /etc/network/interfaces

4) What do the logs tell you?

/var/log/messages
/var/log/daemon.log

* Have you run stuff in debug mode to see what happens?
* Have you run iwlist scan to see if your network is visible for your PC?

---

### Post by wiseguy12851 on 2009-10-04
it mysteriously started working, I can't explain it but I am submitting this post through the live version of ubuntu on wireless connection.

---

### Post by slakkie on 2009-10-04
Good to know.

---

