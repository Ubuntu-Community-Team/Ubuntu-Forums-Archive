---
title: "Optus 3G Connection Issues (Huawei E1762, Post-paid Business Plan)"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by Akavashi on 2010-11-16
Hey guys,
Just yesterday, I purchased an Optus 3G Wireless Modem (Huawei E1762) based on a **business plan** and cannot currently get it online with Maverick.
I've tried setting up using the wizard by choosing *Australia->Optus->"My plan is not listed..."*, and then setting "*Selected plan APN*" to ***yesbusiness*** as listed [[COLOR="DarkOrange"]_here_[/COLOR]]("http://www.optus.com.au/dafiles/OBCA/Marketing/Cust%20Experience/Mobile/StaticFiles/Documents/Optus%20Business%20Mobile%20Broadband/Huawei%20APN%20Work%20Instructions.pdf"). I've also tried APN's: *connect*, *preconnect* and *internet*.

On a side note, I've also tried on another attempt to only set the Authentication method as **PAP** as described [[COLOR="DarkOrange"]_here_[/COLOR]]("http://forums.whirlpool.net.au/archive/1304752").

This is also the output of **usb-devices**:
```
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=140c Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```
And the current layout of my settings:
```

"Mobile Broadband" Tab
[INDENT]Basic:[INDENT]Number: *99#
Username: <blank>
Password: <blank>[/INDENT]
Advanced:[INDENT]APN: yesbusiness
Network ID: <blank>
Type: Any
Allow roaming if home network is not available: <checked>
PIN: <blank>
[/INDENT]
[/INDENT]
"PPP Settings" Tab
[INDENT]Authentication:[INDENT]Allowed methods: EAP,PAP,CHAP,MSCHAPv2,MSCHAP[/INDENT]
Compression:[INDENT]Use point-to-point encryption (MPPE): <unchecked>
Allow BSD data compression: <checked>
Allow Deflate data compression: <checked>
Use TCP header compression: <checked>[/INDENT]
Echo:[INDENT]Send PPP echo packets: <unchecked>[/INDENT]
[/INDENT]
"IPv4 Settings" Tab:
[INDENT][INDENT]Method: Automatic (PPP)[/INDENT][/INDENT]

```
I'm a little adverse to following the guide by [*[COLOR="DarkOrange"]_alexfish_[/COLOR]*]("http://ubuntuforums.org/showthread.php?t=1466490"); as I don't want to risk changing settings on the modem itself.
Any help would be greatly appreciated! :)

---

### Post by Akavashi on 2010-11-16
And not even kidding, 7 minutes after posting... Restarted for the 10th time, and it started working.

Still using the current settings as above, which makes me wonder if the roaming setting is playing me around (or my silly regional Optus connection). And network manager is reporting the connection as: "Optus connection (YES OPTUS HSPA)" which should be right, hopefully.

---

### Post by gamar on 2011-02-22
Hey guys, not exactly the same issue and not exactly a question, but somewhat relevant.

I have pre-paid 3G internet, which I always had trouble to use with earlier versions of Ubuntu (9.10).
I am currently running the live CD of U 10.10  and initially I had same old troubles to connect. I looked at the log and this is what I got:

Feb 22 09:16:41 ubuntu NetworkManager[2887]: <warn> GSM connection failed: (32) Roaming is not allowed.

As I didn't have anything to loose, I checked this option in the settings and miraculously I am now on-line and I am able to post this. However I am a bit worried what kind of roaming does it use and I can't find more details about this option.

It's important to mention that I use virtual provider (bob.at), who is using the physical network of other provider (A1). I guess this is what in my case has been interpreted as roaming, but I don't want to end up with using 'real' roaming. So if anyone has clear idea how this roaming and virtual providers work, please share with us.

My system in the moment: Thinkpad x200 with built in 3G modem, Ubuntu 10.10 live

---

