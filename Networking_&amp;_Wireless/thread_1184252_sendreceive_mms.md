---
title: "send/receive mms"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by conandor on 2009-06-10
Want to ask how to configure mbuni to send/received MMS? I can send/received sms with kannel using huawei e220

how can i configure to send mms?

---

### Post by MaindotC on 2009-06-11
I'd never even heard of mbuni until now.  What precisely are you doing - setting up your own cellular network to send and receive MMS?

---

### Post by cariboo on 2009-06-11
Have a look at this [thread=396942]thread[/thread], it will help you receive mms streams.

---

### Post by MaindotC on 2009-06-11
I believe he's talking about [Multimedia Messaging Service](http://en.wikipedia.org/wiki/Multimedia_Messaging_Service) not Microsoft Media Server.

---

### Post by conandor on 2009-06-11
yes. i intend to simulate a mmsc to send/receive mms from the GSM modem using kannel and mbuni. does anyone ve make it work b4?

thx to verify strAlan. the mms i mean is Multimedia Messaging Service

---

### Post by MaindotC on 2009-06-11
I haven't gotten this working but it seems like a cool project I want to try out.  How far does your modem reach?  Don't the carriers in your area have bandwidth rights over that part of the frequency spectrum? How do you program the phones to work on your network?

---

### Post by conandor on 2009-06-11
> **strAlan said:**
> I haven't gotten this working but it seems like a cool project I want to try out.  How far does your modem reach?  Don't the carriers in your area have bandwidth rights over that part of the frequency spectrum? How do you program the phones to work on your network?

well, it doesnt work that complicated as u imagine.

the simplest example i can show is the SMS voting like in American Idol. whereby user will text to number (or voting system) and then the system will reply back casting the vote. this can be set by oneself at home easily with GSM modem with the telco service u ve with a program call kannel.

but now instead of sms, i wan the 'system' to able to send/receive mms

---

### Post by MaindotC on 2009-06-13
I don't really have any way to help you, but I'm going to keep asking questions if you don't mind.  So when you say "the system", you mean the GSM modem will be connected to a machine running mbuni and you can sms from a device running kannel?  I'm not sure about mms - but I can tell you this: when I send an MMS to a friend, it's usually a picture, some text, and a subject line.  My phone shows three outgoing messages, but it's all just one big message.  So, maybe you have to send the MMS as separate parts, and then just have mbuni reformat them in an MMS format.  I know that's very little detail and very broad, but if that doesn't help put it in persepctive then I hope the mbuni or kannel community can help you figure out this issue.

---

### Post by conandor on 2009-06-14
> **strAlan said:**
> I don't really have any way to help you, but I'm going to keep asking questions if you don't mind.  So when you say "the system", you mean the GSM modem will be connected to a machine running mbuni and you can sms from a device running kannel?  I'm not sure about mms - but I can tell you this: when I send an MMS to a friend, it's usually a picture, some text, and a subject line.  My phone shows three outgoing messages, but it's all just one big message.  So, maybe you have to send the MMS as separate parts, and then just have mbuni reformat them in an MMS format.  I know that's very little detail and very broad, but if that doesn't help put it in persepctive then I hope the mbuni or kannel community can help you figure out this issue.

Yes, the system i mean is what u mention.

Basically what i know is when u send a MMS, the message (picture, text, link) will be send to the MMS-Center. And a wap-push will be send to recipient to trigger to retrieve the message from the MMSC. If the receipient's phone does not support MMS, he will instead receiving a SMS notification to check his MMS on web. However, this is telco-dependent.

I do certainly hope mbuni and kannel community will help but it seems that I got more response in Ubuntu community than those two.

Kudos to Ubuntu community! ;)

---

### Post by MaindotC on 2009-06-16
> **conandor said:**
> 
I do certainly hope mbuni and kannel community will help but it seems that I got more response in Ubuntu community than those two.

Kudos to Ubuntu community! ;)

Do they have an IRC channel or a mailing list?

---

### Post by conandor on 2009-06-16
> **strAlan said:**
> Do they have an IRC channel or a mailing list?

no. i dun think they ve IRC channel
still awaiting response from their mailing list~

---

### Post by juky on 2010-02-01
Anyone managed to install and use mbuni/kannel in ubuntu?

---

### Post by MaindotC on 2010-02-01
I'm not an expert on these two applications but I've just taken a look at the source code and I installed the packages of kannel and mbuni per their respective deb files.  Kannel was in the repositories, and mbuni provides a deb package.  I haven't gotten into the configuration yet but I'm reading the introduction about MMS and what you need in order for an MMS to be transmitted and received.  If it just comes down to installation and operation I should be able to help.  Where are you having difficulty?

---

### Post by juky on 2010-02-01
@strAlan:

Basically, I would just like to install those two on Ubuntu box; OK, since Kannel was in repos, just a hint on how to install mbuni and its dependencies listed [Here](http://www.mbuni.org/userguide.shtml).

Thanks in advance!
juky

---

### Post by MaindotC on 2010-02-01
> **juky said:**
> @strAlan:
ust a hint on how to install mbuni and its dependencies listed [Here](http://www.mbuni.org/userguide.shtml).

Thanks in advance!
juky

I don't know what this means.  Do you need help following the user or installation guide for mbuni?

---

### Post by juky on 2010-02-01
Hi,

yes, help would be appreciated. Meaning, maybe line by line if it differs from the one specified in installation guide.

Also, once installed, how do you start the application? Over command line or from GUI?

Hope I explained it a bit better this time....

Thanks once more, 
juky

---

