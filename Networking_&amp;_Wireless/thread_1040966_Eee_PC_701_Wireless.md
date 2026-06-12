---
title: "Eee PC 701 Wireless"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by AndyGibo on 2009-01-16
Hi everyone,

I'm having lots of trouble with this.  I have an Asus Eee PC 701 4G and can not get the wireless working properly.  Connections are constantly dropping and when I do have a connection it is at a very slow speed, so still unusable.  I have tried a number of fixes that are posted all over the internet and none seem to be working for me.
I am running Ubuntu 8.10 (2.6.27.9-generic kernel) and the wireless card is an Atheros AR5BXB63.
Can anyone please help me?!?!?!

---

### Post by lurchnz on 2009-01-16
I've had similar issues with 8.10 and 9.04, among other problems of where it will keep prompting for the WPA password. 

There was a fix where you go into to gconf-editor then system -> networking -> wireless -> networks.

From there you had to manually change the settings to use WPA only. However you had to make sure that the keyring was remembering the right password. I only got this to work once and for that one time the connection was really slow so tried various fixes I found from googling but after several weeks stuffing around I went back to 8.04 where the wireless works with no issues and no speed drops. Fingers crossed they get it right with 9.04.

---

### Post by AndyGibo on 2009-01-16
I have installed Ubuntu 8.04.1 onto the Eee PC(no updates, tweaks or anything else done yet, just straight install), the system says restricted drivers are being used but now I have no wireless connection at all.  Any suggestions, I'm not a total newbie but still need a helping hand!!

---

### Post by silkstone on 2009-01-16
The standard Ubuntu kernel doesn't support wireless on the eee PC. You can install the Array kernel which is modified for the eee PC and other netbooks, but by far the easiest solution is to install a variant of Ubuntu that has been tailored specifically for these machines.

Probably the best right now is eeebuntu 2.0 which comes in three versions depending on what GUI you prefer and how lean you want the OS to be. More info here...

[http://www.eeebuntu.org/](http://www.eeebuntu.org/)

[http://forum.eeebuntu.org/](http://forum.eeebuntu.org/)

---

### Post by AndyGibo on 2009-01-16
I downloaded eeebuntu 2.0 and just ran the live version(dont want to keep installing every OS mentioned) and I experienced the same problems.  Just so people are aware my attempts I have tried;

eeebuntu
ubuntu eee
easy peasy
Ubuntu (8.04.1 and 8.10)
RiceeeyTweak 2.1
Madwifi drivers

**Uncommon Element: This system is to be used in a school using an Extricom wireless solution, I have no idea how or if this is effecting wireless on the laptop ([http://www.extricom.com/](http://www.extricom.com/)) **

Any suggestions are welcome, thanks!!

---

### Post by AndyGibo on 2009-01-19
Sorry people but I need to bump this!

Bump Bump Bump!!

Anyone had any experience with Extricom products at all?

---

### Post by AndyGibo on 2009-01-19
Bump!!

Am I out of luck with this then?  No suggestions from anyone, anywhere?!?!

---

### Post by madestro on 2009-02-12
Hi I had the same problems after installing Eeebuntu on my 900ha but only after the first update, Im using the NBR version but I guess this should work with everyone, standard, nbr or minimum.
Check out the solution here 
**[http://forum.eeebuntu.org/viewtopic.php?t=312&reeedirected=yes](http://forum.eeebuntu.org/viewtopic.php?t=312&reeedirected=yes)**
now the only thing to change is the location of the session manager, in the nbr edition it's in the Menu - System - Control Center, once there under Personal click on Session and then on Add to get wicd to start all the time.
I hope this solves your problem and remember I didn't write this just found it on the web so all the credit goes to *chillamba* and huge thanks for the effort.

---

