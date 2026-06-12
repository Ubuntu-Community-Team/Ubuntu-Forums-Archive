---
title: "wireless router advice needed"
date: 2006-04-11
forum: Networking &amp; Wireless
---

### Post by towsonu2003 on 2006-04-11
I have four questions I hope someone could answer... Let's see. This is the product I'm thinking to buy: [linksys wrt54gl]("http://www.newegg.com/Product/Product.asp?Item=N82E16833124190") (wireless g router). I'll be taking this to Turkey (bc everything there is 3x expensive than in the US). 

My questions: 
1. How do you setup this router to use an adsl modem and dhcp? Is it hard?
2. How do you setup this router to use a cable modem and dhcp? Is that hard?
3. Do you think this American product would work in Turkey? What information would I need to get this question answered?
4. From experience, would you recommend another wireless router instead of this one? The setup will be <<adsl/cable modem->router->2 computers (ethernet) and 2 computers (wireless)>>, all computers will be running linux (no servers, only desktops, probably ubuntu). 

Any help would be appreciated. Thanks :)

---

### Post by prizrak on 2006-04-11
I'm not sure what the interface to ADSL is. It should run just fine in Turkey or anywhere else the WAN port (one plugging into your modem) is nothing but simple ethernet. DHCP is enabled by default so is wireless. They do have an online guide and you seem to have little trouble reading English ;). I have the g version of it and it's not very hard to deal with it. If you are doing wireless make sure you enable WPA just ot make sure you are not serving your card # to the neighborhood when ordering stuff ;) 
If you have more specific set up questions later feel free to ask I'm sure enough of the community uses it. (You can PM me as well I got quite a bit of experience with Linksys routers).

---

### Post by ember on 2006-04-11
I don't know about electricity in Turkey, yet you may need to get an adapter from the 110/115V used in the USA to something different (e.g. Germany uses 220/230V)

Anything else should be a minor problem.

---

### Post by bjweeks on 2006-04-11
> 1. How do you setup this router to use an adsl modem and dhcp? Is it hard?

Just plug it in :)

> 2. How do you setup this router to use a cable modem and dhcp? Is that hard?

Plug it in.

> 3. Do you think this American product would work in Turkey? What information would I need to get this question answered?

The only issue is the power convertion.

> 4. From experience, would you recommend another wireless router instead of this one? The setup will be <<adsl/cable modem->router->2 computers (ethernet) and 2 computers (wireless)>>, all computers will be running linux (no servers, only desktops, probably ubuntu).

Nope, this is one of the best routers on the market.

I would put a aftermarket firmware on it to unlock the power of it.

---

### Post by towsonu2003 on 2006-04-11
Nice, 3 positive replies out of three. I'm gonna wait another 3 days and buy this thing :) The conversion won't be a problem, I have like 6 power adaptors at home. I'm happy now, until someone comes up with negative replies ;)

Thanks so much for the replies. I really appreciate it.

---

### Post by bjweeks on 2006-04-11
Do you plan on useing aftermarket firmwares cause if not the GL is a waste of money.

---

### Post by prizrak on 2006-04-11
[QUOTE=bjweeks]Do you plan on useing aftermarket firmwares cause if not the GL is a waste of money.[/QUOTE]
Even if not it's better than the G, as the G has half the RAM and needs to be restarted once in a while if there is alot of data being sent through (not uncomon on my network), especially if the data has to be inspected by the built in firewall (such as BT downloads).

---

### Post by bjweeks on 2006-04-11
[QUOTE=prizrak]Even if not it's better than the G, as the G has half the RAM and needs to be restarted once in a while if there is alot of data being sent through (not uncomon on my network), especially if the data has to be inspected by the built in firewall (such as BT downloads).[/QUOTE]

The firmware image used my linksys fits the 2mb flashram so it doesn't matter. The GL will also lock up under heavy load unless you use a aftermarked firmware and change the settings.

---

### Post by towsonu2003 on 2006-04-11
[QUOTE=bjweeks]Do you plan on useing aftermarket firmwares cause if not the GL is a waste of money.[/QUOTE]
For now, no. It seems there's not much done. But I'd like to have some flexibility for future, not to mention having a router that runs linux ;) 

what would you recommend for cheaper? just the wrt54g or some other product / line? If it matters, I expect the fastest network speed to be around 512k or so.

---

### Post by bjweeks on 2006-04-11
[QUOTE=towsonu2003]For now, no. It seems there's not much done. But I'd like to have some flexibility, not to mention a router that runs linux ;) 

what would you recommend for cheaper? just the wrt54g or some other product / line? If it matters, I expect the fastest network speed to be around 512k or so.[/QUOTE]

The WRT54GL is the WRT54G v4 after v5 they stoped useing linux to save money on the flash chips. So unless you want the abilty to use other firmware, there is no point of spending the extra money.

I am happly running DD-WRT on a WRT54G v3 and its great.

---

### Post by prizrak on 2006-04-11
There is actually aftermarket firmware for Gv5 as well now. Like I said the only difference is the amount of RAM.

---

### Post by bjweeks on 2006-04-11
[QUOTE=prizrak]There is actually aftermarket firmware for Gv5 as well now. Like I said the only difference is the amount of RAM.[/QUOTE]

Yes, DD-WRT runs but you have to flash via JTAG. The ram is big if you want to run better firmware.

---

### Post by towsonu2003 on 2006-04-12
one more question... suppose I bought it. how would I try whether it's properly working (not broken out of the box)? I don't have broadband here, and won't be able to buy it for another 2-3 months. And the warantee won't be ok in another country.

---

### Post by bjweeks on 2006-04-12
[QUOTE=towsonu2003]one more question... suppose I bought it. how would I try whether it's properly working (not broken out of the box)? I don't have broadband here, and won't be able to buy it for another 2-3 months. And the warantee won't be ok in another country.[/QUOTE]

Hook it up and go to 192.168.1.1 in your browser.

---

### Post by towsonu2003 on 2006-04-14
ok, I bought the toy and 192.168.1.1 is working. But now, I have three more questions: 

1. I did two setting changes tru 192.168.1.1 (stop UPnP support, disable http access to 192.168.1.1 but enable https access to it instead). After these, I rebooted to Linux (from Windows, where I did these changes) and couldn't access 192.168.1.1 (what's the name of this?). Windows couldn't access it either. I had to reset the router and got scared. Which one got me kicked out of the router's 192.168.1.1? UPnP or https? (got too scared to do trial and error)

2. The thing's firewall is too primitive. For example, it doesn't allow firewall setting like in firestarter (block everything, open specific ports only). There are ~10 ports that can be closed and that's all. Is there a workaround for that? 

3. I'm interested in OpenWRT, but it seems you can only telnet or ssh to it. Does it have a GUI (as like linksys firmware at 192.168.1.1)? Will ask the same thing to their forum as well, but, ehm, this place is more friendly than any other forums I saw till now :oops: 

thanks a lot for the help, it was great. 

PS. Will test whether it works in Turkey in 2-3 months or so.

---

### Post by bjweeks on 2006-04-14
[QUOTE=towsonu2003]ok, I bought the toy and 192.168.1.1 is working. But now, I have three more questions: 

1. I did two setting changes tru 192.168.1.1 (stop UPnP support, disable http access to 192.168.1.1 but enable https access to it instead). After these, I rebooted to Linux (from Windows, where I did these changes) and couldn't access 192.168.1.1 (what's the name of this?). Windows couldn't access it either. I had to reset the router and got scared. Which one got me kicked out of the router's 192.168.1.1? UPnP or https? (got too scared to do trial and error)

2. The thing's firewall is too primitive. For example, it doesn't allow firewall setting like in firestarter (block everything, open specific ports only). There are ~10 ports that can be closed and that's all. Is there a workaround for that? 

3. I'm interested in OpenWRT, but it seems you can only telnet or ssh to it. Does it have a GUI (as like linksys firmware at 192.168.1.1)? Will ask the same thing to their forum as well, but, ehm, this place is more friendly than any other forums I saw till now :oops: 

thanks a lot for the help, it was great. 

PS. Will test whether it works in Turkey in 2-3 months or so.[/QUOTE]

1. Leave UPnP OFF. If you turn on https you now have to go to 'https://192.168.1.1'.

2. 2. The thing's firewall is too primitive. For example, it doesn't allow firewall setting like in firestarter (block everything, open specific ports only). There are ~10 ports that can be closed and that's all. Is there a workaround for that? 

By default it blocks everything and you have to open the port's in apps&games you want to foward to a box.

3. Yes, openwrt has a GUI but I have never used my self, I use DD-WRT it is close to openwrt. It has a GUI and you can ssh,telnet in. 

[http://dd-wrt.com](http://dd-wrt.com)

Also if you plan on flashing to a new firmware post here cause there is a few warnings I should give you.

---

### Post by towsonu2003 on 2006-04-14
[QUOTE=bjweeks]1. Leave UPnP OFF. If you turn on https you now have to go to 'https://192.168.1.1'.
[/quote]
of course, [https://bla](https://bla)... what was I thinking?? thanks a lot :)
[QUOTE=bjweeks]
2. By default it blocks everything and you have to open the port's in apps&games you want to foward to a box.
3. Yes, openwrt has a GUI but I have never used my self, I use DD-WRT it is close to openwrt. It has a GUI and you can ssh,telnet in. 
[http://dd-wrt.com](http://dd-wrt.com)
[/quote]
that's great help. Thanks a lot :)
[QUOTE=bjweeks]
Also if you plan on flashing to a new firmware post here cause there is a few warnings I should give you.[/QUOTE]
What should I be careful about? I will most probably flash it, but in a few months (when I will actually use the router, right now, it's sitting in its box peacefully).

---

### Post by bjweeks on 2006-04-14
This is how I flash my router(haven't bricked since I starting doing this)

1. Before you flash to a new firmware, first reset to factory defaults(must do).
2. After you flash to a new firmware, reset to factory defaults.
3. If you use DD-WRT standerd on the WRT54GL you must flash to mini first.

FYI's 

You have the WRT54GL aka WRT54G v4. Also once you get hooked on DD-WRT(or what ever firmware you pick) ASUS and some other companys make better routers based off the same chipset so some WRT54G firmwares will work.

Don't use sevasoft products, they violate the GPL.

My recommendation of firmware is DD-WRT v23 SP1(not released) v23 is very buggy but SP1 fixes almost the all bugs. It should be out soon.

---

### Post by towsonu2003 on 2006-04-14
[QUOTE=bjweeks]haven't bricked[/quote]
brrrr scary thought 
[QUOTE=bjweeks]
Don't use sevasoft products, they violate the GPL.
[/quote]
yes I heard of that. It's surprising (and depressing) no action is taken against them. 
[QUOTE=bjweeks]
My recommendation of firmware is DD-WRT v23 SP1(not released) v23 is very buggy but SP1 fixes almost the all bugs. It should be out soon.[/QUOTE]
I really appreciate this help. It will be most helpful once I start using the new toy :)
again, thanks a lot.

---

### Post by bjweeks on 2006-04-15
> brrrr scary thought 

Before I started I bricked it all the time. So I would have to spend 30 mins un bricking it...

Yes, you can totaly kill you router but it's REALLY hard.

---

### Post by Lucius Junius on 2006-04-15
Buffalo WHR-G54S seems to be popular for DD-WRT now, it's a cheap router, not a lot of ram ( 4/16), but it worked on tftp flash for me, you just have to wait until the right moment to flash it, after plugging / unplugging it.  Rumour has it that Buffalo is releasing a router with 128mb ram in the third quarter, but it won't be cheap.

make sure you flash the right version of DD-wrt, for WHR-G54S, do the latest unstable beta v23sp1 dated as of today and going forward, there is a new release every evening.

---

### Post by towsonu2003 on 2006-04-15
thanks for the heads up. For now, I'm just waiting to go back home to see what I'll do (in 2-3 months). [QUOTE=Lucius Junius]Rumour has it that Buffalo is releasing a router with 128mb ram in the third quarter, but it won't be cheap.[/QUOTE]With 128mb ram, I'll run Puppy/DSL on it ;)

---

### Post by matthew on 2006-04-15
By request of the OP I moved this to the networking forum...I'll also be watching this thread as I have a WRT54g v2 that I want to switch to the DD-WRT after I move to Morocco (offtopic: leaving in less than a week, back online as soon after that as possible).

---

### Post by towsonu2003 on 2006-04-15
[QUOTE=matthew]By request of the OP I moved this to the networking forum...[/quote] thanks a lot :) I wasn't expecting this thread to become this helpful while staying focused on linux. 
[QUOTE=matthew]
I'll also be watching this thread as I have a WRT54g v2 that I want to switch to the DD-WRT after I move to Morocco [/QUOTE]
Let me know if it works there. I'm still nervous ;)

---

### Post by bjweeks on 2006-04-16
I'm glad you guys are giveing DD-WRT a try, I've running it for a few months and it' been great.

---

