---
title: "Problem using DSL connection through network manager"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by aman256 on 2010-06-04
I have ubuntu 10.04 64-bit installed in my hp pavillion dv6 laptop. I use a DSL connection to access internet. After creating my connection in network manager, I was able to connect to internet. But now the option to dialup that pppoe connection is not shown in network manager. I tried deleting that connection & creating a new one, but that was not helpful. How can i bring that connection back in network manager?

---

### Post by dineshs on 2010-06-05
You mean you cant see the newly created DSL connection when you rightclick the NM icon?(the two opposite arrows on top right corner)
BTW you can also try pppoeconf command
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE) 
Because this thread says NM is not working sometimes
[http://ubuntuforums.org/showthread.php?t=1501265](http://ubuntuforums.org/showthread.php?t=1501265)

---

### Post by aman256 on 2010-06-05
yes thats exactly what I meant.
Since this problem started i have been using pppoeconf, but i like network manager because of its gui. Is there any method to make it visible in the list of available networks?

---

### Post by dineshs on 2010-06-05
> but i like network manager because of its gui
1)There is an application called gpppon which you can install,```
sudo apt-get install gpppon
```
then create a launcher as follows
Right click on the desktop and click create launcher
type-Application in terminal
name-internet(say)
command-sudo gpppon
then click on the icon- if you want to change the default icon
and click OK
2)Another method is to install rp-pppoe
[http://ubuntuforums.org/showthread.php?t=816858](http://ubuntuforums.org/showthread.php?t=816858)

---

### Post by dineshs on 2010-06-07
> But now the option to dialup that pppoe connection is not shown in network managerThere is an option [COLOR="Blue"]Available to all users[/COLOR] in DSL tab of NM which you can check.

---

### Post by aman256 on 2010-06-11
thanks for your suggestions, the problem is now solved.

---

