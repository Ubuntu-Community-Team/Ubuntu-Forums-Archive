---
title: "Web cam chatroulette problems"
date: 2010-03-06
forum: Multimedia Software
---

### Post by skaramanger on 2010-03-06
Greetings,

Recently, I got out my old Fuji Finepix s3100 and set it to web cam mode to see if anything had changed in the world of usb video drivers. Lo and behold it worked!  I can watch myself on **cheese web cam booth**. kewl, but I wanted more.  So, just recently hearing about chatroulette on the Daily Show, I click and wahla no go :(.

After flash comes up and asks for and receives user permission to access my hardware, I click to find a random stranger, and my camera displays yellow and blue lines across its onscreen display box.  I notice that movement is noticed by the camera. If I move I notice a change in background/lines.  As far as I can tell, my camera is not a fault. I mean it works for local viewing.  Is this a flash or possibly a chatroulette problem?  Comments anyone?

Tia

```
[mydesktop ~]$ uname -r v4l2
2.6.31-20-generic
```

```
[mydesktop ~]$ aptitude search
i   libpt-1.10.10-plugins-v4l2 - Portable Windows Library Video Plugin for Video4Linux v2  
p   libpt-1.11.2-plugins-v4l2  - Portable Windows Library Video Plugin for Video4Linux v2  
v   libpt-plugins-v4l2                              -                                                           
i   v4l2ucp        - Video for Linux 2 Universal Control Panel

```

---

### Post by gordintoronto on 2010-03-06
Start Firefox by typing this into Accesories/Terminal:
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox

---

### Post by skaramanger on 2010-03-06
gordintoronto,

thanks for your reply.
For the most part except for sytax, that did it. I adjusted the command for bash shell:

set LD_PRELOAD=/usr/lib/libv4l/v4licompat.so
export LD_PRELOAD

Now all I have to do is either setup firefox to initialize this variable before execution or in bashrc at login.

Thanks again


> **gordintoronto said:**
> Start Firefox by typing this into Accesories/Terminal:
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox

---

### Post by gordintoronto on 2010-03-06
You have translated a one to an eye. (1 not i)

---

### Post by skaramanger on 2010-03-06
Yes thanks, I eventually caught that.
Have more problems will start a new thread.

---

