---
title: "Communcation Front to Back End"
date: 2012-02-05
forum: Mythbuntu
---

### Post by Salbono on 2012-02-05
Did a complete new install on new hard drive partition. Installed from  DVD included in magazine Linux Identity Starter (current issue) where Ialso got Ubuntu from. This  was my third attempt. On the first try I was able to watch and record  video from the remote DVD player plugged into my capture card. But then  had to replace the hard drive. Next attempt kept getting IP address  should be checked, or no NPuP...  I have many hours into this. Anyways I  started over again thinking if I just installed MythBuntu first it  should help. repartitioned the drive, giving windows xp 25% of the drive  then installed MythBuntu. 

Same results...  can't communicate to BackEnd check IP address. I have checked and changed and changed and checked the IP currently set 127.0.0.1, tried local host on both ends. I was fairly excited anticipating being able to  use the computer to record TV. (we don't use cable just over the air  broadcast.) so we could have a better variety in our viewing.

This is a single computer/user install. 

Any suggestions?

Thanks

---

### Post by ianhaycox on 2012-02-06
Have a look in /etc/mysql/my.cnf on the back-end

Find the line,

```
bind-address		= 127.0.0.1
```

and comment it out with #.

---

### Post by Salbono on 2012-02-07
Thanks for your reply. Right now I don't have it installed, and actauly have Linux Mint installed on that machine as well. Installed a new video display card last night and the drivers for it, it's working great! After I install MythTv again I will post here and let you know the results.

---

### Post by Salbono on 2012-02-07
Tried to comment out the line using # but was not able to save it. Operating system said i wasn't authorized.

---

### Post by nickrout on 2012-02-07
> **Salbono said:**
> Tried to comment out the line using # but was not able to save it. Operating system said i wasn't authorized.
well do it as root:

```
sudo nano -w /etc/mysql/my.cnf
```

---

### Post by Salbono on 2012-02-08
Commented out the line as suggested but to no avail.

---

### Post by nickrout on 2012-02-08
did you restart mysqld?

exactly what error messages are you getting and where are they arising?

---

### Post by Salbono on 2012-02-09
I am going to forgo the MythTv until I am sue the capture card is working correctly. I have installed VLC player and have to type information into the configuration every time it starts to get video. I can now view the video but the sound  (which worked at first) has stopped. I can play items of the hard drive and get system sounds so i am assuming it is a capture card read problem. 
Wanted to do some work with python anyways.

Thanks so much for the assistance.

I do think the setup for MythTv seems a bit ... intense. Nothing I could recommend to my mom. She likes TV too.

---

### Post by nickrout on 2012-02-09
It's easy enough if you follow the instructions, although a bit daunting the forst time. It is a bit complex because it is flexible.

---

