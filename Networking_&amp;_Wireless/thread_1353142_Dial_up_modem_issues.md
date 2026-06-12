---
title: "Dial up modem issues"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by dork313 on 2009-12-12
Hello, I am new to Ubuntu but learning quickly. Already I have fallen in love with the OS and want to continue using it. Unfortunately I am having extreme difficulties with my dial up modem. I have been researching the problems for days and have learned quite a bit from it. So far I can connect to the internet using pon or wvdial, though I have the most success with wvdial, but the problem is that my connection gets dropped quite often. The longest I've had it stay online was less than hour. Also, when my connection gets dropped, the only way to reconnect is to restart my computer! This is very frustrating, especially when I want to use ubuntu so badly. 

I am using version 8.10 of ubuntu and my modem is a lucent agrere. As I have said, I have researched this problem on the forums here and on other sites around the net. I have commented out the eco termination line in the /etc/ppp/options as well. 

I do not want to go back to windows but if I can't stay connected to the internet with ubuntu I'll have to. I also don't want to purchase a new modem either, especially since this one is connecting. Please, any suggestions would be greatly appreciated.

---

### Post by _duncan_ on 2009-12-12
Try entering the following command in a terminal before reconnecting. It might spare you the need to restart the computer.
```
sudo /etc/init.d/sl-modem-daemon restart
```

---

### Post by dork313 on 2009-12-13
Thank you for the reply _duncan_. I did as you suggested but it said it was a bad command. I double checked it and even copy/paste it and each time it said the same thing.

---

### Post by _duncan_ on 2009-12-14
my mistake. I should have asked first if your modem requires using the sl-modem-daemon package to work. Some winmodems do, some don't. I fast-tracked the possible solution, knowing that if it's not present, the above command will not harm your system anyway.

1. what is the error message when you try reconnecting? IIRC with 8.10, it used to be "modem is busy".

2. Can you post your wvdial.conf file (make sure to remove user name and password for security reasons)?

3. At what speed are you usually able to connect? Mine used to range between 44kbps to 48kbps?

---

### Post by dork313 on 2009-12-16
Thank you once again for your response _duncan_. Thankfully I nolonger have the problem. I've installed kubuntu 9.10, followed the same directions to install the martian modem drivers, configured kppp, and viola! My connection is running strong.

Thank you again.

---

### Post by tyc on 2010-04-28
> **dork313 said:**
> 
Thank you once again for your response _duncan_. Thankfully I nolonger have the problem. I've installed kubuntu 9.10, followed the same directions to install the martian modem drivers, configured kppp, and viola! My connection is running strong.

Thank you again.


Just came across your thread and thought I'd ask ...

By chance are you using KDE4 with your Kubuntu v9.10?

I ask this as I'm having a problem with KPPP and KDE4 which may be related ... "modem busy." I've used KPPP for years with Suse v10.0 - with no problems but now, with Slackware v13, Mandriva 2009 and Suse v11.1, all using KDE4, all I'm getting now is "modem busy." Sound at all familiar?

tyc

---

