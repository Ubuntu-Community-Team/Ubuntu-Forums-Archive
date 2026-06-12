---
title: "nautilus refuses to load normally"
date: 2011-03-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-03-08
liam@liamspc:~$ nautilus

(nautilus:14968): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:14968): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:14968): GLib-GIO-CRITICAL **: g_bus_unwatch_name: assertion `watcher_id > 0' failed


Any ideas? It runs fine under sudo though but not as a normal user? Cannot seem to touch anything on my actual desktop either :\

---

### Post by kuvanito on 2011-03-08
I am in the same boat you are
Nautilus refuses to work,it's extremely slow opening up any windows.
dam it hurst after I had Natty all up and running! :(

---

### Post by ELD on 2011-03-08
You can use :

> 
sudo nautilus


For now it seems that works fine, BUT BE CAREFUL.

---

### Post by kuvanito on 2011-03-08
nope
it won't help
you can't browse through folders,it takes 1-5 min to open a folder

Edited:
Thanks ELD,I tried once more and it did worked this time.Thank You again

---

### Post by ELD on 2011-03-08
Just be careful that is admin rights, it's the only way i can browse any folders for the moment though.

---

### Post by fuzetsu490 on 2011-03-08
Yup, same issue here since I updated just now for the first time since yesterday. I hope this gets fixed soon :/ since I have no idea what is going on to do anything about it myself :(

EDIT: I just updated once again from synaptic, the update removed gir1.2-unity-3.0 and installed some ubuntu-one updates, nautilus seems to be working now, as I was updating all the windows I had tried to open in nautilus opened at once and I can move around my files without lag now.

---

### Post by Harry33 on 2011-03-09
> **fuzetsu490 said:**
> Yup, same issue here since I updated just now for the first time since yesterday. I hope this gets fixed soon :/ since I have no idea what is going on to do anything about it myself :(

EDIT: I just updated once again from synaptic, the update removed gir1.2-unity-3.0 and installed some ubuntu-one updates, nautilus seems to be working now, as I was updating all the windows I had tried to open in nautilus opened at once and I can move around my files without lag now.

Seems to be a Unity issue.
No problems with Nautilus w/o Unity and with Ubuntu-Classic Desktop.

---

### Post by lancest on 2011-03-09
Nautilus problems here also. 
I have resorted to the command line to open files.

---

### Post by webme on 2011-03-09
I think the problem is caused by the gir... package , in my case I made a partial upgrade which has removed gir (ubuntu-one related partial upgrade) and everything is fine now.

---

### Post by fuzetsu490 on 2011-03-09
> **webme said:**
> I think the problem is caused by the gir... package , in my case I made a partial upgrade which has removed gir (ubuntu-one related partial upgrade) and everything is fine now.

Yeah, I think that was it, it was the same for me.

---

### Post by DougieFresh4U on 2011-03-09
> **webme said:**
>  I made a partial upgrade 
OH NO! Not the partial upgrade.  :lolflag:

---

### Post by lancest on 2011-03-09
Nautilus is working now for me with latest update
However if I click on Ubuntu One the problems with Nautilus return.

---

### Post by gdonwallace on 2011-03-10
I am having the same problem.  Will try the Synaptic update process and see if that fixes the problem.  Hope it does, otherwise this really goes from being unstable to unusable.

---

### Post by lancest on 2011-03-18
I'm afraid the Nautilus problem is back. Also my USB devices are not opening/recognized consistently.  Kernel .38-5.  Fully updated.

---

