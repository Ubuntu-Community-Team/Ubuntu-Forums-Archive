---
title: "Network settings for guarddog"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by newbie9 on 2008-12-07
I need to do a short paper on installing and setting up guarddog on ubuntu. Some of the things that need to be allowed are as follows. Browser on port 80, IM on TCP 5050, RDP on 2179 TCP/UDP, and VNC on 5900 TCP/UDP. Can anyone briefly explain these to me. 
Thank you in advance,
Rob

---

### Post by newbie9 on 2008-12-07
bump

---

### Post by lovelyvik293 on 2008-12-07
The Network works on the OSI or TCP/IP model according to which there are 7(OSI) and 5(TCP) layers.And there is a layer which is called the networking layer is responsable for this port thing.
According to this layer each application is associated with a port number like the HTTP(browser) on port 80.

Now in the guarddog you can make these ports assocaited to needed application open.

---

### Post by newbie9 on 2008-12-07
I thought it might be easier if I just set up ubuntu on one of my computers to figure out how to do this so I can write my paper. My question now is, I've installed Ubuntu Hardy and downloaded Guarddog, it says that I do not have superuser privlages how can I get into guarddog to set it up?

---

### Post by Lupusceleri on 2008-12-07
You have guarddog installed already?

I guess you'd get a root-guarddog by opening the terminal, then do:

```
sudo guarddog
```

If the name of the application is in fact guarddog of course. :)

Did that work?

---

### Post by lovelyvik293 on 2008-12-07
Just read the user manuall of the guarddog
[http://www.simonzone.com/software/guarddog/manual2](http://www.simonzone.com/software/guarddog/manual2)

It helps you in writting the paper and actually doing all the configuration.

---

### Post by newbie9 on 2008-12-07
Yes that did work. Now I just need to figure out how to use it to setup the things that I want to allow and which ports I want them on.

Thank you

---

### Post by lovelyvik293 on 2008-12-07
Welcome always google first.

---

### Post by newbie9 on 2008-12-08
I finished my final project and turned it into the professor today for a grade of 95%. Thanks to all of you for the help. At 38 years old it is a challage being in college and raising a family at the same time. Good to have places like this to come for help.
Thanks again,
Rob Good

---

