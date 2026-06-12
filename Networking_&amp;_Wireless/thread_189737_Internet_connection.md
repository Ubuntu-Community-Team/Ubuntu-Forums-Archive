---
title: "Internet connection"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by streak on 2006-06-05
Sorry my problem is with 5.10 I will move the question there.

Streak


I have installed 5.10.
All went OK and I can see my office network.

The help files says that to set up a new connection (ie. to the internet) you click the add button on the network setup pop up and shows a screen shot of what this setup page should look like.

When I go to this network setup page it shows my active ethernet connection but there is no add button.

My ADSL connection requires a userid and password and this is what I want to set up.

Where to from here?

TIA

Streak

---

### Post by mips on 2006-06-08
Streak,

tell me a bit more about your adsl connection:
USB or Ethernet ?
ADSL device Make & Model for you modem/router ?
Your IP settings for this device ?
Your ISP ?

From the sounds of things you need pppoe but it might not be necesarry depending on my 3rd question above.

---

### Post by streak on 2006-06-09
It's an ethernet connection.
Marconi router.
ISP is Mweb

On my XP PC's one only needs to setup a broadband connection that requires logon.

I hoped for there to be something similar in Ubuntu. The documentation says there is an add network place under network setup but there is none.

---

### Post by mips on 2006-06-12
Streak,

Sorry been away in the berg for a while.

I assume you have ubuntu as opposed to kubuntu ?

From what you say i gather the actual login process is done from the PC and not the router therefore you are running a pppoe client on the PC, correct ?

If the answer to the above is 'yes' then you have your router in bridged mode i suspect. You need to login to your router via a browser and specify 'routed' mode and configure the username and password in the router itself. After this you simply need to go to System->Networking and enable dhcp on the pc/ubuntu.

You could use pppoe config from the command line but the above method is the better route to go.

---

### Post by streak on 2006-06-12
Hi,
Hope you enjoyed the Berg.
It's a standard ADSL setup it's just that I have chosen to make each user login to the ADSL account each time they want to use it rather than having the login details coded into the router. That's on XP anyway.

I want to acess the router in the same way using Ubuntu (nor Kubuntu). However I cant find anywhere where I can setup this type of login.

Streak

---

### Post by mips on 2006-06-12
I have no experience with linux pppoe gui clients but have you looked at **tkpppoe** ?

[http://roaringpenguin.luky.org/pppoe/tkpppoe/](http://roaringpenguin.luky.org/pppoe/tkpppoe/)

Don't really know if it is suitable to your environment. The one thing you don't want is it retaining username & password info.

---

