---
title: "Securing home wireless"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by jomarlinga on 2009-09-24
help pls,,how could i secure my wifi connetion inside our house

---

### Post by t0mppa on 2009-09-25
You need to access the router configuration. To do this, the easiest way would probably be to read the manual that came with it.

Once you gain access to the configuration, set up WPA2 and a lengthy pass phrase that doesn't consist of words. For instance, an easy way to get a pass phrase that isn't easily broken by dictionary attacks is to look at your bookcase and pick the first letters of first 15 book titles on a shelf.

Doing the above will make your network reasonably solid against strangers trying to connect to it or decipher the information being transfered in it. Other simple steps to strengthen your security would be to tone down the signal strength, so no one outside your home can pick it up and turning the wireless off when you don't use it.

Anything beyond these actions other than upgrading your pass phrase (*) will mostly make your daily life harder and won't provide any meaningful protection against people who know what they're doing.

(*) Two ways to accomplish that: 1) adding in more characters, upper case letters, numbers and special characters and/or 2) changing it regularly.

---

### Post by adamogardner on 2009-09-25
> **t0mppa said:**
> You need to access the router configuration. To do this, the easiest way would probably be to read the manual that came with it.

Once you gain access to the configuration, set up WPA2 and a lengthy pass phrase 

I have a linksys router and a modem from comcast cable company.  I don't have a manual or know quite what you mean by "configuration", or WPA2.  All I know is it came supported by windows and had a disk that sets up password and network name etc. in Windows.  I skipped all that and anybody can get on.  

So the question remains, how do I secure home wireless?

Thanks

---

### Post by ChumleyEX on 2009-09-25
Google, or linksys.com has ur back.. 


[http://www.linksysbycisco.com/US/en/learningcenter](http://www.linksysbycisco.com/US/en/learningcenter)

I'm sure you can type in the model of your router in google and maybe add something like secure wpa..


It's all very easy.

---

### Post by t0mppa on 2009-09-26
By configuration, I meant just that. There's usually two choices, either via a software that updates the router configuration or through a web interface (type the routers IP address into your browser). You'll probably find a manual on Linksys's website, if you don't know the default login.

And WPA2 is simply one of the choices for the encryption schemes, latest one at that and least likely to be broken.

---

### Post by darco on 2009-09-26
1. log into the router, typically 192.168.1.1
2. change the default ssid from e.g. linksys to whatever you like
3. Then choose NOT to broadcast your SSID
4. Use strong encryption: Choose wpa2 personal tkip/aes 
5. Go here to really have a secure pw [http://www.techzoom.net/tools/password-generator.en](http://www.techzoom.net/tools/password-generator.en)
6.Limit your IP address range, meaning instead of using the entire ip range of 256 address, limit to say 192.168.1.100 -115
7. Wireless -limit via mac address (not the most secure but combined w/wpa2 ....)

If I think of anything else, I will post...
good luck

darco

---

