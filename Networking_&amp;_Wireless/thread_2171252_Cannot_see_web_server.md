---
title: "Cannot see web server"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by Peter_Sotos on 2013-08-29
Hello there!

I can see my web server on my local network and even see the default apache web page, but no one can see it from the outside. I am running a Apple Base Station and I configured port 80 to point to my web server via port mapping. In any case when I try to browse from the outside to my public IP I get a 502 Bad gateway response. 

Any ideas what I could be doing wrong? The firewall has no rules in it so it shouldnt be the problem. Anyway, lost as to why this isnt working. I am running Ubuntu 12.04.3. Im pretty sure its some kind of port routing issue.

Peter

---

### Post by dhunt84971 on 2013-08-29
Hello Peter -

Just a quick Google on the 502 Error and I found this page that seemed to offer quite a few options:

[http://pcsupport.about.com/od/findbyerrormessage/a/502error.htm](http://pcsupport.about.com/od/findbyerrormessage/a/502error.htm)

Hope this helps.  Just out of curiosity, who is your ISP?  I am using Comcast and have had pretty good success configuring my own website, but I have heard of people with Verizon having difficulties getting an actual public IP.

Good luck!

---

### Post by Peter_Sotos on 2013-08-29
My provider spent a long time and some deep thought coming up with their name: Cox. Anyway, its still not working. I am out of ideas and now suspect that my ISP is the culprit.

---

### Post by Peter_Sotos on 2013-08-29
I'm screwed. :(

[http://ww2.cox.com/residential/orangecounty/support/internet/article.cox?articleId=cacf82f0-6407-11df-ccef-000000000000](http://ww2.cox.com/residential/orangecounty/support/internet/article.cox?articleId=cacf82f0-6407-11df-ccef-000000000000)

Any ideas for options without having to pay enormous hosting fees? Could I run my webserver on a different port and just have my employees use the port number? I noticed that 8080 isnt blocked.

---

### Post by Peter_Sotos on 2013-08-29
oops! JBoss is running on 8080! ok what about using a weird port number? Any ideas?

-------------
Sadly I just found out that this is NOT an option. They also block port 25! SMTP! :(
-------------
Bye bye COX I am switching ISPs!
-------------
Trying Centurylink now.... I'm checking if they block ports.

---

### Post by dhunt84971 on 2013-08-29
I suppose technically any port will do (I would keep it in the high range), but I did see that 8090 seems to have the same usage as 8080.

Perhaps someone else can recommend a good alternative port.

---

### Post by Peter_Sotos on 2013-08-29
Ok here is my solution:
Add a second ISP! :P

Century link has download limits. Very bad for me because I download a LOT. Movies from itunes, software installs for work, etc.. BUT they DO NOT block ports. So I am going to order their CHEAP, and it is CHEAP compared to Cox, internet service and get myself a static IP. Problem solved. (This is all way cheaper than paying for Virtual Private Hosting).

My website is going to be using sendmail, JBoss, Apache, but its going to only have about 15-20 of my employees on it at any time so I should be golden.

---

### Post by SeijiSensei on 2013-08-30
A much better solution might be to rent a virtual server from a company like [Linode]("http://www.linode.com/").  For $20/month you could have a server in the cloud with a public IP address that you can manage yourself.  That is certainly a lot cheaper than upgrading to a business-class Internet connection or adding a second provider.  I have two Linodes, one on each coast for redundancy.  I maintain a local server in my office that connects to the cloud servers over an OpenVPN tunnel.

---

### Post by Peter_Sotos on 2013-08-30
Ah yes for sure. Didn't know you could get it that cheap. No extra hidden bandwidth or whatever fees? If so, I think I will go with your option.

Thanks for the advide Seijisan!

---

### Post by SeijiSensei on 2013-08-30
You get a huge pipe to the Internet, big honking generators for backup power, and for a few bucks a month, daily snapshot backups of the VM.  The default traffic maximum is 2 terabytes/month.  Plus they just doubled the memory and disk space allocation for those of us on older plans for free.  I've been able to bring up and take down a VM the same day and pay nothing for it.  They have excellent, responsive customer service with competent techs.  Plus you can place the VM in any of a number of facilities including London and Tokyo.  I use Newark and Fremont, CA.

Disk space is a bit expensive, but since they doubled the size of the machines it hasn't been an issue any longer for me.

You could say I'm a Linode fanboy.  I wish they were a public company; I'd buy their stock.

---

### Post by Peter_Sotos on 2013-08-30
Yeah sounds amazing and it's what I am going to do. I guess I was geeking out trying to turn my house into a datacenter. :P

I'm not sorry for buying my new linux box though. I am just going to use it as a Phase 1 SIT platform, then move to a temp box at Linode for Phase 2 SIT/Performance. and when all those pass, move it to my permanent node at Linode. Seriously, $20/month is a flippin steal!!

*bow to Seijisan*

---

