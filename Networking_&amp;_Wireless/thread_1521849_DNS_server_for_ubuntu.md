---
title: "DNS server for ubuntu?"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by thenameisgabe on 2010-07-01
So I'm working on a project using the beagleboard running ubuntu karmic. This board creates an adhoc wireless network which allows other devices to connect and communicate to it.

Because there may be several of these in the same area, we need to figure out a way to connect to them without hardcoding IP addresses. Essentially, I want to be able to create a local domain name that points to each board (without editing the /etc/hosts file of each device that connects to it). 

In other words, if I connect to one of the beagleboards and type the following on the computer using to connect:

ping beagle1.mod

I should receive a response. Now, clearly this is what DNS was meant to do. Since i'm a DNS scrub, is there a semi-simple way to do this on ubuntu? This includes figuring out how to get the dhcp server to provide nameservers to the computers connecting to it.

If i remember correctly, we are using dhcp3 for our dhcp server.

I have tried the several bind9 tutorials that are floating around, but none of them seem to work, any thoughts?

---

