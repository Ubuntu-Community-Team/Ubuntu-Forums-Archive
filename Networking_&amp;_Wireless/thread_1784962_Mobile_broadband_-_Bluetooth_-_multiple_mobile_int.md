---
title: "Mobile broadband - Bluetooth - multiple mobile internet sharing"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by manickaselvam on 2011-06-17
Hi Guys,
              Its really cool ubuntu (Natty) now. If am away from home, using the "mobile broadband" utility for accessing the GPRS internet through NOKIA mobile (bluetooth connected). 

Its cool, working like a charm with "Bluetooth Manager" just a click away. 

But I feel the internet speed is less with single mobile. Is it anyway 2 or more mobiles can be connected for accessing the GPRS internet, so that the ultimate speed will be verygood?

Anyone else tried with this? I tried, any individual mobile connectivity is established but not 2 or more mobiles GPRS can be accessed at a same time.

Any suggestions pls?

Thanks.

Manicks:)

---

### Post by jamadagni on 2011-07-03
Boss, that isn't how it works. The basics is that only one connection will be chosen for IPv4 routing and DNS, so just by connecting to two phones you can't improve your speed. However, bluetooth based GPRS connectivity will be definitely slower compared to cable-based one. 

Anyhow, can you tell me how you accomplished bluetooth connectivity? I'm looking for it for a different reason.

---

### Post by manickaselvam on 2011-07-05
Yeah...!!! Thats possible JAMADAGNI... Am working for Routing, Switching, IPv4, IPv6, DNS  & WiFi...  So quite familiar with these concepts... Anyhow I'm ok  with the GPRS bluetooth connectivity, getting about 160kbps in daytime  and around 200kbps in latenights...!!! This is enough just for checking  emails, browse the web, when you are in remote area?

I shall give you the techi details, may be this will be useful for  anyone in ubuntuforums also... USB 1.1 cable give 12Mbps & USB 2.0  give 480Mbps path... Bluetooth Wireless 2.0 give around 3 Mbps path...  Obviously transferring 200kbps data either way is good enough unless  otherwise you want to transfer more than 3Mbps...!!!  I personally  checked this data rates. Am quite fine...!!!

By the way there is the concept of "Load balancing" & "Combined  Bandwidth", two or more internet connectivity can be used together,  either by distributing the different bandwidth for different  applications (like 200kbps for each application) or clubbing the  bandwidth for single application (together 400 kbps for single  application).  

Couldn't able to figure it out for using those above method with the  bluetooth. Any experts those who used with any "additional hardware" or  "with software" can please share the details.

ACCOMPLISHING Bluetooth connectivity is simple, you may know this  already for accessing the files. But for using mobile data connectivity  you need to install "Bluetooth Manager", that will do everything for  your Ubuntu. 

Thats all. Bye.

-Manicks

---

### Post by jamadagni on 2011-07-05
Hi -- sorry to think you are a noob. Looks like relatively I'm "noob"-er compared to you. Thanks for the tip about Blueman (I take it by bluetooth manager you mean Blueman). I'll look into it.

---

