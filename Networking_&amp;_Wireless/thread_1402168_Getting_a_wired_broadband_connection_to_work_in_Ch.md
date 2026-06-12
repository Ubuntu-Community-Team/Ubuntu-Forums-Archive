---
title: "Getting a wired broadband connection to work in China"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by JlyGrnMigt on 2010-02-08
We finally got internet in our apartment in China, but my husband was the only one home when the guy came to set it up (on his windows machine).

He connects by plugging in, then clicking a desktop icon labeled "Broadband Connection" where a box pops up with a username, a password box, and some buttons, one of which says "connect".  

I am trying to figure out how to set this up on my netbook so that I&#12288;can use the internet at home too.  I&#12288;have a feeling that even if I had been home when the setup guy came, he wouldn't have had a clue what to do with mine anyway.

On the WinXP machine: Connection Properties state that this is a PPPoE connection, with TCP/IP, QoS, and Deterministic Network Enhancer all checked. Under the security tab, unsecured passwords are allowed.

Can anyone help?

---

### Post by s3MA00RRNY on 2010-02-08
Right click the network icon and hit "Edit Connections". Go to the DSL tab and add a new connection. Enter your details and click OK.

---

### Post by JlyGrnMigt on 2010-02-09
Hrm, well, it's good to know I was putting it in the right spot, but I didn't really know what to enter where when setting that up.  

The first screen has a spot for username and password, which I filled, but I don't know what to put for service.  Any idea what typically goes there?

Thanks.

---

### Post by JlyGrnMigt on 2010-02-18
Ok, so I've figured out that I don't need to put anything in the service box, but I still can't get it to connect.  Any additional suggestions would be welcome!

Thanks:p

---

### Post by argothian on 2010-02-18
I am in Beijing now, I usually connect to the internet through wireless router, but I tryed what pcdude2143 said and it works for me - I have chinese ISP. Edit connections -> DSL -> Add ... I only wrote username and password and checked "connect automaticaly". Then I had to logout and login and its working.

---

### Post by JlyGrnMigt on 2010-02-23
*sigh* still nothing.  For some reason, I can't edit my connections, so I deleted and re-added.  I made it available to all users even though I'm the only one, but it doesn't work either way.

I did all that, again, and the indicator just spins for about 20 seconds or so then pops up to tell me I am "now offline".  I logged in and out, rebooted, manually told it to connect, disabled wireless...each time nothing.

Thanks for all the suggestions.  I've written to zareason tech support now to see if they have any ideas.

---

### Post by JlyGrnMigt on 2010-02-25
As it turns out, this thread seems to be my  prob: [http://ubuntuforums.org/showthread.php?t=1308020&highlight=PPPoE](http://ubuntuforums.org/showthread.php?t=1308020&highlight=PPPoE)

I'm currently connected using the workaround, but will try the solution that gets network manager behaving so I can use my VPN.

---

