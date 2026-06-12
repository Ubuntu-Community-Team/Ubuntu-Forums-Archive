---
title: "Sip/ voip"
date: 2010-01-20
forum: Multimedia Software
---

### Post by Bunro on 2010-01-20
I would like to have a working SIP/VOIP client on my Ubuntu 9.10 (64 bits) version.
 I would like to us it for video calling with my brother that is living in the USA. He is using a Apple computer. If you could help out witch software he should install on his Apple, that would be great!
 

 I installed Empathy 2.28.1.1  
 
[LIST]
[*]I can call out to a     land line;
[*]The software reacts     to a incoming call > But I can not answer the call;
[*]I can not add     contacts connected to the SIP account;
[/LIST]
 

 I also trying Ekiga ekiga 3.2.5.
 I tried to use my voipbuster account and I created a new Ekiga.net account.
 
[LIST]
[*]Voipbuster account     having the following problem
[LIST]
[*]Could not register         (Internal server error)
[/LIST]
     
[*]Ekiga.net account     having the follwing problem
[LIST]
[*]Could not register         (Forbidden)
[/LIST]
 
[/LIST]
 

 Hopefully there is someone that can help me out?
 

 Regards, Robert

---

### Post by adampaetznick on 2010-04-25
Similar problem with Ekiga 3.2.5 here.  Registered with ekiga.net but when I attempt to connect I get: Could not register (Forbidden).

---

### Post by stani on 2010-05-21
> **Bunro said:**
> I would like to have a working SIP/VOIP client on my Ubuntu 9.10 (64 bits) version.
 I would like to us it for video calling with my brother that is living in the USA. He is using a Apple computer. If you could help out witch software he should install on his Apple, that would be great!
 

 I installed Empathy 2.28.1.1  
 
[LIST]
[*]I can call out to a     land line;
[*]The software reacts     to a incoming call > But I can not answer the call;
[*]I can not add     contacts connected to the SIP account;
[/LIST]
 

 I also trying Ekiga ekiga 3.2.5.
 I tried to use my voipbuster account and I created a new Ekiga.net account.
 
[LIST]
[*]Voipbuster account     having the following problem
[LIST]
[*]Could not register         (Internal server error)
[/LIST]
     
[*]Ekiga.net account     having the follwing problem
[LIST]
[*]Could not register         (Forbidden)
[/LIST]
 
[/LIST]
 

 Hopefully there is someone that can help me out?
 

 Regards, Robert
Can you describe the parameters for Empathy and Voipbuster?

---

### Post by YannBuntu on 2010-07-05
hello

To do voice/video calls with Mac interlocutors, try either :
- [Ekiga with its PPA]("http://wiki.ekiga.org/index.php/HowTo_install_Ekiga_packages#Ubuntu") ; according to [Ekiga's interoperability table]("http://wiki.ekiga.org/index.php/Ekiga_Interoperability#Mac_OS"), your MacOS interlocutor should use [Xmeeting]("http://xmeeting.sourceforge.net/")
- Empathy (with [Telepathy PPA]("https://launchpad.net/~telepathy/+archive/ppa"), and ubuntu-restricted-extras package, and of course a Jabber account e.g. gmail address), that can do voice&video calls with MacOS [Gtalk]("http://www.google.com/chat/video") interlocutors
- Skype (which exists also on MacOS), but this one is not open-source

---

