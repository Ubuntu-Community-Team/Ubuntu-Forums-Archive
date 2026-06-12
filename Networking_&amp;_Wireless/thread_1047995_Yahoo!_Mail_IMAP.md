---
title: "Yahoo! Mail IMAP"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2009-01-23
Okay so apparrently Yahoo doesn't use IMAP even though it's better than pop. Yahoo claims only paid users can use POP, although I used to use if before I became a paid user.

But anyways, on my HTC Touch Windows Mobile phone when I setup my Yahoo email it automatically detected the settings and used the server "imap.mail.yahoo.com" and on phone and it works.

However, when I go on my PC and use the same settings it prompts me for my password and says the login failed.

Does Yahoo only allow IMAP access for mobile devices, I was googlgling and apparrently the iPhone also uses IMAP to access Yahoo mail.

If so is there a way to make Yahoo think my computer is a mobile device when I connect?

---

### Post by randytan on 2009-02-05
I'd like to know this as well.

I've already set up my Gmail's IMAP now if I can do it with at least my Yahoo! Mail, it'd be great. Doing so with hotmail as well would even be better! :p

---

### Post by RealG187 on 2009-02-10
IMAP works on my phone but not my computer....

---

### Post by pdtpatrick on 2009-02-10
I think the imap protocol only works for mobile mail but i know for sure when you are using your computer, it reverts to pop.mail.yahoo.com and you have to be a pro subscriber meaning you have to pay $19.99 for the year or so. However, I haven't paid them again since i last paid them and it's been working for 3 years.. unless they charged me and i didn't know haha.. darn them!

---

### Post by RealG187 on 2009-02-11
I pay for my Yahoo with my small business hosting. The funny thing is I thought Yahoo! didn't use IMAP, but then when I set it up on my phone, that's what it used. Is there a way I can trick it to think my computer is a phone?

---

### Post by pdtpatrick on 2009-02-11
I think now you are talking about messing with the TCP packets  .. don't know how you will fool their server to think you are a mobile device.

---

### Post by RealG187 on 2009-02-11
Maybe a proxy or something, or a program

---

### Post by RealG187 on 2009-03-31
Can someone please help me with this? I need to access my Yahoo! mail from thunderbird.

If i must use Zimbra desktop, can I use it in Ubuntu and can I use it to save my messages to .eml files so I can delete them from my account and keep them on my hard drive?

---

### Post by kf6emm on 2009-05-05
Apparently, Yahoo mobile IMAP email will only work if you are coming through a mobile IP space. Earlier today I tethered my phone to my laptop, using the phone as my internet connection and set up the yahoo IMAP server names in Evolution, and it worked. I am on Sprint so I don't know if that works with any other mobile provider.

I guess if there were some way to spoof your IP while on your land based ISP, it might work, but I don't have a clue on how to do that.

Here are the receive and send (IMAP and SMTP) server names:

imap.mail.yahoo.com (IMAP)
smtp.mobile.mail.yahoo.com (SMTP)

---

### Post by RealG187 on 2009-05-05
I think I can still connect from my phone when I am connected with Wifi.

---

### Post by RealG187 on 2009-10-29
I did it!

[http://www.crasseux.com/linux/](http://www.crasseux.com/linux/)

On that page is a modified thunderbird that connects to Yahoo! via IMAP!

[http://www.crasseux.com/linux/thunderbird_yahoo_imap_non_debug.tar.gz](http://www.crasseux.com/linux/thunderbird_yahoo_imap_non_debug.tar.gz)

I ran the file /bin/thunderbird in there.

The problem is when I start thunderbird from the Applications menu and ALT+F2 and type it it runs my other thunderbird that doesn't work. When when I click mailto links [like this]("mailto:test@example.com") it doesn't work when when I click links in email messages (like topics notifications I get for forums like this) they don't open, I have to copy and paste them.

How do I make this modified thunderbird work like normal where it's more interactive with the OS, I am not sure sure if it would automatically check for new emails and use Ubuntu's notification system to inform me of new messages...

---

