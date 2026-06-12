---
title: "Remote suspend from XP"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by europbaron on 2009-07-12
Hi all,

Great forums - many thanks to all who've posted here without whom I'd have given up on Ubuntu by now.

My problem is how do I remotely suspend Ubuntu 9.04 from a different PC running windows XP, using a command that can be run as a command line/batch file? 

I've found a lot of info on setting up remote desktops, but I do not want to do this. 

The application is that a media PC (XP) wakes up the ubuntu 9.04 server on boot up, using a WOL magic packet. I need it to suspend it (S3) automatically when the XP machine shuts down. Scheduling a command line/batch file is no problem once I know what it should be. I've tried various solutions of simply having the server go to S3 after a period of inactivity, but these are not reliable/predictable enough for my purposes.

Less importantly, I'd like to be able to similarly shut it down from my ubuntu 9.04 laptop.

Many thanks in advance.

---

### Post by europbaron on 2009-07-13
I've found a solution of sorts on my own. it's not very elegant so if anyone can suggest improvements I'd gladly hear them.

The solution I've used is (based on [https://answers.launchpad.net/ubuntu/+question/68239):](https://answers.launchpad.net/ubuntu/+question/68239):)

1. Install openssh-server on linux
2. On XP install PuTTY.
3. Make an autohotkey script as below:

F12:: 
run C:\Documents and Settings\David\Desktop\SD          
          ##this is a path to PuTTY saved profile to my linux server## 
sleep 3000 
Send xx_myusername_xx{enter} 
sleep 6000 
Send xx_password_xx{enter} 
sleep 1000 
send sudo pmi action suspend{enter} 
sleep 1000 
send xx_password_xx{enter} 
sleep 1000 
send !{F4} 
sleep 1000 
send {enter} 
sleep 3000 
DllCall("PowrProf\SetSuspendState", "int", 0, "int", 0, "int", 0) 
return

This means that when I press F12 (actually sent via IR remote control) in XP both the linux server and the XP machine go into standby.


I'm not too happy about the security of this setup, but it works. Any suggestions to improve it welcomed.

---

