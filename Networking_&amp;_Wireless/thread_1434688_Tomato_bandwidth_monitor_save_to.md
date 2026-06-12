---
title: "Tomato bandwidth monitor save to?"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by Jackie999 on 2010-03-20
I'm trying to set up my router, with tomato firmware, to save the bandwidth usage information. One of the 'save history' choices is "CIFS" ... I'm lost as to how to create this save area..anyone able to give me a link to a 'how to' ...or if you've done it, perhaps a step by step?
Thanks!

---

### Post by Jackie999 on 2010-03-21
Well I figured it out so thought I'd post the steps I did in case anyone else is trying to do the same thing.
First I set my IP on my ubuntu laptop static. I did this in the tomato firmware via my laptop wireless mac address. Mine is 192.168.1.122.
Next, in my home folder on ubuntu I made a folder "tomato". When I right clicked on that folder and went to 'sharing options' it asked to download a needed application - samba -did that.  Afterwards I got a sharing error and I read afterwards I needed to update the samba4-common-bin via synaptic-did that. Also, afterwards I realized I had to set a password to the shared file by typing in terminal-
sudo smbpasswd -a username (here I put in my ubuntu username, then pw when it asked)

Now in tomato, in bandwidth/configure I set to CIFS1 (save). Then in Admin/CIFS client I enabled CIFS1 and set the UNC to-
 \\192.168.1.122\tomato (no path is needed here)
username (my ubuntu username)
password (my ubuntu pw)
after saving you should see Total/free size of you ubuntu drive.

I rebooted tomato and saw the a new file in my tomato folder so I think all is working now. I don't leave my ubuntu laptop on 24/7 so I don't expect my figures to be all that accurate - I did set tomato to save every hour..so we'll see how it compares with my ISP figures now.

I hope this helps somebody else trying to set this up :)

---

### Post by Elkaintmoose on 2011-09-23
Hey, thanks man! Just what I was looking for. :D

---

