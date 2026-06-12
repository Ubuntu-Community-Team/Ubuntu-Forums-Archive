---
title: "Wireless not working ubuntu 10.10"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by waterwalker23 on 2011-03-19
Hello everyone,

I'm pretty new to ubuntu...  I just installed 10.10 on my Dell Inspiron 1440 laptop, but I cannot get the wireless to work for me.  My Dell uses the Intel WiFi Link 5100.  When it first boots up the wireless is disabled.  If I click on the F2 (wireless) button absolutely nothing happens.  When I click on the wireless notification the wireless connections is grayed out.  

If I run the following command: gksu gedit /var/lib/NetworkManager/NetworkManager.state k the wireless enabled = false.  I have edited it to true and saved the change, but when I restart the network manager it doesn't resolve the problem.  It changes back to false.

I would greatly appreciate any help at all.  I have used ubuntu on a desktop in the past with no problems, but this is my first time on a laptop.

Thanks for any and all suggestions.

---

### Post by kestrel1 on 2011-03-19
See if there are any Additional Drivers available. Go to System > Administration > Additional Drivers
If there are install them.
If not type the following in to a terminal:
```
lspci
```
& post the result.

---

### Post by waterwalker23 on 2011-03-19
That was odd... I was unable to check for additional drivers because I had no connection.  I plugged it in and that did the trick.  After plugging in the wireless started working.  It listed all the available wireless connections.  All is fine now.

Thanks for your quick response!!

---

### Post by kestrel1 on 2011-03-19
That is a bit wierd. Oh well at least it is working now.

---

### Post by mezsen on 2011-03-19
I have ubuntu 10.10 on parkard bell r1938. am having problems connected to wifi. I Can't turn the wifi on. is it missing a driver? any ideas??

---

### Post by kestrel1 on 2011-03-20
have you tried the above?
post the results of ```
lspci
```

---

### Post by mezsen on 2011-03-20
i type the code : lspci in the terminal. there's atheros AR5001X+. Is that the driver for wireless??

---

### Post by kestrel1 on 2011-03-20
Yes, I think you will find that is your wireless card.
Have a look at the following as it may help:
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by mezsen on 2011-03-20
thanks will give that a try  Not sure what all these code means-lol 

i found this [http://piloverdon.blogspot.com/](http://piloverdon.blogspot.com/)  i was trying to work this out

---

### Post by Ayers on 2011-03-20
I am having a similar issue, the network manager or wicd wont allow me to connect...it keeps asking me for the password although the one i use is correct

---

### Post by mezsen on 2011-03-21
thanks [kestrel1]("http://ubuntuforums.org/member.php?u=458492") got the Ethernet cable connected and have access to internet:)  

i'm still trying to get my wirless to work. this terminal coding is new to me - will c how it goes!

---

### Post by kestrel1 on 2011-03-21
> **Ayers said:**
> I am having a similar issue, the network manager or wicd wont allow me to connect...it keeps asking me for the password although the one i use is correct

I you have the password written down, double check it. If you have it in a text document, copy & paste it. Sounds like the wireless is fine if you are getting as far as the password for your wifi, so make sure that the password is correct.

---

### Post by kestrel1 on 2011-03-21
> **mezsen said:**
> thanks [kestrel1]("http://ubuntuforums.org/member.php?u=458492") got the Ethernet cable connected and have access to internet:)  

i'm still trying to get my wirless to work. this terminal coding is new to me - will c how it goes!

What coding are you having trouble with? Let us know & we will try to help you out.

---

### Post by mezsen on 2011-03-21
With the ethernet cable connected I update the additional driver - hoping to fix my wireless card.

The wifi logo is grey out with "!"  it will not search for any local wifi around. I know my router SSID is visible. 

kestrel1- i dont think its the password. it wont even search for any local wifi around. ( i hope this make sense??)

I think the wireless Driver is there and its turn off somehow. So frustrating!

---

### Post by mezsen on 2011-03-21
Hey Kestrel1, What is "linux-backports-modules-intrepid"??

do you search and install that using Synapthic Package Manager?

thanks

---

### Post by kestrel1 on 2011-03-22
> **mezsen said:**
> Hey Kestrel1, What is "linux-backports-modules-intrepid"??

do you search and install that using Synapthic Package Manager?

thanks
They are for Intrepid (Ubuntu 8.10)
No use in later versions really.
Do you have a hardware switch that switches the wireless off? I know some laptops do.
Are you using Ubuntu 10.10?

---

### Post by mezsen on 2011-03-24
Yeah it has running on Xp- not sure how to activate it on Ubuntu- andy ideas? i tried install inf  file 4 using ndiswrapper - The hardware is showing present.

The drivers is in But its block somewhere- please help

---

