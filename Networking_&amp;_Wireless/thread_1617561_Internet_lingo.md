---
title: "Internet lingo"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by KegHead on 2010-11-09
Hi!

I recently contacted a company called jostens. I saw at the bottom of the email the attached:

Server [www.jostens.com/Email.asp](www.jostens.com/Email.asp) Port 80
Browser Name: Netscape
Browser Version: 5.0 (X11; U; Linux i686; en-US) AppleWebKit/533.4 (KHTML,
like Gecko) Chrome/5.0.375.70 Safari/533.4
Browser UserAgent: Mozilla/5.0 (X11; U; Linux i686; en-US)
AppleWebKit/533.4 (KHTML, like Gecko) Chrome/5.0.375.70 Safari/533.4
Cookies Enabled: True
JavaScript Version: undefined

Any idea what all this means?

KegHead

---

### Post by CharlesA on 2010-11-09
That's different. It looks like it grabbed some info about yer browser probably by using javascript (?)

See here: [http://www.javascriptkit.com/javatutors/navigator.shtml](http://www.javascriptkit.com/javatutors/navigator.shtml)

---

### Post by KegHead on 2010-11-09
Hi!

I was wondering if they captured some info about me and sent it to who ever!

KegHead

---

### Post by CharlesA on 2010-11-09
It's nothing personally identifiable. Just what browser you are using and what OS.

I am just puzzled why they would collect that info in the first place, maybe if the problem is a technical issue?

---

### Post by KegHead on 2010-11-09
Hi!

Not a tech issue that I'm aware of.

It's interesting that they identified linux, crome etc.

KegHead

---

### Post by chili555 on 2010-11-09
As far as I know, this information is available to every website you visit. Some sites will reject your visit based on your user agent data because they don't wish to support Linux. Here is some more information.

[https://help.ubuntu.com/community/TurboTaxOnline](https://help.ubuntu.com/community/TurboTaxOnline)> that website is now checking the user agent string reported by Firefox to specifically exclude Linux users.

Modifying Firefox's User Agent String

Fortunately, it is trivial to change the user agent string in Firefox and step around this disappointing exclusion.

   1.  Point Firefox to the special url: about:config
   2.  Filter on the string useragent
   3.  Change the value of general.useragent.vendor from Ubuntu to Windows
   4.  Change the value of general.useragent.vendor from gutsy to Windows NT 5.1I don't believe the information is personally identifiable; it just says somebody visited using Mozilla and Linux. That's not even strictly true, I suspect you actually visited using Firefox.

---

### Post by KegHead on 2010-11-09
Hi!

Good hearing from you again chili555!

I did use crome!

KegHead

---

