---
title: "Cannot get my Linksys wireless card to work... BHAH....!"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by chris301up on 2011-07-10
Right. I have installed Ubuntu 11.04 and for several days have tried many, many different ways of installing my Linksys WPC 11 wireless card into my IBM Thinkpad T30 laptop.

I have got the wireless working by installing Ubuntu 8 and then upgrading to the current version, and I would assume some drivers are currently installed.

As usual though, the signal drops out after only a few minutes and I have to keep re-booting the laptop to continue what I'm doing.

This as now become very, very annoying and I would like to correct the problem if I can?

Any advice would be greatly appreciated.

---

### Post by kanishkdudeja on 2011-07-10
try installing it again with the help of the second post in this thread..

maybe then it works..

[http://ubuntuforums.org/showthread.php?t=95591](http://ubuntuforums.org/showthread.php?t=95591)

---

### Post by chris301up on 2011-07-10
Yes I have already followed the steps in this thread but it just will not work.

When I get to [COLOR="Red"]**"$ sudo ndiswrapper -i NET8180.INF"**[/COLOR] I get the following message [COLOR="red"]**"couldn't open NET8180.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219".**[/COLOR]

I'm totally lost now????

---

### Post by kanishkdudeja on 2011-07-10
You have to specify path to *.inf , 
ie ndiswrapper -i /home/foobar/net8180.inf 
if net8180.inf is in foobar's home directory. 

net8180.inf will be in the directory which you have got after extracting the driver you downloaded. so you have to give path to that directory in which net8180.inf is present..

Also be aware it's case sensitive so if inf is NET8180.inf then it will be ndiswrapper -i NET8180.inf .

---

### Post by kanishkdudeja on 2011-07-10
im going to get some sleep now..

will get back tomorrow morning..:)

---

### Post by chris301up on 2011-07-13
Right. Thank you all for your kind help and advice. I have done what you have suggested many, many times and BINGO - it works!! 

I don't really know where the problem was as I've installed, and reinstalled that many times I've lost count, but it would have been nice to have known where the problem occurred for future reference.

I don't suppose we can have it our own way all the time - can we??

From Ubuntu 8 onwards I have been unable to access the internet, until now - so will give this version a fair go - and hopefully WILL NOT RETURN TO TROUBLESOME WINDOWS.

YIPEE !!

---

### Post by kanishkdudeja on 2011-07-13
i think you didnt give the path correctly to net8180.inf earlier.

maybe that's why it didn't work.

anyway, congratulations :)..cheers! :)
have a great day :)

---

### Post by kanishkdudeja on 2011-07-13
please mark the thread as solved so that other people don't waste their time looking into your thread as you've already solved it.

---

