---
title: "Captive portal wifi issue"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by cena4592 on 2011-11-02
In running an Acer Aspiron 5315 laptop with Ubuntu 11.10.  Atheros 5008 wireless

I am at a motel that uses wifi with a captive portal. That is a wifi that is open but whenyou connect and go online redirects you to a portal page for a password and to accept terms and agreements.

My problem is that my Ubuntu Laptop, and my Samsung Galaxy Tab 8.9 tablet, do not redirect to the portal. It will connect to the network but when you try to go online They both will display a loading page for a couple minutes then cannot connect page. 

My smartphone, LG Optimus V, my Uncles Laptop A Toshiba Satellite Windows 7 and his smartphone HTC Hero S also connect to it and redirect fine. 

The problem is not a problem with my laptop wireless. When i make my phone a hotspot it works fine.

If there is any help that you can provide it would be much appreciated.

---

### Post by jonobr on 2011-11-02
Is the redirect site browser specific?

I.e. only supports IE but not firefox?

I have seen that before....

---

### Post by cena4592 on 2011-11-02
It doesn't appear to be browser specific. My phone uses Dolphin Brower and it redirect just fine. My Uncle uses Chrome and IE on his laptop and Default Android on his phone and they connect fine.

---

### Post by jonobr on 2011-11-02
Your going to have to go technical....
Open a terminal window and type

```
sudo tcpdump -vvv -i any -s 1600 port 80 
```

Open up your browser, hopefully you will see something
post it here if tis not anything to secretive.

You can drop me a private reply of it is

Cheers

---

