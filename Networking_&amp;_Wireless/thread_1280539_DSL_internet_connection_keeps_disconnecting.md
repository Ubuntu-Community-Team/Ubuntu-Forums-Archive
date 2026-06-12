---
title: "DSL internet connection keeps disconnecting"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by Raik.48 on 2009-10-02
Hi 

I have a DSL internet connection. I am on Ubuntu 9.04. i have connected the connection manually. there is no modem or anything. i entered my username and password in "dsl" tab of "network connections", and in the "IPv4 settings" i chose "Automatic PPPOE address only" and filled the ip address of isp in DNS servers. It works fine most of the time. but in a day sometimes it disconnects more than 10 times and i get irritated by it. Does anyone have a solution for this? 

Thanks!

---

### Post by Evelien on 2009-10-02
Examine your incoming phone line. Can you make it shorter? Is anything connected BEFORE the splitter that should be AFTER the splitter?
I have improved my S/N ratio by 2 dB just by cutting off an unused part of the phone line that led to the bedroom. (We all use wireless phones these days, but when the house was built, people wanted an extra phone in the bedroom. I forgot all about that until I got problems with my DSL-connection dropping off several times a day and people advised me to check the wiring...)

---

### Post by Raik.48 on 2009-10-02
I do not have a phone connection. I have an anteana in the rooftop , through which wire is comes to my pc.

---

### Post by Evelien on 2009-10-02
> **Raik.48 said:**
> I do not have a phone connection. I have an anteana in the rooftop , through which wire is comes to my pc.
 
Owww, I see...
 
Then maybe you mean something else by DSL than I do...
I thought DSL was the abreviation for "Digital Subscriber Line", the technique to connect to the Internet over a twisted-pair (i.e. telephone) cable.
What does your abreviation DSL mean?

---

### Post by jonobr on 2009-10-02
Hello

I think a discription of what your connecting with may help here.

It sounds as if your using some WISP or wireless ISP.

As mentioned DSL uses a telephone line to carry the data and a modem to encode and decode at your end.

You pretty much have the same thing, however, your phone line is RF or radio waves and your modem is problem some customer premise equipment that enodes and decodes your data to/from RF.

Maybe you could tell us the device your connecting your computer to,
is there a brand name?
What Kind of cable connects your device from your computer, is it ethernet?
 Also, Im thinking you may just need to change your NM settings, but again, if you explain the setup we could help.

Im thinking you dont need to enter the ip address or anything like that.
this information should be dynamically assigned to you, but again first things first

---

### Post by Raik.48 on 2009-10-04
I don;t know the brand name of the device that is in the rooftop.  But the wire from that device comes to a splitter. Then there is one port for the anterna and the other port says LAN, from that LAN port a cable comes out and goes into my pc ethernet port( or the port which seems like the phone line ) of my motherboard.

I connected the internet in DSL because any other connection seems to fail, and my isp also has given me a username and password, and DSL is the only section where there is such name and password fields. And in the IPv4 setting i changed to Automatic PPoE addresses only and kept by DNS server ip address. and leaving the "Search Domian" blank cause i don;t know.

Thanks for replying me a lot!

---

### Post by jonobr on 2009-10-05
so when you open a terminal and type ifconfig,
what do you get?

Cheers

---

