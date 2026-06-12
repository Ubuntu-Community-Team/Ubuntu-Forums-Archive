---
title: "Questions about NetworkManager"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by grizdog on 2010-01-24
Hi,

I'm new ubuntu /gnome, coming over from fedora/kde.  I may move to kubuntu at some point, but for now, I want to give gnome a try for a while.  I have some questions that I have not been able to find in TFM, although I am sure the answers must be there somewhere, so if you want to direct to exactly where, I would appreciate it.

The first question is probably more gnome question.  I found the little icon for NetworkManager up high on the gnome desktop, and as long as it is there I can run it that way.  But just in case it goes away some day, for whatever reason, I'd like to know what that icon is doing.  Here is one place where the basic ubuntu documentation is not helpful, it just says use the icon, but there must be some gnome docs that will help.

When I use my laptop, I typically am connecting to a network I have little or no experience with - like in an airport or hotel, or a small business, or something like that.  They usually have a very high level explanation of how to connect - like to type something into your browser, or they give you a username and password, but they never tell you WAP or WEP or a 128 bit key.  NetworkManager seems to want to know which protocol.

So my question is, how do I connect to these newfangled networks, especially if I am in an environment that has several running at once and I have to pick one.

Thanks.

---

### Post by chili555 on 2010-01-24
> So my question is, how do I connect to these newfangled networks, especially if I am in an environment that has several running at once and I have to pick one.Generally, it will be pretty obvious which one you want. They will have names that sort of indicate who they are, like 'coffee_wifi' or 'MotelNet' and they are usually unencrypted. You simply click on them and connect. The IP address and DNS nameserver you are given directs you to a sign-in page where you must plug in the details you were given at the desk. Then you click on your home page (presumably ubuntuforums.org!) and you are all set.

If you see a network 'jakes_trukstop' and it's encrypted, it's clearly not the one you want. Network Manager asks for a WEP or WPA key when it detects that the network you've selected wants one.

---

