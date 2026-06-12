---
title: "Cant start a ssh server... {fail}"
date: 2006-02-05
forum: Networking &amp; Wireless
---

### Post by floyd27 on 2006-02-05
Hi..

I have been using a ssh server to access another kubuntu comp..
It ususally works fine but it stopped recently..
I have installed on the remote comp..

-ssh
-fuse (and the utils etc)

When I try.
sudo /etc/init.d/ssh start

I get a (fail) error..
I have not modded the config file at all, The only thing I did was I uninstalled fuse and re-installed it (due to it not working, to access the host comp)
After that I could not access the remote comp or the host comp..

Any ideas how i could fix this..  Thanx

---

### Post by floyd27 on 2006-02-05
I managed to get ssh to start up but I still cant connect..

I think it may be something simple im overlooking?
Is there a log file i could post to give you guys some more info?
thanx

---

### Post by Pragmatist on 2006-02-05
Here is a dumb question:  Do you have sshd daemon running on the computer your trying to connect to?  Also, while I don't know that much about this, one of the things I did to get ssh working was to list both machines in each computers  **/etc/host**  file.

---

### Post by bscbrit on 2006-02-05
If the message that you are getting is that your connection has been refused, then I will bet that you haven't installed ssh-server on your destination machine.  So that you can SSH both ways, install ssh-client and ssh-server on both machines.

---

### Post by floyd27 on 2006-02-05
I have ssh installed on both and ssh is running..
Like I said I was able to connect until recently..

I dont get connection refused.. I just get a timed out..
It does nothing for a few minutes then times out..

I will try to add both comps to the /etc/host file, but i never had to do it before..

---

### Post by bscbrit on 2006-02-06
It sounds like a network or connection problem.  Can you ping each machine from the other?  You haven't installed anything else, (firewall?) since you last had a successful ssh connection have you?

---

### Post by floyd27 on 2006-02-06
Im doing some more trouble shooting..
i will update when I have some more useful info to give you guys..
No, no firewalls or anything special...

thanx again..

---

