---
title: "slow login with fglrx?"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by Lysi on 2006-11-09
Hallo everyone,

I actually got 3d acceraltion on my laptop zt3000 with ati 9000 mobility card to work on my dapper installation following this [guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Troubleshooting_for_both_Methods"). However, now after entering my password and login in gdm the system shows the ubuntu background and just sits there for ~30s. Finally the login sound plays and everthing keeps running without further delay. 
I was looking on a terminal for active processe, but besides top the system didn't show any activity.

With the original mesa the system logged in without delay.

Does anyone know, what causes this, and how can it be fixed?

Thx,
Lysi

---

### Post by barney_1 on 2006-11-09
I had a problem with slow login as well.  Check and see if you get a FAIL on Swap Signature.  Seems that the swap partition can get messed up with the upgrade to Edgy.  Try [this link]("http://www.ubuntuforums.org/showthread.php?t=287096&highlight=swap+signature") if that's your problem.

---

### Post by Lysi on 2006-11-09
thx for your help... I am on a new way of troubleshooting and experiments...

Right now I am trying to get my wlan card working, and for some reason the lag is gone... So I think the network configuration is somehow connected to it.
I guess that I removed the autoconfiguration of the wlan which didn't work before and was activated in between...

---

### Post by redbull34th on 2006-12-07
I've been experiencing the same problem with a IBM(Lenovo) T43p running Edgy with fglrx

I found another entry on the forums attributing the problem to the hosts file and X having to time out...

Try editing /etc/hosts to resemble this:

127.0.0.1 localhost <your_computer_hostname>
127.0.1.1 <your_computer_hostname>

The theory is that(and your situation with multiple network interfaces may support this) X attempts to resolve the hostname on the active non-connected interface and it has to time out before X will load.  Like you said, after it's loaded, it works just fine.

This is in line with my situation, where I switch from WIFI at home and Gigabit Ethernet at work, having to disable and enable interfaces at each location after login.

Just another idea for you.

---

