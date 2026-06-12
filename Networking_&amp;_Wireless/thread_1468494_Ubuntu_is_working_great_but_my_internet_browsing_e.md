---
title: "Ubuntu is working great but my internet browsing experience is very slow"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by gnik1 on 2010-05-01
I have tried a couple of improve ubuntu internet speed posts and haven't seen any improvements. Might have even made it worse.

Pages aren't coming up sometimes until the second try. I've reset my router and modem just in case to clear them up. I have windows machines on the network that are unaffected by any slowdowns on the network.

Can someone please point me in the right direction of improving the browsing performance of firefox/ubuntu?

I am really impressed by ubuntu thus far as I've installed some alternative apps that I desire to use/used in windows.

Thanks so much in advance.

---

### Post by oldgeekster on 2010-05-01
> **gnik1 said:**
> I have tried a couple of improve ubuntu internet speed posts and haven't seen any improvements. Might have even made it worse.

Pages aren't coming up sometimes until the second try. I've reset my router and modem just in case to clear them up. I have windows machines on the network that are unaffected by any slowdowns on the network.

Can someone please point me in the right direction of improving the browsing performance of firefox/ubuntu?

I am really impressed by ubuntu thus far as I've installed some alternative apps that I desire to use/used in windows.

Thanks so much in advance.I had a **very** similar problem in using FireFox under Karmic Koala when I first loaded it - here is what fixed it for me:

----------
Open Firefox and in the URL window type:
About:Config
and hit Enter

After assuring the popup you will be careful, scroll down to:
network.dns.disableIPv6

If it is not already set to "True", Right-click on it and select  "Toggle" then it should be.

Close/re-open your web browser and surf to test the speed as you move  from site to site.  
----------

This was the ONLY change I made on my Karmic Koala system after  upgrading to it and it did away with all of the sluggishness I had  previously been experiencing in FireFox (I chose to do the on-line "Upgrade" to version 10.04 and thus far have had no problems with it - but I did check to make sure that item was still set to "True").

Of course you mileage may vary, but worked for me. :popcorn:

Let us know if that worked for you - sometimes old stuff can come back to haunt us. ;)

---

### Post by gnik1 on 2010-05-01
VIOLA!!!

OMG!!!

THANK YOU SOOO MUCH!!!


U have made me so very very happy. Thank you so much for your experience. 

Your suggestion worked like a charm.

Thanks again!

[SOLVED]

---

### Post by oldgeekster on 2010-05-01
> **gnik1 said:**
> VIOLA!!!

OMG!!!

THANK YOU SOOO MUCH!!!


U have made me so very very happy. Thank you so much for your experience. 

Your suggestion worked like a charm.

Thanks again!

[SOLVED]Glad to hear it worked for you too.  Sometimes it is the simplest things that get in the way eh?

Warm Regards,
-=dave=-

---

### Post by gnik1 on 2010-05-01
I'm so grateful that I can continue to enjoy this experience without frustration.

---

### Post by speedync on 2010-05-05
Another big thank you from me. I was going nuts wondering why my internet speed had taken a massive dive, but this fixed it for me also. Thanks again.

---

### Post by souse on 2010-05-07
Hi All,

I wiped off Microsoft Vista from my laptop and installed 10.04. Though the interfaces look great, my internet browsing was very slow and most of the times didn't load at all. I thought I had done a mistake as this laptop is also used by my wife. 

I went through lot of forums to fix it, disabling ipv6 dns, fiddling with firefox browser config etc, but no avail. I came across a post where they mentioned the internet speed improved after they pointed the DNS to local DSL modem ip address rather than public or provider DNS. I changed it and immediately saw significant improvement. 

In face most of the site that never loaded (including archive.ubuntu.com) were working fine. I am grateful for the forum community who have been excellent in terms of support. I will stay with Ubuntu!

---

### Post by gnik1 on 2010-05-07
> **souse said:**
> Hi All,

I wiped off Microsoft Vista from my laptop and installed 10.04. Though the interfaces look great, my internet browsing was very slow and most of the times didn't load at all. I thought I had done a mistake as this laptop is also used by my wife. 

I went through lot of forums to fix it, disabling ipv6 dns, fiddling with firefox browser config etc, but no avail. I came across a post where they mentioned the internet speed improved after they pointed the DNS to local DSL modem ip address rather than public or provider DNS. I changed it and immediately saw significant improvement. 

In face most of the site that never loaded (including archive.ubuntu.com) were working fine. I am grateful for the forum community who have been excellent in terms of support. I will stay with Ubuntu!


Could you post how you did that?

---

