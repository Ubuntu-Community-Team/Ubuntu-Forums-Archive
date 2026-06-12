---
title: "Wifi 2200BG help"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by gm__ on 2006-06-14
Hi      

/intel 2200BG, Breezy 2.6.12.10-686/

I was following all the How-to's to make my wifi card work but unfortunately it just
went worse.
In the beginning it was detected natively now its not even showing in Network settings, though its still there in "lspci"
So i guess i should clean the system from all Wifi drivers and start a-new.
Are there any commands to that?

Thanks for any help!

---

### Post by gm__ on 2006-06-15
Hi guys!

Here's another Happy Ubuntu Story :)

I upgraded to Dapper Drake , installed the windows driver Autorun.inf
with ndiswrapper & ndisgtk 
and my intel wifi card's working fine, i'm posting this with it right now.

Good Luck to ya all ! :)

---

### Post by dan4444 on 2006-06-15
Also, see my post [http://www.ubuntuforums.org/showthread.php?t=197315](http://www.ubuntuforums.org/showthread.php?t=197315)

Hope it helps. Please do let me know if it does.

---

### Post by gm__ on 2006-06-16
Thanks Dan for preventing me, in that case i will avoid to upgrade my kernel to 2.6.16.
By the way i find that its more simple to go by ndiswrapper , 
that way you only need to install one driver instead of three with IPW2200.

---

### Post by radii on 2006-06-29
Went through the expected (Intel 2200BG not working) until yesterday afternoon, when I moved to 2.6.15-25-386 with headers, source, etc..

Wifi is working!  PnP is working!

Phewwwww

---

