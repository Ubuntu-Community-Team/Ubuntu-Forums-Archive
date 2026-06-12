---
title: "Firewall with 100% logging"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by stoneydk on 2010-01-23
I am trying to help a client of mine (A hotel in denmark) setting up a wireless network, and as there are a law in Denmark forcing the "provider" of the wireless network to log all traffic to and from the computers that attach to the internet, I am trying to make the following:

1. Setup an Ubuntu Firewall (Proxy?) - that makes a COMPLETE log of all the traffic, including the MAC address of the client PC

Is this possible ?

(Would like it if it also could be put in a daily compressed file with a password)

Regards

Stoney

---

### Post by Lars Noodén on 2010-01-23
It sounds like rather a waste of time.  However, it can be done easily with iptables, if that is your gateway, or a sniffer like snort or kismet.  

However, what is meant by %100, each packet in each stream of data?

Please provide a link or citation to the alleged law and the relevant section.

---

### Post by stoneydk on 2010-01-23
Oh, this is a PDF file in 38 pages, and in danish - and even with a lot of it in "law paragraphs" :)

I am not  allowed to put this file up here, but short said it says "the hotel is to log the users MAC, and what the user communicates to / from the internet" - this data is to be kept safe for 1 year, after that it shall be deleted"

So to be sure they logged "enough", I just wanted to log everything, there is nothing in the PDF as to in what format to keep it, just that i should be kept for this year.

Today they use a program called "Firstspot" - but this makes a proxy, and not that stable is they would like it to be..

So I am trying if I can make a different offer for them, but has to be stable :)

---

### Post by Lars Noodén on 2010-01-25
> **stoneydk said:**
> Oh, this is a PDF file in 38 pages, and in danish - and even with a lot of it in "law paragraphs" :)

I am not  allowed to put this file up here...

Then please provide a URL to where it is posted or to where it is allowed to put it up.  It didn't used to be the case that Denmark had secret laws, so there should be a link already in existence even if it's to a scanned paper copy.  

The reason for asking is to see exactly what is required.

---

### Post by stoneydk on 2010-01-25
Been trying to search if it is online, but can't find it anywhere. (I got by email from the owner, who got the copy on email from a lawyer company)

Never mind, I am pretty sure you can't understand any of it anyways (You are french?) - And I can't find a way to send private messages in this forum to you ?

So I am just gonna mess around with IPtables some day, to see if I can get it to do what I want :)

---

### Post by Lars Noodén on 2010-01-25
> **stoneydk said:**
> Been trying to search if it is online, but can't find it anywhere

Then can you post the citation to that law, please?  

If it's a real law, then it has a name, a date it was put into effect.  There will also be a relevant chapter and section.  If you have that, please post it.

> **stoneydk said:**
> ... get it to do what I want :)

That's what I'm trying to find out.  ;)

---

### Post by stoneydk on 2010-01-26
Could you try and send me an email

contactstoney    gmail    com

Regards

Stoney

---

### Post by Lars Noodén on 2010-01-27
The hourly rates here are much lower ;) and others may benefit from the questions and answers.  

Snarfing *all* the traffic will certainly be in violation of EU and Danish privacy laws.  

How about at least humoring us with the name of the law?

---

### Post by stoneydk on 2010-01-27
I wanted your email address, so I could send it to you :)

---

### Post by stoneydk on 2010-01-27
Ohhh, now I found it...

the PDF I got is from a lawyer company, and marked as

"Strictly Confidential - Legal Privilege"

therefore i didnt wanna publish from it..

But I have read a little more specific in it, and found that it is just a clarification of the law, WHICH I have now fou[SIZE=2]nd (actua[/SIZE]lly a lot) of links to:

The Law it self:

[http://logningsdirektivet.dk/](http://logningsdirektivet.dk/)

Proparly the section[SIZE=1] "[/SIZE][FONT=Verdana][SIZE=2][SIZE=1]Artikel 5:  Kategorier af data, der skal lagres" is the one you are looking for.

When you see it (translate?) - you might agree with me, easier to just log EVERYTHING, and store it in a safe way..[/SIZE].
[/SIZE][/FONT]

---

### Post by Skaperen on 2010-01-28
We cannot make legal decisions about what you must log.  You are making that decision.  But saying 100% does not make sense.  That would mean to copy and store the entire contents of every packet.  Anything less is less than 100%.

I suggest you, as a contractor for the hotel, get in writing what they (their lawyer) says needs to be logged.  Ask that those terms not be confidential so you can tell others.  Then you need to determine how much data that is, figure out the resources needed, and provide them with a cost estimate.

---

### Post by Lars Noodén on 2010-01-29
> **stoneydk said:**
> 
The Law it self:

[http://logningsdirektivet.dk/](http://logningsdirektivet.dk/)


Thanks.  That was just the link I was looking for.

What I was thinking of was something like the *[**Directive 95/46/EC** of the European Parliament and of the Council of 24 October 1995 on the protection of individuals with regard to the processing of personal data and on the free movement of such data](http://eur-lex.europa.eu/LexUriServ/LexUriServ.do?uri=CELEX:31995L0046:EN:HTML)*, which is also [available in Danish](http://eur-lex.europa.eu/LexUriServ/LexUriServ.do?uri=CELEX:31995L0046:DA:HTML).  That sets the minimal standards so that the member states can then whine fiercely that the minimum is far to high or low.  In the case of the Nordic countries, the minimum is locally set much higher.  Here is one example of the [privacy law applied in Sweden](http://www.datainspektionen.se/lagar-och-regler/personuppgiftslagen/).  Denmark's will be different, but not UK- or USA- different.   

Copying and recording **all** packets will incur an enormous waste of resources in addition to probably violating most privacy laws. You will get a lot of clear text personal information in those logs, wanted or not.  

Copying and recording just the **start and end packets**, (SYN and FIN) of each TCP connection to other machines wouldn't be much better for privacy, and still an enormous storage requirements.

I guess it's your business.  It looks from here like it could be an 'injection attack' using a lawyer.  Anyone can hire one to send just about any kind of letter.  In some countries it's kind of like a sport to do so.

---

### Post by Lars Noodén on 2010-02-02
Here is a longer list of EU guidelines and legislation on personal data protection:

[http://eur-lex.europa.eu/en/dossier/dossier_02.htm](http://eur-lex.europa.eu/en/dossier/dossier_02.htm)

---

