---
title: "Aircrack-ng error messaging"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by HybridSquirrel on 2009-02-14
I am attempting to install aircrack-ng right now...i downloaded and installed openssl (using sudo wget...ect) and followed the instructions on the aircrack-ng.org website to install, when i get to the sudo make step...it gives me an error and on t he aircrack website it says its because openssl isnt installed...i am a total noob at ubuntu ive only been using it for a few months so i most likely messed something up.  I didn't receive any error messages when installing open ssl so idk =\

---

### Post by Dan_B on 2009-03-16
Hi,

I am assuming you worked it out yourself by now, but just in case..

Basically, don't bother compiling it yourself (Though it does mention that technique in some of the guides) - There is an easier way, an automated install..

Just connect to the net, launch terminal, and type:

sudo apt-get install aircrack-ng

Thats it :)

If you do want to start compiling from source code yourself, type this in terminal, once again, will only work if whe are connected to the net:

sudo apt-get install build-essential

---

