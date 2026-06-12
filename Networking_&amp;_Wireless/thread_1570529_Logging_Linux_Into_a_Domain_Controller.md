---
title: "Logging Linux Into a Domain Controller"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by Dragonbite on 2010-09-08
Please bear with me, I am very new to Networks and Servers.

I see the steps outlined in HowToForge's [[COLOR="Blue"]_Using eBox As Windows Primary Domain Controller_[/COLOR]]("http://www.howtoforge.com/using-ebox-as-windows-primary-domain-controller") and may be trying it out but what I don't know is how do I make my desktop Linux clients log into the same controller?  

I am looking at this at 2 different angles; [LIST=1]
[*]Use for my home network so to make it easier to control the different users, permissions, tracking, etc.  This includes Linux (Ubuntu, Fedora and openSUSE), Windows XP (laptop) and Windowx 7 (desktop)
[*]Ease of use for somebody I know who is thinking it may be good for one of HIS clients, which likely is going to be a Windows-based network.
[/LIST]

Also, are there any special considerations to keep in mind in regards to the laptop logging in and the possibility of the laptop being started outside of the network where there is no access to this server (or, how do I make sure I can log into my laptop when not at home)?

Thank you.

---

### Post by MaindotC on 2010-09-08
I don't know about this eBox business, but there's a package you can install that provides easy logon of Linux clients to a winblows domain called [Likewise](http://www.likewise.com/).  Is that what you're looking for or did you want to setup a winblows domain controller with AD too?

---

### Post by Dragonbite on 2010-09-09
From the looks of it, the eBox component is a web-based interface for managing a headless server.  In this case, it is basically eBox running on top of Ubuntu 10.04 LTS.

I am not looking for connecting to Active Directory, but to hook into the Domain Controller running on Linux and don't know what the client side needs or needs to configure to know to look for it.

---

### Post by MaindotC on 2010-09-09
Ok I'm a little confused - when you say "hook into the DC running on Linux", do you mean the DC is running on Linux or do you mean "authenticate to a DC using a Linux client"?  And you said you're not looking to connect to AD, but are you trying to connect a Linux client to a DC and just not sure how to configure that client to do that?  And I'm assuming by the tutorial you posted that eBox is your DC?

---

### Post by Dragonbite on 2010-09-09
> **strAlan said:**
> Ok I'm a little confused - when you say "hook into the DC running on Linux", do you mean the DC is running on Linux or do you mean "authenticate to a DC using a Linux client"?  And you said you're not looking to connect to AD, but are you trying to connect a Linux client to a DC and just not sure how to configure that client to do that?  And I'm assuming by the tutorial you posted that eBox is your DC?

Sorry if I am confusing. Like I said, I am new to this and some of this is prompted by a guy who is looking into whether this can replace a Windows Server for somebody he knows.  So I am (mostly) out of my element, but willing to learn.


Ok, I think this is a fair summary of the situation [LIST]
[*]the DC is running on Linux, set up using the eBox tutorial from HowToForge.com.
[*]The tutorial includes how to set Windows (XP) to connect to the DC.
[*]How do I do the same thing with a Linux client? How do I connect a Linux client to the DC?
[*]There is no AD in the mix.
[/LIST]

If I am going at this bass-akwards, or there is a much better method please feel free to let me know.  I'm learning here and won't be surprised if I'm doing it totally "wrong" (or, "wierd").

Thanks for your patience.

---

### Post by MaindotC on 2010-09-09
It's ok - I gotcha now.  I don't know precisely how to do it other than using Likewise but it seems you need to edit smb.conf or use the "net" command.  This is what I googled [http://is.gd/f2Hdu](http://is.gd/f2Hdu) and a few results down is a UF post on how to join a Ubuntu client to a Samba DC.  I don't mean to be rude by telling you to google it but I just haven't done it that way before so hopefully I'm pointing you in the right direction.  Let me know if this works b/c I wouldn't mind doing this as well.

---

