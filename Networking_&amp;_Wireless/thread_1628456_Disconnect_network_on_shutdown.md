---
title: "Disconnect network on shutdown"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by jamessimo on 2010-11-22
Hey guys! I like to think that is an easy request. A month ago I had (and still have) a weird problem were leaving my switched off computer plugged into the network killed the whole network.

[http://ubuntuforums.org/showthread.php?t=1585116](http://ubuntuforums.org/showthread.php?t=1585116)

well I have found a fix, if I disconnect my computer via software (Right click and disconnect "eth1" and shut down the network will remain up. 

I want to make a script that runs on shutdown that simply disconnects "eth1".

Are there any pre-made shutdown scripts in ubuntu that I can simply add "eth1 enabled = 0" or something. 

Thanks!

---

### Post by Suparious on 2010-11-22
I think this is a pretty easy request.

Have a look at the scripts in both rc0.d and rc6.d;

The scripts that begin with S are startup scripts, and K are shutdown scripts.

Also, there is a similar discussion here:
[http://ubuntuforums.org/showthread.php?t=436346]("http://ubuntuforums.org/showthread.php?t=436346")


And here is a small article on the linux boot-up and shutdown process:
[http://articles.techrepublic.com.com/5100-10878_11-1056248.html]("http://articles.techrepublic.com.com/5100-10878_11-1056248.html")

---

### Post by jamessimo on 2010-11-23
Thanks for the reply! I still cannot find what command is used to diconnect a interent connection. 

Anyhelp?

---

### Post by jamessimo on 2010-11-24
I'm still struggling with this, I have this code that I just whacked into pigins shutdown script (Seemed the safest place).

I dont think its working. 

```

status=`ifconfig | grep eth1 | wc -l`
ifdown eth1
echo "eth1 Disconnected"
```

Is this wrong and can I make my own K file?

---

### Post by Cheesehead on 2010-11-27
The correct command is indeed 'ifdown <interface name>', 
for example 'ifdown eth1'.

If it's run as a root script, 'ifdown eth1'
If on your command line, add 'sudo' of course.

Yes, you can make your own change-of-runlevel script, or you can capture a 'shutdown' upstart event. Whichever makes you more comfortable. 

There's no magic...just be careful, test thoroughly, and document it so you can maintain it.

---

