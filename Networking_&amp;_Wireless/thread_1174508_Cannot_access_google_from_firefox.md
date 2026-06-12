---
title: "Cannot access google from firefox"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by amishera on 2009-05-31
Hi,
I have ubuntu 8.04 installed in my computer. Whenever I try to search something by typing some keyword in the google toolbar of firefox, the "page not found" page is shown. Even if I try to access by typing "www.google.com" in the address field of the browser the same thing happens. What is more frustrating is that I cannot even access gmail. Except for google all other websites/search engines are accessible from firefox. This does not make any sense to me. Does any one have any idea what could be the reason behind this peculiar behavior.

---

### Post by dunbrokin on 2009-05-31
> **amishera said:**
> Hi,
I have ubuntu 8.04 installed in my computer. Whenever I try to search something by typing some keyword in the google toolbar of firefox, the "page not found" page is shown. Even if I try to access by typing "www.google.com" in the address field of the browser the same thing happens. What is more frustrating is that I cannot even access gmail. Except for google all other websites/search engines are accessible from firefox. This does not make any sense to me. Does any one have any idea what could be the reason behind this peculiar behavior.

Try changing your DNS to open DNS

[http://www.dyndns.com/about/](http://www.dyndns.com/about/)

---

### Post by amishera on 2009-06-01
> **dunbrokin said:**
> Try changing your DNS to open DNS

[http://www.dyndns.com/about/](http://www.dyndns.com/about/)

I am not sure I understand what you meant. However, I tried to choose the only reasonable and free option of creating a new "dynamic host" from the site you mentioned. But then even pinging that newly created host does not seem to recognize the host.

I think I have skipped some important information. I am using ubuntu from a laptop with wireless internet connection. If I try to ping "www.gmail.com" or "www.youtube.com" the command results in "unknown host". However pinging "www.yahoo.com" can report some reply.

This is a bizarre problem. I dont understand why would I have this particular problem for a particular os (ubuntu). It seems funny that a particular OS cannot cope with a particular website. It makes ubuntu a less and less attractive system every day.

---

### Post by dunbrokin on 2009-06-01
Right click on you wireless network icon - click on edit connections. Then click wireless and your Auto login router and click on Ipv4 settings. In this screen change the Method to "Automatic (DHCP) addresses only"

Then in the DNS Server type 208.67.222.222 and in the Search Domains type in 208.67.220.220.

This worked for me when I was having severe problems accessing certain sites.

---

### Post by amishera on 2009-06-02
> **dunbrokin said:**
> Right click on you wireless network icon - click on edit connections. Then click wireless and your Auto login router and click on Ipv4 settings. In this screen change the Method to "Automatic (DHCP) addresses only"

Then in the DNS Server type 208.67.222.222 and in the Search Domains type in 208.67.220.220.

This workproperties. The last dialog has a drop down menu with options such as "DHCP", "Zero configuration", "IPv4". I choose DHCP as always. 
ed for me when I was having severe problems accessing certain sites.

Man you saved my life. It works now. 
 
Let me tell you this, I had connection from a cable company and the DNS was 192.168.0.1. I don't get why it is so particular about DNS. In windows I dont have to enter DNS at all and it works.

---

### Post by amishera on 2009-06-02
However, I noticed that the dns that I set gets frequently reset. Could this be because of the disconnection/reconnection of the wireless? This has really become irritating.

---

### Post by dunbrokin on 2009-06-02
> **amishera said:**
> However, I noticed that the dns that I set gets frequently reset. Could this be because of the disconnection/reconnection of the wireless? This has really become irritating.

Sorry, I do not know enough of theory to know why the DNS seems more important under Ubuntu then under Windows...but that seems to be the reality of the situation. 

Not sure why your DNS gets reset.....whenever my Network Manager does a disconnect/reconnect, the DNS has not changed.

Perhaps somebody with more technical knowledge can fill us in on what is happening here.

Addendum: here is an after thought - set the Open DNS numbers at your router level rather than at your PC level...that may help....in fact, if memory serves me right, that is what I did to over come the reset of the DNS numbers.

---

