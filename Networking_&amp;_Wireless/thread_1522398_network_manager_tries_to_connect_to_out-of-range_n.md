---
title: "network manager tries to connect to out-of-range networks"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by batti on 2010-07-02
Hi,

 I have a problem with network manager. I use Ubuntu 10.04 on a Dell  Latitude D530. I used to have the same problem with Ubuntu 9.10 before I  upgraded.
 
I typically connect to two wireless networks: HOME and WORK.  Both networks are set to automatic connection mode. I am at work, I  connect to the network WORK. At the end of the day, I just close the lid  and go home. At home, I open the lid and have the following problem:  network manager still displays the network WORK whereas it is clearly  out-of-range and it automatically tries to connect to it. It does so  until network manager asks if the password is correct. If I want to  connect to HOME, I have to tell network manager to do so. Then, I  receive a notification that I am disconnected to WORK. Next morning, I  go to work, and I have the same problem, network manager tries to  automatically connect to HOME.
 
What I would expect from network manager: when I am at home, NM  automatically connects to HOME and does not display WORK, when I am at  work, NM automatically connects to WORK and does not display HOME.
 
Thanks for your consideration.

---

### Post by grahammechanical on 2010-07-02
What is actually happening when you close the laptop's lid? Does the operating system shutdown, suspend, or hibernate? When you open the lid the OS assumes that you want to resume from where you left off both in regard to what you were working on and where you were working. How is it supposed to know that you are in a completely different location.

Before closing the lid try clicking Enable networking. Disabling networking will disconnect you from the network as far as Ubuntu is concerned. When you open the lid click Enable networking again and the system will search for any available networks and you can select whichever one you want HOME or WORK. Or any others that are in range. What would you do if you wanted to access free WIFI from a cafe or some other place? Remember, it is just a machine.

Regards.

---

### Post by batti on 2010-07-08
thanks for your answer. the machine suspends when I close the lid. 
The procedure you are pointing out would certainly work. A windows machine does, however, perfectly handles this issue, so i don't see why ubuntu couldn't. 

Furthermore, I believe that ubuntu should only try to connect to in-range networks.

---

### Post by batti on 2010-07-15
anyone has an idea of how to solve this issue? should it be posted as a bug?

---

