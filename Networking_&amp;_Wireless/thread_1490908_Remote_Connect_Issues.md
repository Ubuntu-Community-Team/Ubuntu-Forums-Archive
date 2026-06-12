---
title: "Remote Connect Issues"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by Infinitum7 on 2010-05-22
Alright so i just wanted to try and get remote desktop connections running so i can access files on the other computers in my house. For my first try i went after my laptop. I'm using rdesktop. 

First couple times i tried i typed in 

```
 rdesktop ipaddess 
```

After about 15 seconds it would pop back with 

```
 ipaddess: Unable to connect 
```

I realized that my laptop's firewall was blocking the packets, so i created a custom rule that allows all TCP packets on port 3389. So i fired up rdesktop again. Now it pops back with:


```
 ipaddess: Unable to connect 
```

But instantaneously, not after 15 seconds (not sure if thats significant or not.) I checked my firewall's log and it allowed the tcp packets. So now i'm throughly stumped. Any input would be great, thanks!

---

### Post by Riaku on 2010-05-22
Are the other computers OS's configured to accept remote connections?

---

### Post by Infinitum7 on 2010-05-22
Forgot to mention that, yes they are, i have windows set to allow remote connections.

---

### Post by captain_171 on 2010-05-23
What we need to know is some info like. What operating system is running on both computer. Can you ping each computer. Is there any firewall enabled. What programs are you trying to view or what is the task you wish to do.  Let us know and it will help a LOT.

---

### Post by Infinitum7 on 2010-05-23
The computer i'm connecting from is Ubuntu Lucid. 
As i said before the computer i'm connecting to is Windows, more specifically windows 7, and it is configured to allow remote desktop connections. Yes i can ping the computer. Yes there is a fire wall enabled as i said.  At this point i'm just trying to establish the connections, i'll probably just be copying files and whatnot.

---

### Post by theozzlives on 2010-05-23
> **Infinitum7 said:**
> The computer i'm connecting from is Ubuntu Lucid. 
As i said before the computer i'm connecting to is Windows, more specifically windows 7, and it is configured to allow remote desktop connections. Yes i can ping the computer. Yes there is a fire wall enabled as i said.  At this point i'm just trying to establish the connections, i'll probably just be copying files and whatnot.

If you're just copying files, why not just copy them over the network using SAMBA?

---

### Post by Infinitum7 on 2010-05-23
I suppose i could try that, but i more want to do it now because it's irritating and i should be able to. haha. I mean my firewall is allowing the tcp packets which means at least the SYN packet is getting through. But i will certainly give samba a try, looks pretty nifty.

---

