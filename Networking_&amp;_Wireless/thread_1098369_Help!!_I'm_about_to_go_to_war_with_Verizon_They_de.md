---
title: "Help!! I'm about to go to war with Verizon They demand I use windows to &quot;install&quot; DSL"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by smacfarl on 2009-03-16
Hey,

Tech support of course claims, they don't support linux.

The new verizon router/modem forces a download of crapware and service agreement which magically requires windows and ie. WTF?

How do I deal with these people? What do I do to get around this crap?

This is a problem, as I build linux boxes for people, and I may not be in the same local to support them.

---

### Post by lisati on 2009-03-16
I know what you mean: the ISP I use has a "connection assistant" (to help troubleshoot connection problems) that you can download, which not only *requires* Windows but seems to prefer IE over whatever other browser you've set as default - don't you just hate websites and software which do that? And their PC health check complains about lack of antivirus when you have chosen something to install something other than their preferred one.

---

### Post by ugm6hr on 2009-03-17
> **smacfarl said:**
> How do I deal with these people? What do I do to get around this crap?

Buy your own decent router?

Or look into what the underlying Verizon hardware is and find a default manufacturer firmware (although this will likely invalidate warranty etc - you have been warned).

---

### Post by solitaire on 2009-03-17
As long as you have your "Username" and "Password" you can use any router you like!!
Hopefully Verizon is not like "SKY" Broadband in the UK that have the router generate your username and password via a program in the router and don't give you a record of the username and password!!!

---

### Post by smacfarl on 2009-03-17
No. No. It's far worse.

When you first turn on their supplied router/modem it forces you to a sight called activate.verizon.net, which then forces a downloand a whole bunch of windows/MacIntosh crapware and to click on various usage agreements. It will absolutely NOT proceed with this process unless you have an approved operating system and an approved browser.

You can't use broadband at all until you get past this "registration" process even if you already have an account with them. This is about as draconian as it gets. And I am calling out to the Ubuntu linux community to help me deal with this.

Clearly we are talking about EVERY new user to Verizon broadband requiring a windows system, or a Mac system. Is there anyway we can alert the brain trust of Ubuntu land to figure out what can be done?

---

### Post by OrangeCrate on 2009-03-17
^,

Frankly, it's a battle you're not going to win. I'd suggest looking at alternatives, unless you want to dual boot Windows, so you can hook up to Verizon.

(Besides, for 1 meg service, once the trail offer wears off, it's really expensive in comparison to other providers. At least it is here.)

---

### Post by sgosnell on 2009-03-17
I would never deal with Verizon by choice.  I'm doing it, though, because my brother-in-law moved to a place where they are the only available provider.  I haven't encountered the problem cited here because they haven't even got the phone line working, a week after it was supposed to be installed.  They just closed the work order, but the line is completely dead a the drop.  Still waiting for another technician to show up and fix it, for the third time.  It has not worked at all yet.  He has a Windows computer, so that's not a problem - I can't get him to change under any circumstances.  All he knows, and all he wants to know, is Windows, and he knows little or nothing of Windows.  So I get to do the work.  Oh well...

---

### Post by sedawk on 2009-03-17
This sound really strange. When connecting a PC to a DSL modem, such
software might be needed, but when using a DSL router (with built-in
DSL modem) you normal start the Web interface of the DSL router
to set USERNAME & PASSWORD and that is all. There is no reason
to touch the PC(s) if there is a DSL router involved.

Here are some possible solutions:

* If you have Username/Password pair test another DSL modem or 
  DSL router or a all-in-one-box.

* If IE6 is supported try this "IE on Linux" setup tool:
  [http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/)
  (runs special IE in special WINE environment).

* There might be some way to "fix" the OS and browser detection.
  E.g. with Firebug (Firefox plug-in) or other plug-ins.

---

### Post by netztier on 2009-03-17
> **sedawk said:**
> Here are some possible solutions:

* If you have Username/Password pair test another DSL modem or 
  DSL router or a all-in-one-box.

* If IE6 is supported try this "IE on Linux" setup tool:
  [http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/)
  (runs special IE in special WINE environment).

* There might be some way to "fix" the OS and browser detection.
  E.g. with Firebug (Firefox plug-in) or other plug-ins.

and another one: if you still have a *ahem* valid license for Win2k or XP, install **Virtualbox** (either OpenSource edition from the Ubuntu Repos or the closed source version from virtualbox.org) and set up a Windows-in-a-Box.

Use that Windows installation to configure the crappy thing. Since by default, the virtualbox "guest" runs behind a virtual NAT router inside the host OS, the ISP's router very probably won't be able to tell the difference, even if it should take record of MAC or local IP addresses.

I've stopped dualbooting my boxes ever since I discovered Virtualbox.

regards

Marc

---

### Post by smacfarl on 2009-03-17
Thanks for the advice so far.

However none of these solutions are really solutions.

Here we have a clear case of a monopoly engaging in anti-competitive practices, for no reason. I picked Ubuntu as my distro entirely because there is a community behind it.

What kind of business fundamentally won't take my money because I have linux? This demands major action.

The goal here is mass adoption of linux, right? Who can I talk to higher up in the food chain, so that we can get adequate linux support from verizon?

---

### Post by the8thstar on 2009-03-17
> **smacfarl said:**
> Thanks for the advice so far.

However none of these solutions are really solutions.

Here we have a clear case of a monopoly engaging in anti-competitive practices, for no reason. I picked Ubuntu as my distro entirely because there is a community behind it.

What kind of business fundamentally won't take my money because I have linux? This demands major action.

The goal here is mass adoption of linux, right? Who can I talk to higher up in the food chain, so that we can get adequate linux support from verizon?

Then you have a case for a pending lawsuit against Verizon : [http://en.wikipedia.org/wiki/United_States_antitrust_law]("http://en.wikipedia.org/wiki/United_States_antitrust_law").

---

### Post by damis648 on 2009-03-17
Install Windows in Virtualbox. That's what I had to do when I got a new modem.

---

### Post by damis648 on 2009-03-17
> **the8thstar said:**
> Then you have a case for a pending lawsuit against Verizon : [http://en.wikipedia.org/wiki/United_States_antitrust_law]("http://en.wikipedia.org/wiki/United_States_antitrust_law").

Only if you think you can win.

---

### Post by sgosnell on 2009-03-17
Some battles are worth fighting, and some aren't.  This one isn't one I'm prepared to fight, it's just not worth the effort to me.

---

### Post by sports fan Matt on 2009-03-17
Had the same battle with at&t with an old computer..When I got my new one though I simply changed the bios to boot from cd and the rest is history.  

PS: I realize its not that simple sometimes but its what I did.

---

### Post by AboveTheLogic on 2009-03-17
silly question....

run their required software in wine, maybe?

---

### Post by damis648 on 2009-03-17
> **AboveTheLogic said:**
> silly question....

run their required software in wine, maybe?

Wine? Doubt it. Virtualbox, sure.:D

---

### Post by lvleph on 2009-03-17
I have verizon, and I just don't use there equipment. Everything works just fine. Maybe they have changed things in the last 2 yrs, but my setup still works.

---

### Post by Don1500 on 2009-03-17
I thought of that, too. When I set up my connection it was with XP. Since switching to Ubuntu I have not had to do anything, it just works.

But I think the OP (smacfarl) said he was going to be doing a lot of Linux boxes without any Windows around so this might not be the answer. Except that he might bring a laptop to each site with a Virtualbox installed, just to get past the set up.

---

### Post by smacfarl on 2009-03-17
So what is actually happening in the Verizon Broadband install, is that the firmware in the router forces you to go to activate.verizon.com. It is this web site that then insists on doing OS and Browser sniffing so it can install some Active-X controls which it uses to install a bunch of windows crapware as well as click buttons to indicate various service agreements.

It's amateur hour, but diabolically so, in that none of these crapware apps support web standards or do anything at all that requires any knowledge of the OS, though they refuse to advance until they sniff an "approved" configuration.

Verizon has just OEMed the construction of the routers, and possibly outsourced the firmware as well. The problem is they do not offer a manual for the firmware, so that you can clearly see how to turn off the forced routing to their activation site.

I have no problem signing service agreements, but there is no reason on god's green earth this can't be done using W3C standards in any compliant web browser. The forcing of OS and Browser choice is as worthy of anti-trust scrutiny as any bundling games Microsoft ever played.

The irony is that the router itself is running linux. A similar Westell modem/router for AT&T actual has open source firmware and is Fedora based. 

So why did Verizon insist on giving the linux world the big middle finger?

I would really like to talk to people who are closer to Ubuntu HQ about trying to get this resolved.

Clearly this is just a naked play to exclude all forms of linux from the home market, and must be stopped.

The minimum solution Verizon must provide is documentation of their firmware so that you can go in and turn off their walled garden if you are running linux.

I am interested to here from other linux users who are interested in solving this problem.

I like Sox fan Matt's boot from CD windows image to satisfy. It's very technically savy, and yet not so aggressive that it would piss anyone off. However I think when billion dollar corporations are threatening the adoption of linux, we as a community must insist on a serious response. New Ubuntu users are not going to want all the hassle of even the this boot from CD/Flashdrive to register solution.

---

