---
title: "Network security question"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by niranjan_rao on 2011-07-26
Not exactly linux/ubuntu related question, but I think there are experts here who know what's really happening and can explain.

I came across article about wireless security at [http://www.siliconvalley.com/personal-technology/ci_18524092?nclick_check=1](http://www.siliconvalley.com/personal-technology/ci_18524092?nclick_check=1). One of the key quote from the article is "Anybody who tells me they do their online banking in a cafe needs to rethink what they can live with" in terms of risk, she said. "It's like writing (personal information) on a postcard because it hasn't been scrambled."

My question is if the bank site or other sites you are visiting is https or ssl based, is it possible to snoop the information? I thought whole purpose of https is encrypt the packages so that these things should not happen.

Thanks for the clarification

---

### Post by haqking on 2011-07-26
> **niranjan_rao said:**
> Not exactly linux/ubuntu related question, but I think there are experts here who know what's really happening and can explain.

I came across article about wireless security at [http://www.siliconvalley.com/personal-technology/ci_18524092?nclick_check=1](http://www.siliconvalley.com/personal-technology/ci_18524092?nclick_check=1). One of the key quote from the article is "Anybody who tells me they do their online banking in a cafe needs to rethink what they can live with" in terms of risk, she said. "It's like writing (personal information) on a postcard because it hasn't been scrambled."

My question is if the bank site or other sites you are visiting is https or ssl based, is it possible to snoop the information? I thought whole purpose of https is encrypt the packages so that these things should not happen.

Thanks for the clarification


If its not your computer or one you know well enough to trust then how do you know what tools may or may not be on the machine such as keyloggers capturing all your details.

DNS spoofing, when you type in [www.bankwhatever.com](www.bankwhatever.com) how do you know it isnt a webpage created by someone else set up and forwared by the router you are using etc again to capture your details.

It is like would you leave your wallet lying around at home, of course, would you do it in a cafe ? of course not ;-)

simple laymans answer i hope, and lots more responses could come to this also

---

### Post by niranjan_rao on 2011-07-26
I agree with your points. Especially DNS forging point is very interesting. 

Let's assume that I am going to starbucks and using my laptop or other mobile device. Hopefully, if you are careful about what you install, you have a clean machine.

DNS forging can forge the bank website, but can it forge the ssl certificates also? I remember reading few days back, to use ssl so that packet sniffers can not see what's going on. 

Just confused - many other sites say use SSL and then you read something like this which basically invalidates. If hackers can takeover public hotspot, they can easily do so on your home wifi network also. I have read at many places how easy it is to crack SSID etc.

---

