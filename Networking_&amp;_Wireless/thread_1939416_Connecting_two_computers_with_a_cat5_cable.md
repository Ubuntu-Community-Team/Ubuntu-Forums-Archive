---
title: "Connecting two computers with a cat5 cable??"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by richiegriffin on 2012-03-11
Hi,

I need to move 100+GB of files from one PC (11.04) to another PC (11.10).

Here's my dilemma, I'm broke and only have an ADSL2+ $30 router/modem with one jack, no wireless... I have a Cat5 cable and wonder if there's an app on 11.04/11.10 for transfering files between computers via a Cat5. I'm terrible at terminal...

Anyone heard of anything like this? A "cloud" is one idea but I'll have to upload all the data then download it (extra time). 

From what I'd always thought, you can't do this, however I stumbled across articles of people claiming to do this with USB cables and Cat5, just wanted to see if anyone is familiar with this,

Regards.

---

### Post by utnubuuser on 2012-03-11
you'd need a cross-over cable to connect directly

---

### Post by winh8r on 2012-03-11
You would need to use a crossover cable, which is basically a normal cat5 network cable with the wiring rearranged to allow data transfer.

there are other methods you could use though:

take the hard drive from the machine you want to transfer to and put it into the machine you are transferring from and set the receiving hard drive as a slave using the jumper pins on the back of it.Then reset the pins back to master and put it back in the other machine when you are finished.

Or

dvd rw 's 

or borrow an external hard drive.

---

### Post by oldfred on 2012-03-11
Some of the very new Ethernet cards support direct connection without a crossover cable. Not sure how you tell.:(

---

### Post by ajgreeny on 2012-03-11
You could also use ssh and filezilla, or similar means.

---

