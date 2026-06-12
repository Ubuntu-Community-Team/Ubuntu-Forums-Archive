---
title: "D-Link Router Randomly Reboots - measuring network connection"
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by RT236 on 2011-12-26
This might affect other D-Link models too.  This solution seems to work well.

I have  a D-Link DIR-655 router that recently started randomly rebooting.  My firmware is up to date, settings are OK and it's been in service OK about a year plus, it's not overheating.

I've read about this happening occasionally with other D-Link models too with not a lot of solutions found.

Logging into the router I sometimes was getting the message "The gateway is currently measuring your network connection."

I'm posting this here for greater visibility and credit goes to Yahoo Answers Canada and dslreports.com  [http://ca.answers.yahoo.com/question/index?qid=20081221171135AAaxwco](http://ca.answers.yahoo.com/question/index?qid=20081221171135AAaxwco)

The problem is that the router (for some reason) is frequently checking your upload speed.

The solution is: 

In your router admin mode go to "advanced", "QOS" and uncheck "automatic upload check" and manualy enter your upload speed in the "manual loadup speed" box.  There is also a drop down menu where you can also select your typical upload speed.  

I did this and my router is now rock solid.  As I mentioned, this seems to affect several models and came on suddenly.  My ISP appears to have been tweaking their system so perhaps something has changed in their configuration that started my router rebooting a lot.

Long story short, I've seen this problem posted a number of time on Googling, but not many solutions.  This solution worked well for me and hopefully for others.:)

---

### Post by inobe on 2011-12-26
wow, this is a keeper, i may have to use this info some day.

thanks for posting.

---

### Post by ratibars on 2011-12-28
Great tip! Thanks.

---

