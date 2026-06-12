---
title: "Automatic File Transfer at regular intervals."
date: 2012-03-26
forum: Networking &amp; Wireless
---

### Post by tattushenoi on 2012-03-26
I have Linux running inside an IP camera. I have one memory card inside that too. What I want to do is, to transfer the media files inside the memory card to a windows server machine/Red Hat  automatically at 23:59 every night. 

Is there any kind of script/command to do this?

Thanks

---

### Post by sudodus on 2012-03-26
If the camera's memory card is mounted it should be possible to run rsync from cron. Make a crontab entry.

You can learn about cron and crontab browsing for ***crontab tutorial*** on the internet. And read ```
man crontab
``` Finally, the environment is very simple, so use the full path obtained by ```
which rsync
``````
/usr/bin/rsync
``` etc for all commands.

---

### Post by tattushenoi on 2012-03-26
Thanks for the quick reply, 

If I use

rsync -v -e ssh mylocation remotelocation


It should ask for a password?

If yes, then can I include the password so that I do not have to be present when it executes at midnight?

---

### Post by spynappels on 2012-03-26
To avoid asking for a password, you'd have to use key based authentication. 

However, in this case, I'd initialise the the rsync operation from the receiving server, so that the key to access the IP cam is stored on the server rather than the other way around.

Is the IP cam on your own LAN?

---

### Post by spynappels on 2012-03-26
> **tattushenoi said:**
> rsync -v -e ssh mylocation remotelocation

And the syntax you need is
```
rsync -vz camlocation serverlocation
```
whether you are launching it from the IP cam or from the Server. You simply use the user and IP address of the non-local node. The -z switch compresses the data in transit, which for video or jpeg streams is a good idea.

You do not need the ssh option as it uses ssh by default.

---

