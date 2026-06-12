---
title: "How to connect to CISCO Anyconnect SSL VPN?"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by ygleung on 2009-11-12
I''ve tried to wine Internet Explorer, but can not launch the VPN application.

It looks there is client package for Linux, can anybody provide it? Or any other solution?

---

### Post by casevh on 2009-11-13
(I'm assuming you need to connect to a web page and then  download/automatically install the AnyConnect client.)

If you can connect to the web page, but just can't install AnyConnect, you probably don't have the Sun Java web plugin installed. It must be the "Sun" JRE.

You should alos be able to get the standalone AnyConnect client from whomever administers the remote access server.

If you are using 32-bit Ubuntu 9.04 or 9.10, that should work. If you are using 64-bit Ubuntu, you need to install some packages.

If this doesn't help, can you describe exactly the steps you're doing.

casevh

---

### Post by ygleung on 2009-11-13
Thanks for the reply.

Actually I've installed IE7 and JRE on Crossover Pro 8 (with a Winxp bottle). Yes I can open the web page and login, after I clicked on the Anyconnect button, it told me *failed to launch the client*.

I don't think the adminstrator is willing to help me out, coz I think I'm the only Ubuntu user in my company. I've tried to download the client package from CISCO.com, but it looks I can't download it as a normal registered user.

---

### Post by Yoann Juet on 2009-11-14
You can get the linux binary at the following url: 
[https://wiki.univ-nantes.fr/doku.php?id=nomade:document](https://wiki.univ-nantes.fr/doku.php?id=nomade:document)

On my side, it works fine under 9.04 and 9.10.

---

### Post by msbentley on 2009-12-13
I installed the standalone Cisco AnyConnect client, but found it to be a pretty poor piece of software. Then I discovered that there is an open source port called OpenConnect - [http://www.infradead.org/openconnect.html](http://www.infradead.org/openconnect.html).

You can just install the openconnect and network-manager-openconnect packages from the repositories (in Karmic at least).

This works very well for me, and integrates with NetworkManager etc.

---

### Post by DouglasAWh on 2010-02-04
> **msbentley said:**
> 
You can just install the openconnect and network-manager-openconnect packages from the repositories (in Karmic at least).

This works very well for me, and integrates with NetworkManager etc.

This didn't seem to work in Lucid.  Any thoughts?

---

### Post by dwmw2 on 2010-03-23
> **DouglasAWh said:**
> This didn't seem to work in Lucid.  Any thoughts?

Um, my crystal ball isn't working today. Can you perhaps tell us *how* it didn't work? Did it give you an error message when you tried it? Did it crash? Did a pixie jump out from under your desk and run away with your laptop?

If you provide this information in a mail to the [EMAIL="openconnect-devel@lists.infradead.org"]openconnect-devel@lists.infradead.org[/EMAIL] mailing list, we can try to help you.

---

### Post by DouglasAWh on 2010-03-23
> **dwmw2 said:**
> Um, my crystal ball isn't working today. Can you perhaps tell us *how* it didn't work? Did it give you an error message when you tried it? Did it crash? Did a pixie jump out from under your desk and run away with your laptop?

At the time, AnyConnect wasn't working, so I was looking at doing it through network-manager.  AnyConnect works now, so no biggie here.

At the time, I was asking about packages that would have changed that would have made this not work.  I could have gone digging through bug reports, I suppose, but I didn't.  I don't remember how it didn't work as that was ~two months ago.

---

### Post by dwmw2 on 2010-03-23
> **DouglasAWh said:**
> I don't remember how it didn't work as that was ~two months ago.

Thanks for the update. If you ever feel you want to switch to properly-supported Free Software without a history of root holes, and if you still have problems with it, please feel free to post your results to the mailing list (no need to go looking for existing bug reports), and we'll try to get you up and running.

---

### Post by DouglasAWh on 2010-03-23
> **dwmw2 said:**
> If you ever feel you want to switch to properly-supported Free Software without a history of root holes

As much as I would like that (and appreciate the offer for help), I am not a member of our networking team and our networking team guys (and thus our ~3500 employees) use AnyConnect.

Thems the breaks, I guess.

---

