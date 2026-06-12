---
title: "No Email Since Router Has Been Installed?"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by TheNewbieGeek on 2010-06-19
Hi I hooked up router to tower and ever since I have not been able to get PeoplePC WebMail. I unplugged router and I still can't get the web mail. The customer support have stated web mail is down other reps say it is not. I get the internet. I have Ubuntu installed. Thanks for the replies.

---

### Post by jonobr on 2010-06-19
I dont know anything about PeoplePC WebMail

but I notice it has a login page.

Can you get to the website?
Can you login to the website?

If you cant test without having the router, how do you connect?

Given you can get to other websites, it sounds as if this is a provdor specific issue, however, theres not really a lot of information to go on here

---

### Post by TheNewbieGeek on 2010-06-19
I have uplugged the router and it still doesn't work. I can surf all over the internet etc. I can login but I can't access the page that has the email. It doesn't work on two computers one running windows. It has always worked.

---

### Post by jonobr on 2010-06-19
The forums dont charge you extra for supplying more details:-)open a terminal window and type in nslookup <url>
Im guessing it will be webmail.peoplepc.com
see what you get back.
If you get back the ip address of the website, then try 
to ping the ip address and then the url,
if all those work, put the ip address in the web broswer

the ip address I got for this service was 207.69.130.57

you should see what you get.
Given the cross platform nature of the problem, I figure the issue is your ISP DNS not giving you back the right IP address

---

