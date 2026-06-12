---
title: "Ubuntu 9.10 &amp; Linksys WUSB11 ver 2.6"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by bjk03 on 2009-11-10
I upgraded to 9.10 from 9.04 today and now my wireless card isn't working properly. It can see my wireless network and attempts to connect to it but in the end it fails. Any help would be great!!

---

### Post by anlouis on 2009-11-10
I have been looking for the answer for over a week now. This has to be simple.
Help us out.
Peace

---

### Post by bjk03 on 2009-11-20
I am still trying to figure this out. I ended up wiping out 9.10 & reinstalled 9.04. When I upgraded to 9.10 the first time I just updated via the update manager. Today I downloaded the ISO of 9.10 and booted the LiveCD, Still no wireless connection :( How do I go about figuring out what driver 9.04 is using versus what 9.10 is using. Also can I make 9.10 use the verion 9.04 uses?

---

### Post by johngat on 2009-11-21
I'm having the exact same problem as You . I upgraded through the updtae manager and now , now wireless . I was going to re-install 9.04 but , how do I wipe 9.10 and do it ? I do have the disk for the 9.04 . Thanks

---

### Post by bjk03 on 2009-11-21
> **johngat said:**
> I'm having the exact same problem as You . I upgraded through the updtae manager and now , now wireless . I was going to re-install 9.04 but , how do I wipe 9.10 and do it ? I do have the disk for the 9.04 . Thanks

Boot off the 9.04 CD. When it comes up choose install. It will walk you through formatting and then reinstalling 9.04.

---

### Post by mhansens on 2009-11-21
> **bjk03 said:**
> Boot off the 9.04 CD. When it comes up choose install. It will walk you through formatting and then reinstalling 9.04.

Is this going to wipe out all of my files and configuration?  Is there a graceful way to rollback?

---

### Post by bjk03 on 2009-11-22
> **mhansens said:**
> Is this going to wipe out all of my files and configuration?  Is there a graceful way to rollback?

Yes formatting will erase the hard drive. I don't know of a less destructive way to go about it.

---

### Post by bjk03 on 2009-11-28
I have finally got this working in 9.10!!! Here is what I did to get things working. 

1. After I learned how to figure out what driver I was using under 9.04, I ran the command **lshw -C network** This told me I was using the at76_usb driver. 
2. I then googled at76_usb and stumbled upon [this post]("http://ubuntuforums.org/showpost.php?p=8050414&postcount=5"), After updating to 9.10 via the alt install CD, I ran the commands, then restarted my machine. 
3. HOORAY I can use wireless!!!!

---

### Post by kf5nd on 2010-02-09
Hi bjk03, I followed your advice and the Linksys WUSB11 ver 2.6 was working for a short time, then I got a kernel crash for some reason, which never happened before when I was not using the wireless. Then nothing, I can't get it going again.

After banging my head against the wall, I am tempted to do what you did earlier and just roll back to 9.04. Is there a big difference between 9.04 and 9.1? 


> **bjk03 said:**
> I have finally got this working in 9.10!!! Here is what I did to get things working. 

1. After I learned how to figure out what driver I was using under 9.04, I ran the command **lshw -C network** This told me I was using the at76_usb driver. 
2. I then googled at76_usb and stumbled upon [this post]("http://ubuntuforums.org/showpost.php?p=8050414&postcount=5"), After updating to 9.10 via the alt install CD, I ran the commands, then restarted my machine. 
3. HOORAY I can use wireless!!!!

---

