---
title: "Flash playing only on selected sites"
date: 2009-09-21
forum: Multimedia Software
---

### Post by tdmoore on 2009-09-21
Using Jaunty 9.04, dual boot with Windows XP.

Flash plays on selected sites including the Adobe site, however have found a site that worked in Windows but not Ubuntu.

If someone can try this and let me know if it's my install or the site itself, I would appreciate it.

[http://www.allstream.com/iptrunking_customer_demo/index.html](http://www.allstream.com/iptrunking_customer_demo/index.html)

If my install, any suggestions on how to fix the issue would be appreciated.  I did install Adobe Flash 10.

Thanks!

---

### Post by tkoco on 2009-09-22
The website is MS IE oriented. You can not get Ubuntu to ever display the flash. When I looked at the source code of the page, the javascript looks for a "Visual Basic script" called "detect.vbs". Of course, FireFox fails to load that file and causes the page to display the error message that you see. Write the webmaster and let him know that his product is not reaching all the possible clients!
> **tdmoore said:**
> Using Jaunty 9.04, dual boot with Windows XP.

Flash plays on selected sites including the Adobe site, however have found a site that worked in Windows but not Ubuntu.

If someone can try this and let me know if it's my install or the site itself, I would appreciate it.

[http://www.allstream.com/iptrunking_customer_demo/index.html](http://www.allstream.com/iptrunking_customer_demo/index.html)

If my install, any suggestions on how to fix the issue would be appreciated.  I did install Adobe Flash 10.

Thanks!

---

### Post by mayooresan on 2009-09-22
I have kind of similar issue. I can play YouTube and no issues but when I play flash games it doesn’t load at all.

One of my friends recommends me to try it on Opera 10 and I did. Opera plays most of the flash contents without problem but the mouse pointer fails to point where we point.

For example If I click on a button in the flash screen it won’t happen but instead it’ll click on some other control on the flash screen as pointer is pointing to some other place. It is so annoying. Is there any work around?

Some say if I uninstall the open source flash player and install official flash player it might work but how to do it?

---

### Post by tdmoore on 2009-09-22
Thanks tkoco...it is as I suspected.

Will definitely advise their webmaster.  You would think that they would recognize this and build their site for this!

---

### Post by mayooresan on 2009-09-22
> **tdmoore said:**
> Thanks tkoco...it is as I suspected.

Will definitely advise their webmaster.  You would think that they would recognize this and build their site for this!

sure, good chance that they'll consider as even in windows most of us are using Firefox.

VB Script will not work in any browser other than useless IE, which never adhere to the web standards.

---

