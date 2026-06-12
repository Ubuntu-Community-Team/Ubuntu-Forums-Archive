---
title: "connect to xp to transfer files to ubuntu"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by zeus123 on 2010-08-30
I have ubuntu 10.04 on my netbook and all my files on my XP desktop.

How can I connect the two so that i can transfer files from the xp machine to the ubuntu netbook? Both have wifi and ethernet.

Im not fluent in windows networking but could manage to join two xp machines using an ethernet cable and naming the two with the same workgroup then setting a folder as shared!

Many thanks for the any help!

---

### Post by JD32 on 2010-08-30
How much you talking? A couple of trips with a flash drive would be the easiest and most simple :D. But, if you really must transfer through your network connecting the two with a cable would provide the fastest transfer (can be done wireless though). Then a simple install of samba on the linux machine would be all you need to get them moving

---

### Post by zeus123 on 2010-08-30
Ive got loads of stuff... about 20gb. I only have a 2gb memory stick and that has ubuntu on it! 

Ill try installing samba and then running the auto eth0  again.

Thanks!

---

### Post by zeus123 on 2010-08-30
Ok, I opened synaptic and installed samba but when I connect the two computers using the cable auto eth0 cannot connect the two.

Am I missing something?

---

### Post by pricetech on 2010-08-30
Are you using a cable between the two, as opposed to putting them on the same subnet with a router ??  That's what I'm reading anyway.

You'll need to set a fixed IP on both computers, in the same subnet, and make sure you're using a crossover cable as a "normal" network cable won't work.

---

### Post by zeus123 on 2010-08-31
ahh, im getting somewhere now!!

I went to edit connections and added a new connection with the ip and netmask (?) to match what it seems to be on my windows computer.

Plugged in the cable (I have a yellow one; "Cat .5" and a green one "Cat 5 Patch Cable") and it connected straight away. 

So then went to the browser in ubuntu and then to network. In there it had a Windows Network icon, clicked that and got an icon named Workgroup and then got Rik-Laptop. This is the name of my ubuntu laptop. Inside that it just had Print$

So I seem to be almost there! Except it doesnt see any of the folders I have shared on the windows desktop. 

At least its connected now!

---

### Post by pricetech on 2010-08-31
Try this:
Places - Connect to Server
Choose Windows Share
Put in the IP of the windows computer and c$ as the sharename.

"c$" is a hidden share that exists on all NT based windows boxen.

You should be prompted for a username and password.  Once you enter that information you should be able to connect.

---

