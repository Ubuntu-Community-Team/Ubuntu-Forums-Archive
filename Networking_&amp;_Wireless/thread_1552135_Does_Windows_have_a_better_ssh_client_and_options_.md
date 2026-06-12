---
title: "Does Windows have a better ssh client and options than Ubuntu!"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by igarny on 2010-08-13
Here is my problem! I recently switched from Windows not suspecting that Linux would put those constraint on my work.
I am a big fan and constant user of putty and especially the port forwarding feature. I often switch and change forwarding options, which is very easy with the right button to the title bar of the connection. So in an established connection I switch with no hassle the option and this works. Also I often use the duplicate this session option.

Now how could one accomplish these routines under Ubuntu?
(change settings of an established session. i even searched for a commands solution)
duplicate an existing session

Does Windows have a better ssh client and options than Ubuntu?!

---

### Post by scorp123 on 2010-08-13
> **igarny said:**
>  I am a big fan and constant user of putty  "Putty" exists for Linux too, there just isn't a need for it IMHO as all Linux distros out there have all the SSH functionality built-in right from start whereas in Windows there is no SSH client out of the box (so people have little choice but have to install "Putty" or similar programs). 

You can install "Putty" by search for it in the "Synaptic Package Manager":  ***System > Administration > Synaptic Package Manager***

Or you install it via the terminal:
```
sudo apt-get update && sudo apt-get install putty
```


> **igarny said:**
>  and especially the port forwarding feature. I suggest you read the manual:
```
man ssh
```

All the options are right there. Or you could try these tutorials? They have a few useful examples:

[http://www.rzg.mpg.de/networkservices/ssh-tunnelling-port-forwarding](http://www.rzg.mpg.de/networkservices/ssh-tunnelling-port-forwarding)
[http://www.revsys.com/writings/quicktips/ssh-tunnel.html](http://www.revsys.com/writings/quicktips/ssh-tunnel.html)
[http://www.brandonhutchinson.com/ssh_tunnelling.html](http://www.brandonhutchinson.com/ssh_tunnelling.html)


> **igarny said:**
>  So in an established connection I switch with no hassle the option and this works.  Putty can't change the parameters of an established connection. What happens in reality is that you quickly get disconnected and reconnected. :D

As for reusing parameters that you already used once ... in the command line you simply use the cursor keys and navigate to a previous command, change it to your liking, hit enter ... Done.

And you could put commands that you regularly use again and again and again into small shell scripts, so they automatically trigger the connection you need. Example: I have a Solaris machine here and its name is "jupiter". I need to get into that machine every day, and because that server is behind a firewall I need to use special ports for that. So instead of having to type the needed command again and again I put into a small shell script with the name "jupiter". So now I simply type "jupiter" into my terminal and ... **woooosh** ... I'm already there and can start doing the stuff that needs to be done.

But as I said above: If you're more comfortable with "Putty" ... there is a Linux version too. I personally honestly fail to see the need for it on Linux as all the terminal programs that are already shipped with all the various distros are more than enough to do any work via SSH and terminal .... but if a Windows-convert like you feels easier using "Putty" then please help yourself and install it as explained above :)


I hope this helped ... ? :)

---

### Post by igarny on 2010-08-14
You are damn wrong about "Putty can't change the parameters of an established connection. What  happens in reality is that you quickly get disconnected and reconnected"

I am administering linux machines for 10 years. I have read and analyzed tons of logs and you may be sure: Putty doesn't reconnect me every time i change settings. It is obvious you haven't seen the power of putty under Windows.



The big problem on using putty under wine is that its titlebar is totally changed by the gnome desktop control so I loose the "change settings" on active session, which I used to exploit so much under true Windows.
Please be careful when reading [http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter4.html](http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter4.html) before you forward me to basic tutorials.

I have given up and realized that Windows has a better tool for remote management of Linux. As Metallica sang "Sad but true".

---

### Post by snowpine on 2010-08-14
(never mind)

---

### Post by Elfy on 2010-08-14
Thread closed - if you have gone elsewhere to deal with your issue that is fine.

No need to bring the attitude here that you did.

These 2 statements appear to be at odds with each other.

> I recently switched from Windows not suspecting that Linux would put those constraint on my work.

> I am administering linux machines for 10 years. I have read and analyzed tons of logs and you may be sure:

Closed

---

