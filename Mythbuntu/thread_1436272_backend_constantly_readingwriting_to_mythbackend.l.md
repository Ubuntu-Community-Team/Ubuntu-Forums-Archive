---
title: "backend constantly reading/writing to mythbackend.log"
date: 2010-03-22
forum: Mythbuntu
---

### Post by rienzio on 2010-03-22
My Mythbox has started constantly reading/writing the hard disk even when no job such as recording or flagging commercials is engaged. I ran iotop and found that it is reading and writing to var/log/mythtv/mythbackend.log .   

Any thoughts on what might be causing this? Any input is much  appreciated. My machine's specifications are attached.

I thought it might be hard drive failure at first, ran smartctl , and the drive got a clean bill of health.

---

### Post by tgm4883 on 2010-03-22
Post 
/var/log/mythtv/mythbackend.log

---

### Post by rienzio on 2010-03-22
.log posted to:
[http://bullock.cc/ubu/mythbackend.txt](http://bullock.cc/ubu/mythbackend.txt) 
thanks

---

### Post by nickrout on 2010-03-23
so which bits are you saying it shouldn't be writing?

This bit > 2010-03-20 23:45:28.983 MainServer::ANN Monitor
2010-03-20 23:45:29.121 adding: n722ht as a client (events: 1)
 looks a bit suspicious, but everything else looks pretty normal, on a quick look.

---

### Post by rienzio on 2010-03-23
I had been wanting to try daily builds for a while--and finally gave it a go last night. After the update, the backend seems to settle down when no jobs are engaged. Thanks everyone for your input!

---

