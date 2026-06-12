---
title: "Can't connect to Windows shares from Ubuntu but works in reverse"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by alican timur on 2009-05-27
I have two machines, one Vista pc with wire connection to Linksys router, and a Jaunty netbook which is connected via wireless. 

I have managed to connect those two and mapped the Ubuntu netbook on a drive with samba, and now i can browse files on the netbook, but i cannot do the same thing in reverse. 

I added the "UbuntuSMB" group to users of Vista and the user "ubuntu" under it, but i cannot connect to the Vista box. Any suggestions?

ps: I can ping the Ubuntu netbook from Vista but cannot ping the Vista machine from Ubuntu.

---

### Post by alican timur on 2009-05-27
bump

---

### Post by dmizer on 2009-05-27
Try this: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

If that doesn't work, try the second link in my sig.

Please wait at least 24 hours before bumping your thread. There is a team dedicated to hunting down and answering 0 reply posts. Once you bump your thread, you no longer appear in the 0 reply search results.

---

### Post by alican timur on 2009-05-27
i followed the instructions precisely to no avail. I tried the link too. It still doesn't work.

---

### Post by dmizer on 2009-05-27
> **alican timur said:**
> i followed the instructions precisely to no avail. I tried the link too. It still doesn't work.

It seems extremely strange that the CIFS tutorial didn't work, what was your mount line?

As an aside, I think this is going to be a VISTA issue. Perhaps firewall or UAC interference from the Vista side of things.

---

### Post by superprash2003 on 2009-05-28
it looks like a firewall issue , try disabling the firewall temporarily ( just to test ) to see if things work..

---

