---
title: "Configuring dsl is such a hassle"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by vkam2000 on 2010-03-07
My internet connectivity works through a username password authentication.

After setting up **ppoeconf** the connection works but _I do not want it to start/connect at boot time_.

So I reconfigured **pppoeconf** and set the the option as not to start the connection at boot time.

However after a reboot ,if I enter the command pon dsl-provider internet  does not work.

The network tools under administration also has a dsl tab to configure....but I don't know how to set it up.

---

### Post by perham on 2010-03-07
> **vkam2000 said:**
> My internet connectivity works through a username password authentication.

After setting up **ppoeconf** the connection works but _I do not want it to start/connect at boot time_.

So I reconfigured **pppoeconf** and set the the option as not to start the connection at boot time.

However after a reboot ,if I enter the command pon dsl-provider internet  does not work.

The network tools under administration also has a dsl tab to configure....but I don't know how to set it up.

have you tried rp-pppoe instead? 

[http://www.roaringpenguin.com/products/pppoe](http://www.roaringpenguin.com/products/pppoe)

---

### Post by vkam2000 on 2010-03-07
Will download rp-pppoe install and get back.

What about the dsl option under network tools ? Why not use that...

However,I have a  router/modem through which I connect

---

### Post by vkam2000 on 2010-03-07
Ok Installed the software and set the idle time as 10 seconds.

Please tell how this s/w works and what does that idle timer mean .

---

### Post by perham on 2010-03-07
> **vkam2000 said:**
> Will download rp-pppoe install and get back.

What about the dsl option under network tools ? Why not use that...

However,I have a  router/modem through which I connect

if you have a router, you can use it in routing mode instead of bridge mode, set its dhcp and nat and then you don't need to set up anything in your ubuntu box. it just gets the ip address via dhcp and works fine. however, if you're avoiding routing mode for any reason, rp-pppoe is a great pppoe manager and works in a simple way. I've been using it from 6.06 lts and I never checked out ubuntu's default tool since I never needed too. give it a try and get back if you had any problems.

---

### Post by vkam2000 on 2010-03-07
Ok the internet works,setup some options and I can initiate/drop the connection through pppoe-start/pppoe-stop.



But again,while setting up rp-pppoe it asked for an idle timer what is that ?



Thanks for the help.

---

### Post by perham on 2010-03-07
> **vkam2000 said:**
> Ok the internet works,setup some options and I can initiate/drop the connection through pppoe-start/pppoe-stop.



But again,while setting up rp-pppoe it asked for an idle timer what is that ?



Thanks for the help.

probably for disconnecting after an amount of idle time. I'm pretty sure it can be set to infinite.

---

### Post by vkam2000 on 2010-03-07
Im back with a fresh problem.


I installed rp-pppoe and it worked ,however I was trying to setup file sharing with my windows pc...and after that rp-pppoe stopped working...it shows that it has connected but the browser does no work.


Also how do I start the rp-pppoe gui again??

---

### Post by shantanurai on 2010-03-07
Hi Vkram,
I have struggled with exactly this issue for over 2 months. I was using a BSNL connection which worked well initally using ppoeconf. But once it broke, it gave me sleepless nights but i could not get it to work again.

A much simpler solution is to configure your DSL modem with the user name password and remove all configurations from the Ubuntu system. You can do this by loggin into your modem "http://192.168.1.1" . The default password is 'admin' and 'admin' and then configure the user names and password.

Once this is done, it is simple to physically swith on the modem when you want it and the same can also be managed by the network manager in ubuntu.

hope this helps

---

### Post by vkam2000 on 2010-03-07
To begin with my name is not vikram,look at the username.

I perfer to have bridged connectivity where I manually control my authentication to the internet...it gives me flexibility when doing files sharing between 2-8 am (BSNL 500)...I have sceduled my windows OS to do so.

Thanks anyways.

---

### Post by vkam2000 on 2010-03-07
pppoeconf works while rp-pppoe does not.

I want to uninstall it,but how.its a compiled program with no uninstall methods !

---

