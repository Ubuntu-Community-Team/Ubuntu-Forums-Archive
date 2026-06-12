---
title: "using all inputs"
date: 2011-10-16
forum: Mythbuntu
---

### Post by GaryG007 on 2011-10-16
I am getting the message > "mythtv is using all inputs, but there are no active recordings?. 
Hitting "OK" after the above message, the message "could not connect to the master backend server" is received.

My capture card is a hauphaug(spelling??) pvr150; I am using the 
composite-1 input; the video source is a "Dish network VIP211K satellite box"

The command
 ```
cat /dev/video0 > /home/gary/Desktop/xxx.mpg
```
does produce a good view-able mpeg file. 

Very frustrating;

Any help greatly appreciated

Gary

---

### Post by nickrout on 2011-10-16
what do your logs tell you?

---

### Post by GaryG007 on 2011-10-18
> **nickrout said:**
> what do your logs tell you?

Thank you for the reply, Nickrout.
I had previously looked at the logs, but they didn't really tell me a whole lot about what was causing the problem. After your reply, and some more changes trying to get it to work,and doing a good bit of searching, I discovered that the localhost name used by mythtv wasn't necessarily that which was entered in the configuration files. The configuration files all said "localhost" as host name; yet the backend used "sdd4"** as host name.

What I had was a frontend with a host name of "localhost" and a backend using "sdd4" as host name. Both running on the same box.

I checked /etc/hostname and found that it showed "sdd4" so I changed it to "localhost" - that took care of the problem.


** sdd4 was the name I used when I installed mythbuntu



Gary

---

### Post by fierodough on 2011-10-22
> **GaryG007 said:**
>  
I checked /etc/hostname and found that it showed "sdd4" so I changed it to "localhost" - that took care of the problem.
 
 
** sdd4 was the name I used when I installed mythbuntu
 
 
 
Gary
 
I have the same problem!
 
At the expense of showing my true skills with ubuntu... How do I change the above setting? 
 
Thank you!

---

### Post by GaryG007 on 2011-10-31
> **fierodough said:**
> I have the same problem!
 
At the expense of showing my true skills with ubuntu... How do I change the above setting? 
 
Thank you!

what I did was to look at "/etc/hostname" to see what it contained. It contained what was shown in the command prompt, which was "sdd4".

So I changed /etc/hostname to contain the hostname that mythtv was looking for. 
"localhost"

---

