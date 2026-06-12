---
title: "Public wifi with no encryption - redirect defeats Firefox"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by keithpeter on 2011-10-10
Hello All

I'm sitting in a major public building in Birmingham which provides free wifi. There is no encryption at all on the connection. Xubuntu (and other Linuxes) will connect to the network ok, and show the connection speed &c in the indicator applet.

When you start a web browser, the wifi system redirects the browser to a 'terms and conditions' page where you click to say that you understand the connection is not secure &c.

None of the Linuxes I have tried can make it through the connection redirect. Firefox comes up with a 'page disconnected while loading' error.

I'm typing this on Firefox 7 on Windows 7, which, needless to say, follows the redirect straight away.

Below is the url of the redirect...

```
https://securelogin.arubanetworks.com/upload/custom/cp_ICC_FREE/default.htm?cmd=login&mac=FF:FF:FF:FF:FF:FF&ip=10.100.254.150&essid=The%20ICC&url=http%3A%2F%2Fpinboard%2Ein%2Fu%3Akeithpeter
```

The one below is redirecting from a request for my links page which I use as the browser home page, and it includes the mac address of the laptop (shown as a stack of FFs here).

Anyone any experience on how to navigate around obstructions like this?

EDIT: a local arts centre has a redirect page that works through a local web address  [http://2.2.2.2](http://2.2.2.2) and Firefox copes with that easily.

---

### Post by newbie-user on 2011-10-11
Maybe try changing your user agent settings in firefox to match the settings for firefox on windows.

---

### Post by wildmanne39 on 2011-10-11
Hi, the only thing I can suggest is do you have firefox set to reject redirects? with noscript or adblock plus or something like that.
Thank you

---

### Post by keithpeter on 2011-10-11
Hello All

@newbie-user: yup, I'm thinking along those lines and googling how to change user strings

@wildmanne39: stock xubuntu as downloaded - booted off cd in the thinkpad which is a windows machine, so I don't think there is any adblock/redirect prevention. Also looked at time out settings on dns lookup.

Thanks chaps. This used to work fine until about a month or so ago. Suspect they have just changed some setting.

---

### Post by sammiev on 2011-10-11
I would use a free VPN site in those areas. :)

---

### Post by keithpeter on 2011-10-11
> **sammiev said:**
> I would use a free VPN site in those areas. :)

Thanks sammiev

I'll research those but I would rather just get the functionality back that we had a month ago! Suspect someone 'improved' the landing page.

---

### Post by keithpeter on 2011-10-14
Hello All

Browser string makes no difference. I'll be taking a windows laptop, an Ubuntu netbook down on Sunday with the aim of finding out what is going on. I've also installed chromium and opera on the netbook.

Does anyone know of any configuration differences between firefox on windows and linux?

---

