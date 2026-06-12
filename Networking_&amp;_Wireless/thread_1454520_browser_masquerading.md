---
title: "browser masquerading"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by conradin on 2010-04-14
I have an online Class that requires I log into a session saying I attended the class. There is some other software they make you run to view the content, but I can get that to run in wine. The problem I have is the Sever that controls logins only accepts OSes win 2000 or later, or OSX 10.4 or later. (No Iphone support either). Once I log in and authenticate, Then I can run this software. 

I don't want to have to go to the doze just so I can log in. I tried informing the admins that my OS has nothing to do with web content.

All I want to do is change my browser user agent strings to something that says I have an acceptable OS so I can log in. I'm willing to use any browser to do this.

---

### Post by conradin on 2010-04-14
in Firefox: There is the about:config
which looks promising. I cant login until tues /thurs which will be when I test this. What options should I modify in about:config to ensure my bratty college thinks I'm using windows to access their server?

---

### Post by chili555 on 2010-04-14
Search about:config for useragent. Then you can change vendor, vendorComment and vendorSub according to these guidelines: [https://developer.mozilla.org/User_Agent_Strings_Reference](https://developer.mozilla.org/User_Agent_Strings_Reference)

I changed my useragent to do my taxes on line and it went smoothly.

---

