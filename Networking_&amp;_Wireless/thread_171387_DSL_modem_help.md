---
title: "DSL modem help"
date: 2006-05-06
forum: Networking &amp; Wireless
---

### Post by Ocxic on 2006-05-06
I have a router and a bell sympatico DSL modem, cnected like this:

my comp----->router----->modem--->internet

now i need to connect to my dsl modem, but both devices have a 192.168.*.* ip address so when i go to connect to my DSL modem nothing happens.

I've tried connecting directly to the dsl modem but it requires PPPoE and i haven't been able to get it to work properly. and i don't know how to get my computer back to normal whewn im done. so I'm wondering if there is a way to connect to my modem.  

Thanks guys.

---

### Post by dmizer on 2006-05-06
it should be easy enough to go into your router and change the ip range.

what is the make and model of your router?

---

### Post by Ocxic on 2006-05-06
D-Link DI-604, you think changeing the ip range will make a difference?

---

### Post by dmizer on 2006-05-06
yes ... change your router ip range to something completely different ... like 10.0.0.1 - 100 or something.  that way there will be no ip conflict between your modem and your router.

thing is, your modem is set up as a router as well.  usually you can get away with using a 192.168.1.1 for the modem, and a 192.168.0.1 for the router and get away with it, but that causes problems sometimes too.

alternatively, you could just change your router into a hub so it pulls it's ip from your modem rather than creating a network ip for itself.  if you have configured it for pppoe already, it will still work for pppoe as a hub.

---

### Post by Omnios on 2006-05-06
Take your main computer and hook it up to the second router connection, Go into networking to get the ip for the second connection which should hopefully auto detected in XP or even Linux I think. Usualy you have one ip for the router that connects to the modem and multiple ips for the different router connections which are useualy slightly different. Anyways that how I figured out to set my two systems out.

 The best solution would be to get the router manual online and it should list the ip ranges for the other connections.

---

### Post by Ocxic on 2006-05-06
i managed to get PPPoE workin so I'm all good now. thanks guys

---

### Post by mips on 2006-05-07
I know it is working but why would you want to,

1. Connect the D-Link to another modem seeing it has a built-in modem.
2. Use PPPoE when your router can do that stuff.

Just wondering....

---

### Post by Ocxic on 2006-05-08
my new DSL modem is wireless and has 4 ethernet ports, so I just wanna get rid of the router cause it's basically unnessaccary.

---

### Post by mips on 2006-05-08
[QUOTE=Ocxic]my new DSL modem is wireless and has 4 ethernet ports, so I just wanna get rid of the router cause it's basically unnessaccary.[/QUOTE]

What brand/model is your new 'dsl modem' ?

---

