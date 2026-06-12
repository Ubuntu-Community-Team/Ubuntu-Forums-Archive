---
title: "No Network Device!"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by beartofear on 2009-07-02
Hi everyone,

I've installed Kubuntu 8.04 on a Dell Optiplex 960

It has an Intel(R) 82567LM-3 network connection.

Kubuntu seemed to install fine, but when I boot up there is no device listed with knetworkmanager and no eth0. I'm not sure what to do now?

---

### Post by computer13137 on 2009-07-02
Could you paste the output of "lspci" to us please?  Just go run the command in a terminal window.

Also, the launchpad answers section suggests that there is an issue with that revision of network card on Ubuntu, but suggests a solution.

[https://answers.launchpad.net/ubuntu/+question/68901](https://answers.launchpad.net/ubuntu/+question/68901)

-Kirk

---

### Post by beartofear on 2009-07-03
Kirk, 

I would paste that to you except that the computer won't connect at all so I'm on a different system for the help so I don't have to keep logging off and logging into Windows then.  

However I will tell you that when I run the lpsci command I get the following output. 

00:0.19.0 Ethernet Controller:  Intel Corporation 82567LM-3Gigabit Network Connect ion (rev 2)

So it does recognize that it exits interestingly.  

If I wanted to try the "fix" in your link - how would I go about changing the version number?

---

### Post by computer13137 on 2009-07-03
Unfortunately, I'm not sure I can assist you further.  Hopefully someone else here can. 

Here are a few threads I found that might prove useful to you:
[http://ubuntuforums.org/showthread.php?p=7552925](http://ubuntuforums.org/showthread.php?p=7552925)
[http://ubuntuforums.org/showthread.php?t=1128970](http://ubuntuforums.org/showthread.php?t=1128970)

Hopefully someone more advanced in this area can fix your problem now that I've helped diagnose it.

-Kirk

---

### Post by beartofear on 2009-07-03
Kirk, 

I actually got things fixed!  

I tried re-installing a driver from intel.com.

It didn't work for others but in my case it fixed the problem immediately.

Thanks for the suggestions though!

---

