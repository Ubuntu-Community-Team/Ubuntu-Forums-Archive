---
title: "mic not found"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by mgrajesh on 2007-12-26
Hi, 

I am new to linux. On my ubuntu desktop, I do not see "mic" device in sound recorder or in alsamixer. Can someone please help? 

Thanks
Rajesh

---

### Post by Mithrilhall on 2007-12-26
In a console try this when you have your Mic connected and post back the results.

```

x@kubuntu:~$ sudo asoundconf list
[sudo] password forx:
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
NVidia
Headset
x@kubuntu:~$

```

---

### Post by mgrajesh on 2007-12-26
Thank you for quick reply:

Here is the output

xyz@ubuntu1:~$ sudo asoundconf list
[sudo] password for ubuntu1:
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Intel
xyz@ubuntu1:~$

---

### Post by mgrajesh on 2007-12-28
When I run "sudo asoundconf list", I see "Intel", but no mic or headphone listed.
Can someone please help?

Thanks
Rajesh Gopinathapai

---

