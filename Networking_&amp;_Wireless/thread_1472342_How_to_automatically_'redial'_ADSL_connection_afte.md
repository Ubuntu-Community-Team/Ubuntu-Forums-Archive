---
title: "How to automatically 'redial' ADSL connection after power failure?"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by ashwinhgtx on 2010-05-04
I use an ADSL connection which I 'dial' using the Network Manager. My laptop is connected to the modem through an ethernet cable.


The thing is the place where I stay is prone for power failure. So the modem goes out with the power. It comes back on within a minute when the power is restored but Network Manager doesn't seem to automatically re-establish the connection after it is lost once. I have to manually do it. Hence most of my downloads do not get done.


I would be very grateful if someone could help me fix this issue.

---

### Post by gzarkadas on 2010-05-04
If your modem goes out of power, the downloads (I assume you use a web browser with no download resume capabilities) will be lost anyway. 

Also since the laptop stays on, there is no event to use as an easy target to auto-trigger a Network Manager restart. But you can code your actions in a script and make an easily accessible launcher (either on your desktop or on your menubar) to click it instantly when the modem powers up.

The best thing to do is to use an app that has download resume capabilities such as [**wget**]("http://www.gnu.org/software/wget/"). That way you will not have to start from the beginning each aborted download.

I strongly suggest for your situation to buy a ups; the required wattage is small and so it will cost you little.

---

### Post by ashwinhgtx on 2010-05-04
By downloads I mean mainly torrents, so they can be resumed. My Kubuntu Lucid download has not yet finished. :(


I used to use pppoeconf for ADSL on Karmic and it could redial automatically when the modem came back on. I just want to somehow incorporate this functionality in Network Manager. I've checked the 'Connect Automatically' option in the connection properties. Things like auto eth0 seem to get connected automatically but not ADSL.


Can this be done?


Also I've no idea on how to write scripts. :(

---

### Post by gzarkadas on 2010-05-05
What is your modem brand and model? Do you access its settings with a web interface and if yes which address are you using? Paste also the outputs of these commands (as root, prepend sudo):
```
ifconfig
cat /etc/resolv.conf
```And also the steps you take to re-enable your connection.

A possibility to solve this problem is to create a script to check if your modem web interface is accessible and if not to restart the connection. Then put it as a cron job with the desired frequency.

---

### Post by ashwinhgtx on 2010-05-05
I solved the problem temporarily by using pppoeconf. But is this a bug in Network Manager? Does this happen to anyone else?


gzarkadas, would it help fix it if I posted all the things you had asked for? I'm saying this as i have solved the problem for now.

I really appreciate your help. I am willing to provide all the data required. :)

---

### Post by gzarkadas on 2010-05-05
The information I asked was for understanding what your setup is, so that I could -possibly (can't guarantee it)- make a script to test if connection is ok and if not apply action to re-establish it. 

The rationale was that since you download torrents you most probably leave your machine unattended to download for large intervals, which means a power failure will remain unfixed for a long time, since you'll have to return and see there is a need for fixing.

However, if this is not much of an issue then there is no need to proceed, since you have fixed the problem. So, you decide... :)

---

### Post by ashwinhgtx on 2010-05-05
I guess since it's working for me now I don't need to trouble you with it. :)


Thanks a lot man. :guitar:

---

