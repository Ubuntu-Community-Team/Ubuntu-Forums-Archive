---
title: "Can't Connect to MSN"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by SpongeBob SquarePants on 2009-06-28
Evening all,

This is a strange problem. I recently replaced my old wireless router modem with a similar style Belkin model. Everything set up fine. It all connected fine. But I can't access MSN. Firstly I use Pidgin. Yahoo connects. AIM connects. MSN does not connect. At first I thought it was down...but I haven't connected for three days now. So, out of curiosity, I tried Kopete. Same. Connects to Yahoo and AIM, but not MSN. So I tried aMSN. Wouldn't connect to MSN.

Anyway, I tried to access MSN through the java based client MSN2Go. It connected. Puzzling. So I logged out of Kubuntu 9.04 and into XP, installed Pidgin, same problem. Connects to Yahoo and AIM but not MSN. So, in XP I tried to connect to MSN through Windows Messenger. It connected. I tried to connect to MSN through MSN Live Messenger. It connected.

It makes no sense to me. Despite being able to connect to MSN through Windows Messenger, MSN Live Messenger and MSN2Go, I tried to port forward the necessary ports AND turn off the firewall (Linux's firewall, apparently you can't turn off the router firewall).

Still the same problem. Anyone have any ideas as to why I can't connect to MSN through Pidgin or Kopete all of a sudden, yet I can through the java based client and MSN LIve Messenger and Windows Messenger?

Many thanks

---

### Post by computer13137 on 2009-06-29
Instant messengers in general can be stupid sometimes.  On my Windows box upstairs, MSN won't connect half the time with Trillian.  It says my password is wrong - even though it's not.  Downstairs on Ubuntu, Pidgin connects to MSN fine, but Yahoo always thinks it's signed on at another location, which it's not. :|

I've had a ton of random connectivity issues with MSN in the past.  I'm interested in finding a solution to this problem too.

-Kirk

---

### Post by rodneyorpheus on 2009-12-28
It's a bug in the Belkin router. The quickest solution is to set MSN to work over HTTP in the Pidgin account preferences, that usually works.

---

