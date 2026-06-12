---
title: "Mythbuntu Control-Centre Aborting"
date: 2008-09-21
forum: Mythbuntu
---

### Post by fjbintbus on 2008-09-21
I have installed Mythbuntu 8.04 with the frontend and backend on the same machine.  I have successfully received OTA ATSC programming.

My problem is when I try to start Mythbuntu-Control-Centre I see its window for about half a second. Then it's gone...

I tried to start it from the terminal. The result was the same.  I got a segmentation fault message in the terminal window.

How can I fix this???

---

### Post by superm1 on 2008-09-21
> **fjbintbus said:**
> I have installed Mythbuntu 8.04 with the frontend and backend on the same machine.  I have successfully received OTA ATSC programming.

My problem is when I try to start Mythbuntu-Control-Centre I see its window for about half a second. Then it's gone...

I tried to start it from the terminal. The result was the same.  I got a segmentation fault message in the terminal window.

How can I fix this???
Sounds like you found a bug ;)

Can you turn on apport temporarily, and file a bug with it?

1) Modify /etc/default/apport
Put enabled=1

2) Restart apport service
sudo /etc/init.d/apport restart

3) Run app

4) File bug

5) Profit

---

### Post by fjbintbus on 2008-09-22
> **superm1 said:**
> Sounds like you found a bug ;)

Can you turn on apport temporarily, and file a bug with it?

1) Modify /etc/default/apport
Put enabled=1

2) Restart apport service
sudo /etc/init.d/apport restart

3) Run app

4) File bug

5) Profit
Will do shortly.....

---

### Post by superm1 on 2008-09-22
Apport should intercept the crash and get all the needed information added to the bug report.  If it's still not catching it, try restarting the computer.

---

### Post by fjbintbus on 2008-09-22
> **fjbintbus said:**
> Will do shortly.....

Submitted bug report# 273159

---

