---
title: "Fax server solution"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by rebz7 on 2009-06-17
I am currently looking into setting up a **[COLOR=#ff0000]Fax[/COLOR]** **[COLOR=#ff0000]Server[/COLOR]** Solution.

Can anyone give me some pointers on what are pro's and con's of installing a **[COLOR=#ff0000]Fax[/COLOR]** intelligent board or a full FoIP / software solution?

regards,

---

### Post by jonobr on 2009-06-17
Hello


Routing through synaptic there seems to be a package the could do this,
its called 
hylafax-server

and there are also clients available to connect to the server.

One thing I do notice is that the package does not mention that it supports class 3 fax, but supporting class 2 means the other end should negotiate down.

Doing a quick google, I also found this quick howto......
[Here]("http://www.howtoforge.com/linux_hylafax_server")

---

### Post by arama on 2009-06-18
Dear All,

There is no need to install a fax server in order to [send fax]("http://en.popfax.com/Send%20fax%20subs.html"). All you need is to find an Internet [fax service]("http://en.popfax.com/Fax%20service%20tariffs.html") provider and start send and receive fax on your virtual [fax number]("http://en.popfax.com/Fax%20number%20subs.html"). If you have more questions I will be glad to answer.

> **jonobr said:**
> Hello


Routing through synaptic there seems to be a package the could do this,
its called 
hylafax-server

and there are also clients available to connect to the server.

One thing I do notice is that the package does not mention that it supports class 3 fax, but supporting class 2 means the other end should negotiate down.

Doing a quick google, I also found this quick howto......
[Here]("http://www.howtoforge.com/linux_hylafax_server")

---

### Post by jonobr on 2009-06-18
Hello

I think its rebz7's requirements that need to be claified.
If he is ok with not controlling this and signing up to a service then that would work,
However, As I understand his post, he wants to control the setup himself and not have an external provider do it.

You could also use something like efax which I think has a package in synaptic which would allow integration with an existing fax providor

Cheers

---

### Post by rebz7 on 2009-06-22
This is going support around 400 users and will be replacing 35 stand alone analogue fax machines.

---

### Post by jonobr on 2009-06-22
Hello

So the question then posed by arama is a valid one, although it was not asked directly.

Its the maths of the thing, and you going to have to assess what makes best sense for you....

Your time, effort and cost to create your own fax server in the company (in which case you can control everything yourself)

Versus interfacing to a public IP fax solution such as efax...
With efax, 

Some of the pros and cons of using your own fax server are, (just off the top of my head)
Pro-
1- you control the whole thing and you are administering everything
2- Not dependent on a remote third party company
3- Company policy may be able to be adhered to better with a fax server in your location instead of people sending whatever they want to numbers they want with you having no access or insight to it.
4- No payments to an external company for heavy fax usage.

Cons

1- see points 1 and 2 above
2- No costs to maintain analog phone lines
3- Your the support center for this
4- Your time to install it, judging from responses, not a lot of people have done this....

---

### Post by penguin30 on 2009-06-23
Hello,

I am trying to do the exact same thing as described in this post.  I would like to make a scalable solution where I can add fax numbers so something like efax would probably not suffice.  Can you please continue to update this forum with any developments?  I will do the same.

Thanks

---

### Post by penguin30 on 2009-06-29
I just wanted to follow up on this thread for anyone who has a similar situation in the future.  I am going with Gafachi.com.  They provide a service/hardware to do PSTN to IP with T.38 protocol.  This is much cheaper for me than setting up my own VOIP hardware and it gives me more control than something like e-fax.  Anyways, hope this helps someone.

---

### Post by jonobr on 2009-06-29
Hello


I would be careful of using T38,

there are vendors who support this, but a whole heap more that dont.
I have worked with this protocol a lot and can tell you its one of those things where even both sides may be talking the same language, but just dont work.....

---

### Post by rebz7 on 2009-06-30
The abilty to administate everything is the main drive and providing the function to send and recieve faxes directly from the users inbox (outlook 2007). Also to manage all documents sent on a central location. Does anyone recommend and software Foip solutions for this ?

---

### Post by arama on 2009-11-24
I advice you to subscribe to Internet fax [service]("http://en.popfax.com/Fax%20service%20tariffs.html"). They provide an option in order to send/receive faxes directly from your email account. You can [send fax]("http://en.popfax.com/Send%20fax%20subs.html") or manage all faxes while accessing your mail.

---

### Post by arama on 2010-01-15
With Internet [fax service]("http://en.popfax.com/Fax%20service%20tariffs.html") you can find you faxes on your computer by doing search by a simple word which is included in the fax. This is very useful as no need to have paper stocks on your table which might get lost.

Text recognition is now done for free in all the faxes you receive via Popfax.com - [fax to email]("http://en.popfax.com/Fax%20to%20email%20faq.html").

---

### Post by nida520 on 2010-07-08
Dear  following are my suggestion hope to help you.
 
old fax machin are out of time.now there exist  three kinds of  fax solution to instead of  fax machina.
 
1. fax software 
 
2. fax service
 
3.fax server 
 
fax software's disadvange is you need run a pc always.software is not steay ,if your pc is down due to some reasons like power off ,got vius ... your fax software will be strike at the same time.some times lead you lose some import document.
 
fax service is will be pay as you go and no need initial cost like fax software and fax server.but your all the incoming fax and out going fax will be monitor by your fax service provider.your risk is you may leak  you info to your competitors.
 
fax server will be good choose work independently, no need a pc always open there.your faxes will be all in your monitor.but you may cost at initial.there existing
some fax serve specail for small to middle office which will be affordable.with price 
around 500 usd.economical and practical.
 
above Personal opinion is for reference only.

---

### Post by epsolon77 on 2010-08-27
Ok I know this message is old, but I have been using hylafax to run faxing for a little over a year now.  What it really comes down to is how you are connected to the PSTN.  Internet links do not work well unless you can introduce QOS and jitter buffers.  That being said, I highly recommend the Hylafax solution.  I also really highly recommend pairing it with something like Asterisk, or any other IAX compatible phone system, even if it is just as a front end.  Do not have your system routing through a SIP or VOIP connection to the PSTN, it will not work well.

---

