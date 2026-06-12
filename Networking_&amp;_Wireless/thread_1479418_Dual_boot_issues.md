---
title: "Dual boot issues"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by saurabhgeo on 2010-05-10
I have dual boot windows Vista and Ubuntu 9.10. Internet works perfectly well on ubuntu ( both wired and wireless )and also on windows . but the issue is that internet on windows works in uni but not at home ! where as no such issue with ubuntu 

I tried to figure out and found that Default Gateway was missing in Vista so i manaually pasted the values of default gateway values from ubuntu .

But i am not understanding what values should i put in settings for WINS , Primary DNS suffix and Alternate DNS Server 

Could some tell where I can locate these values from Ubuntu so that I can use them in Vista

---

### Post by mikewhatever on 2010-05-10
Usually, the DNS value will be the same as the default gateway. You can check what Ubuntu uses by right clicking the network manager icon in the panel and selecting 'Connection Info'.

---

### Post by pricetech on 2010-05-10
You should probably use DHCP on windows.  That way it should work no matter where you are.

But to answer your question;
Leave wins blank.  You won't use it.
Default Gateway is the IP of your router, which you already have.
DNS servers are usually assigned by your ISP, but most routers will function as a caching DNS server so try using the same address as your default gateway for your primary DNS.  If that doesn't work use 208.67.222.222 and 208.67.220.220  Those are Open DNS and they work just fine.
You can safely leave the DNS suffix blank.

---

### Post by saurabhgeo on 2010-05-11
well I would try this today the suggestion you people gave 

but i also found this thread 

[http://www.daniweb.com/forums/thread141979.html#]("http://www.daniweb.com/forums/thread141979.html#")

so i do have problems similar to this guy but i do not have any security software installed .

Well i get back to you soon i try your suggestions

---

### Post by saurabhgeo on 2010-05-12
I tried your suggestions 

by noting down all the information from the Ubuntu abount DNS, IP and Default Gateway 
I added it to Windows but unfortunately it did not worked .

Could you suggest something else and if you need to see some ouput of windows and Linux kindly let me know

---

### Post by pricetech on 2010-05-13
Did you try setting windows to use DHCP ??

---

### Post by saurabhgeo on 2010-05-13
I did tried that as well but no conection

---

### Post by pricetech on 2010-05-13
It may one of vista's paranoia settings.  You might get a quicker answer on a windows forum.

Not trying to run you off, but a lot of folks here don't even use windows any more if they ever did.

Good luck with your vista.

---

### Post by saurabhgeo on 2010-05-13
thanks i do appreciate your concern but vista forums seems to be very inactive as compared to Ubuntu :)

---

### Post by varunendra on 2010-05-13
Have you tried turning off the firewall? It's just a guess that it might be interfering with the communication between your Laptop (it is a laptop, right?) & your router.

Maybe pasting here the **screenshots of Connection Info in Ubuntu** & **that of Vista depicting IP, Subnet, Def Gateway, Primary & Secondary DNS** could help us get a better picture of your problem.

PS. I've recently been a (sort of) network admin at a mgmt. institute & connecting students' lappys to our network / internet was one of my daily business. The firewall issue did play the culprit most often !

---

