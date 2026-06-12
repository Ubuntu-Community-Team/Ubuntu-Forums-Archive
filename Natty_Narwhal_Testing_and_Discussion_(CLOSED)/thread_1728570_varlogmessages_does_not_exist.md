---
title: "/var/log/messages does not exist?"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by M4570D0N on 2011-04-13
Well this is odd. I've been using Natty mostly from my Mint 10 partition via Virtualbox. My Maverick partition got screwed up and remained screwy when I tried to update it to Natty. I finally decided to wipe that partition today and do a clean install. There's a few bugs, which is expected, but overall it seems to be running pretty well. However, I do not have a log file for messages which should be located in /var/log/messages. I am not seeing any evidence that this file has ever been created since I did the install this morning. What's the deal here? I've tried to search around but I'm finding it rather difficult to sift though the endless search results referencing "/var/log/messages" that are completely unrelated to this. I'm also not seeing the daemon log either. What controls these logs? Can't say I've ever had this issue or read about anyone having this issue.


EDIT:
Post #2 solved the problem. Thanks!

---

### Post by stepore on 2011-04-15
> **M4570D0N said:**
>  I've tried to search around but I'm finding it rather difficult to sift though the endless search results referencing "/var/log/messages" that are completely unrelated to this. I'm also not seeing the daemon log either. What controls these logs? 

This is the file you're looking for:
/etc/rsyslog.d/50-default.conf

Back it up, then feel free to play with it as you like. The 2 sections you're looking for are these:
*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none          -/var/log/messages

daemon.*;mail.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole

After you make changes do:
sudo restart rsyslog

---

### Post by dino99 on 2011-04-16
i'm affected too like many others

please add your voice: [https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/762505](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/762505)

---

### Post by VMC on 2011-04-16
> **stepore said:**
> This is the file you're looking for:
/etc/rsyslog.d/50-default.conf

Back it up, then feel free to play with it as you like. The 2 sections you're looking for are these:
*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none          -/var/log/messages

daemon.*;mail.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole

After you make changes do:
sudo restart rsyslog
Thanks. Interesting read, although I don't have the html that is mentioned in the text. The rsyslog links were helpful, but not sure how to implement them. I'm guessing they were done for me in the past. I'm also guessing that if I remove the "*" they will work. I've never had to alter rsyslogs before. 
Fun stuff.

---

### Post by VMC on 2011-04-16
> **dino99 said:**
> i'm affected too like many others

please add your voice: [https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/762505](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/762505)

I did just that. Lets just see where this will end up. :)

---

### Post by mc4man on 2011-04-16
> **VMC said:**
> . I'm also guessing that if I remove the "*" they will work. I've never had to alter rsyslogs before. 
Fun stuff.
No, if you wanted a 'messages' log you'd uncomment the 4 lines as shown in post 2

---

### Post by hellslinger on 2011-04-19
Thanks so much for posting this. I uncommented the lines out and got my /var/log/messages back. I simply do not understand why this would be disabled.

---

