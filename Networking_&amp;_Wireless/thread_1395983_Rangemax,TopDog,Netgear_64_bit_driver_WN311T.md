---
title: "Rangemax,TopDog,Netgear 64 bit driver? WN311T"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by bobby six on 2010-02-01
i need help getting 64 bit ubuntu 9.04 or mint 7 to recognise my rangemax/netgear wn311t wifi adapter.
 
the drivers work out of the box in 64 bit Vista, and will work fine in 32 bit 9.0/mint 7 via ndis wrapper.
 
when i use the drivers from the netgear website in 64 bit 9.04/mint7 i get an error " invalid driver." I searched the net for a 64 bit driver and found driver that recongnises the card in 64bit 9.04/mint 7 but when i go into terminal the result shows that that the card is "unclaimed" (it also says unmanaged i think) 
 
right now i am stuck using Vista and this wifi problem is killing my linux hobby...

---

### Post by bobby six on 2010-03-23
bump..

---

### Post by tentaro on 2011-02-03
I loaded wine and loaded the netgear wireless drivers into wine found the inf and sys file for vista 64 bit and copied them to a folder I would remember. I then used ndiswrapper to "install" the driver. That is as far as I have gotten I can't get the network manager to recognize the card. 

Not sure what else I have to do to get this to work but I am like you and I wish I could move to Ubuntu full time but it's a few small things that are holding me back and not having wireless is on of them.

---

### Post by tentaro on 2011-04-06
Unsure what the problem is but I thought maybe this was a problem wit h64bit Kubuntu but I have wiped the drive and installed 32 bit Kubuntu (both of them 10.10) and I am getting the same error message about unknown symbols ndiswrapper. I have run through every sort of config I can find on the web and have now tried both 64 nd 32 but Kubuntu version with the same errors. Why are other people able to get this same card working and I cannot? Is it maybe 2 new of a driver version? Anyone have a really old one? I would really really like to get wireless working. It is the number one reason I cannot use Kubuntu exclusively and I am tired of dual booting my system to be able to do anything.

---

### Post by walt.smith1960 on 2011-04-07
If I read correctly, you used Vista 64 bit files.  Vista drivers don't work with NDISwrapper, the .inf & .sys must be from XP or W2K drivers and must be 32 bit or 64 bit as appropriate for Ubuntu version.

---

### Post by tentaro on 2011-04-07
Ok thanks for the info.....that is the first time I have seen that little tidbit. I tried Win 7 first, then Vista. Anyway I got it running on 32 bit with a driver some one had all setup. Not even sure why I want 64bit anyway, just figured I might as well use it since I could use it :) I will look into trying to find some old drivers if they are even available anymore. Thanks again

---

### Post by walt.smith1960 on 2011-04-07
> **tentaro said:**
> Ok thanks for the info.....that is the first time I have seen that little tidbit. I tried Win 7 first, then Vista. Anyway I got it running on 32 bit with a driver some one had all setup. Not even sure why I want 64bit anyway, just figured I might as well use it since I could use it :) I will look into trying to find some old drivers if they are even available anymore. Thanks again

If it works I wouldn't mess with it.  NDISwrapper is not the preferred way to enable wireless, but more like a "if all else fails" or "I have an oddball device that doesn't have Linux support" or "my chipset is really new" type of solution.  At least that's the way I look at it.

---

### Post by chili555 on 2011-04-07
For the benefit of the searchers; from *man ndiswrapper-1.9*:> NAME
       ndiswrapper  -  Linux kernel module and user space tool to load and run Windows XP drivers for wireless cards

---

### Post by tentaro on 2011-04-07
Yeah I was really surprised that there is no native support for this card since it was still from the Draught- N era. But oh well and for anyone who wants to use the WN-311T and gets it to work with 64bit let me know but until then I guess I am using 32bit :)

also for anyone who wants to know, how this link :
[http://undiff.com/2008/11/how-to-get-the-netgear-wn311t-to-work/](http://undiff.com/2008/11/how-to-get-the-netgear-wn311t-to-work/)

gives you the exact instructions to get the card to work on 32bit versions.

---

