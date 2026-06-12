---
title: "Adsl error codes ????"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2010-07-12
Hi, 

Is there a way to get adsl error codes in Ubuntu to troubleshoot adsl connectivity issues ?

Although it happens very rarely, sometimes I experience problem connecting to the internet.

I use a D-Link 802C modem.

Until a few days back I was using the modem in pppoe mode (with its inbuilt dialer configured). But then suddenly the modem was unable to establish a internet connection. At first I thought it was because of some maintenance work at the ISP end but when whole week passed I called up my ISP's helpline.

After hearing my problem the ISP guy straight away asked me "Tell me the error code"

He definitely must have assumed that

(a) I was using windows (Which is not the case)

                      & 
(b) I am using my modem in bridged-mode & using the OS's dialer (Which was not the case either)

After knowing my conf he clearly said "without the error codes I can't do anything"

So I borrowed my neighbor's laptop (xp installed) , configured my modem in bridged mode & after dialing from the laptop received an error code

"error 678 The remote computer did not respond"

Then it took only a few hours for my ISP to fix it.

But the problem is, suppose in future if this happens again is there a way I can get the error codes using Ubuntu?

Please help.

---

### Post by wookieshaver on 2010-07-12
The d-link adsl modem you mention does have an internal log for errors on the admin tab. However, you could install wine, download and install a windows pppoe client and install it there and have your errors that your isp needs. (of course leaving the modem in bridged)
 
Though it must be said, I did DSL and broadband support for 5 years at the local telecom company and those that need a windows error code to troubleshoot authentication should not be doing support!

---

### Post by linuxyogi on 2010-07-12
> **wookieshaver said:**
> The d-link adsl modem you mention does have an internal log for errors on the admin tab. However, you could install wine, download and install a windows pppoe client and install it there and have your errors that your isp needs. (of course leaving the modem in bridged)
 

Thanks for your reply. 

I actually told the ISP what was written on the modem's log. It was something like "ppp name not intact" or similar but he was not familiar with it.

I can install wine & dial using windows pppoe client for diagnostics but is there no way to do this without installing wine ? I mean by increasing the verbosity level by dialing using the gnome-terminal or something ?
If there is no such way I will install wine.

I am hesitating to install wine because I am worried that viruses may  start to work. May be not that badly but still you know ........ !!!!
Ubuntu doesn't know what an .exe is. What a relief !!!  

Thanks a lot.

---

