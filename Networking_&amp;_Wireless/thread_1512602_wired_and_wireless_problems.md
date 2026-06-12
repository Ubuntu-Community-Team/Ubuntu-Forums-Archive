---
title: "wired and wireless problems"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by capitalfear on 2010-06-18
i can't connect with either! i keep entering in all the info it asks for from my laptop connected wirelessly to my router! what do i do! i cant get to anything! i hardwired it and am trying to use it wirelessly...please help =[

---

### Post by Sealbhach on 2010-06-18
It would help if you provide more information.

Run 
```

sudo lshw -C network 

```

in a terminal and copy the results to here.

.

---

### Post by capitalfear on 2010-06-18
> **Sealbhach said:**
> It would help if you provide more information.

Run 
```

sudo lshw -C network 

```in a terminal and copy the results to here.

.
okay so i entered that in the command line and a couple different things pop up like
SYS and SPIC and stuff like that idk it doesnt stay up i am trying to connect for the first time

---

### Post by Sealbhach on 2010-06-18
Strange. Well run this command, it will put the output of the network hardware info into a file on your desktop:

```
sudo lshw -C network > ~/Desktop/networkinfo
```After you run the command you will find a file called "networkinfo" on your desktop.

Open it and copy and paste the info in this thread.

Also, another thing to try.... check in your menu, System/Administration/Hardware Drivers and make sure that you have all available hardware drivers activated. It might be you may not have any, but check it anyway.

---

### Post by capitalfear on 2010-06-23
thanks i figured it out...hardware problem...someone didnt tell me there was a problem with it but i fixed it with spare parts..thanks :D

---

