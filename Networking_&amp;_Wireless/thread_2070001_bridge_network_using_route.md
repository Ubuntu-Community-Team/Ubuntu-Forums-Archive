---
title: "bridge network using route"
date: 2012-10-11
forum: Networking &amp; Wireless
---

### Post by jwannabe on 2012-10-11
Hi everyone,

This is my first post on ubuntu forum and hoping that someone can help me out :)

I have been googeling and searching on how to do bridge my wifi connections to my internet connection using route.

I have a ubuntu server 12.04 with a wifi and normal network card

I also have a router that is connected to the internet

on my ubuntu server i have eth0 connected to the router; IP 192.168.1.12 GW 192.168.1.1 DNS 212.54.40.25

this all works great

I have set up my wlan0 as my accespoint, and DHCP to feed an IP to any device that connects to it.

if i connect, for example, my android smartphone to my wlan0 acces point it will get the following IP 10.10.0.2 GW 10.10.0.1 DNS 212.54.40.25

How in earth can I bridge this connection and acces the internet from my android?

I dont want to make use of BR0 bridge-utils but accomplish this using route.

Many thanks in advance

---

