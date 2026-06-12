---
title: "New Linux User Overwhelmed"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by NeedyourHelp on 2013-01-11
Hello Everyone. I am a brand new Linux User with a vague understanding of what I want to do and how to do it.

I am working on a project right now. My goal is to have a secure browsing experience on the internet at this time. I know this will to some degree potentially limit my internet experience but I really need a secure experience at this time.

So here is the just of my problem. I have almost no programming experience. 

The Solutions to the problems presented in obtaining my goal require knowledge of the Ubuntu Terminal. I have a very little knowledge. 

Anyways here is my challenge. I have a wireless router. My computer that I am securing has just been reformatted and has not once been connected to the internet. I want to establish a connection to the internet at home and in public.

However, and this is the fun part for those of you with this knowledge, I wish to have iptables configured before I ever touch the internet in any way shape or form. 

I have an amazing amount of questions. Such as iptables needs to be configured to be able to accept the initial connection to a wireless router in the first place how do I do that. It also needs to be configured to put in place my rules as soon as the initial connection takes place this way my browsing experience is secure as soon as I set foot on the internet. 

I can find a lot of information on the basic set up of iptables for making my internet "basically secure" I am willing to do the research to set up my own rules I really just need to know how to get the initial connection to the router without connecting to the internet. Again this is to make sure my rules for iptables are in place before I get on the internet. Please Help. I can provide general information but detailed information can not be given. So . . . . . This is my challenge please help me.

---

### Post by jonobr on 2013-01-11
Hello


You sound very scared.

[This]("https://sites.google.com/site/easylinuxtipsproject/security") may be a nice easy start in.

[Heres]("https://help.ubuntu.com/community/IptablesHowTo") the howto on the ubuntu homepage,
I would recommend you read a bit before getting started, but again,
this sounds like your very scared to connect to the internet for some reason

---

### Post by kurt18947 on 2013-01-11
Caution is one thing, paranoia is another.  If you want to be able to get in the web and do research without possibly compromising your installed O.S., here's a thought.  Use a live CD/DVD or USB.  Have you tried a live install?  The benefit to a live install from a CD/DVD  is that even if it did get a nasty (which is very unlikely with linux if you use some sense about where you go and what you click),  the nasty is only in RAM and is not going to survive a restart.  A CD/DVD can't 'remember' anything from previous sessions.  A live USB can 'remember' things  if persistence is enabled but the live USB can be nuked and reformatted.  Or simply do not enable persistence.

The biggest question IMO is can you get an internet connection using a live session, either wired or wireless?  If you have a network adapter  that 'just works', you should be golden.  Perhaps use Mint due to its greater inclusion of codecs and flash.  If you have a problem wireless adapter you might still be able to use it on a live USB install with persistence enabled and  install a proprietary driver or use NDISwrapper  but that can get pretty daunting.  I don't own wireless adapters that are 'problem children', they find other homes or are unused.  I am posting this from an Xubuntu live USB session with persistence enabled.  You can do a fair bit to become familiar with linux distros without touching your hard drive.

---

### Post by offgridguy on 2013-01-11
Have you looked at this site yet ?

[[COLOR=Red]https://wiki.ubuntu.com/BasicSecurity[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

A lot of reading but it addresses pretty much everything, including iptables.

---

