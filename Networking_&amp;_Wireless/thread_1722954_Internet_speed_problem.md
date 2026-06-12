---
title: "Internet speed problem"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by Exeleration-G on 2011-04-06
Hello everybody,

I'm using Ubuntu 10.10 on an Acer Aspire 5715Z laptop. I really like using the OS. There's been a problem since the beginning, however: loading web pages on Ubuntu takes much more time than loading them on Windows Vista. On the internet, I've seen solutions like editing the pipelining settings in Firefox' about:config, as well as disabling IPv6. This didn't work for me however: the 'deeper' problem hasn't been solved yet.

To check if the problem was the installed Firefox, I've installed Opera as well. Sadly enough, Opera was as slow as Firefox. Upgrading Firefox to version 4.0 didn't help either.

There's one strange thing that took away this speed problem, however. Instead of downloading Firefox via the repositories, I've downloaded Firefox as a tar.bz2-file. I've unpacked it and run it. This 'tar.bz2-Firefox' was just as quick as the one in Windows Vista.

So why not use the tar.bz2-Firefox? The problem here was that the list of programs to run downloaded files with, was empty. What was even worse was that some necessary plugins didn't work on this Firefox, so watching Youtube.com or going to Beatport.com became impossible.

Concluding, I'd like to have the repositories-Firefox to run at the speed of the tar.bz2-Firefox. Editing the tar.bz2-Firefox so it's loaded with the plugins would be fine as well, but I prefer the first thing, for I like the smooth way of updating the programs which are installed via the repositories.

I've already asked this question on the Dutch Ubuntu-forums, but no-one could help me out over there. So I'm just hoping that you guys can.

Thanks in advance.

Exeleration-G

---

### Post by Exeleration-G on 2011-04-07
So I guess that I'm the only one having this problem? That'd be too bad for me. Hopefully, the bug will be gone when I'll install Natty Narwhal on the 28th of April.

---

### Post by Exeleration-G on 2011-04-26
The problem has been solved. I had to tick the box 'Available for all users' in the connection settings to get it working.

Hope this is of some help to some users.

---

### Post by [__nik__] on 2011-04-28
First of all I am very new to Ubuntu. First time user - was getting a lot of problems with the net.
Thank you for your post - your fix works.

What exactly does it change though ? why is it slower if you dont check available to all users?
I am just trying to understand basic functionality because right now if i face a problem i can do nothing but search the net (compared to windows where most of the times i just know what it is - since ive used it so much)

---

### Post by Exeleration-G on 2011-04-28
I'm glad to hear that I've helped someone else. I really don't know why the pages load faster when you've checked the box (I'm quite of a noob myself :-)). But I think that it has something to do with DNS.

---

### Post by deeperDATA on 2011-04-28
So I've been searching the forums and I haven't been able to find a solution to my problem anywhere. Slow internet. I need to solve this problem. The speed is about 50% slower on my Linux box than on the Windows machine right next to it. I am using wifi and even tried using different wireless adapters. Still the same. I tried disabling IPV6 at boot up and it still happens. Any suggestions?

Ubuntu 10.10 x64

---

### Post by Exeleration-G on 2011-04-29
Do you mean slow internet? Or do you mean slow browsing speed? To test, you can check your download speed by downloading an Ubuntu rom. Is your download speed here the same as in Windows? If yes, your problem is a browsing speed problem.

Check if using a different browser (Opera, Konqueror, Midori) solves your problem.

Also, it'd be cool if you could post your ```
ipconfig /all
``` (on Windows) and your ```
ifconfig -a 
``` on Ubuntu here. I'm not a pro myself, but there are people here who understand these data and might solve your problem.

---

### Post by xd20 on 2011-05-01
its not a browsing speed issue for me considering it does this when I need to download ubuntu applications or updates.

---

### Post by deeperDATA on 2011-05-02
I will post those settings shortly. I have tried different browsers, wireless routers, wireless adapters... nothing. Currently I'm trying manual wireless configuration through the terminal command "iwpriv" to see if I can figure something out.
I was curious about this /etc/modprobe.d directory. I found a file titled blacklist-ath_pci.conf and was curious of its purpose. I'm ready to try anything.

---

### Post by Exeleration-G on 2011-05-02
OK, good luck with that. Hope you'll find something interesting :)

---

### Post by deeperDATA on 2011-05-03
OK so I realized after testing a USB attached wireless adapter in a virtualized Windows 7 guest OS through a Ubuntu host OS that I'm having the same issues. I'm assuming the problem defaults back to how Ubuntu is "operating" the device. Maybe a power or transmission setting that is incorrect but for 2 different wireless adapters it just seems strange.

I was thinking about trying ndiswrapper to see if that would straighten it out.

:confused:

---

