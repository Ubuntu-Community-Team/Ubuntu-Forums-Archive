---
title: "Selective Synchronization of Connection Tracking State Tables between Firewalls using"
date: 2013-07-15
forum: Networking &amp; Wireless
---

### Post by uautkarsh on 2013-07-15
_Selective Synchronization of Connection Tracking State Tables between Firewalls using conntrackd_
I have got three firewalls running on Ubuntu 12.04 Server in  the ACTIVE/BACKUP/BACKUP mode. The firewalls are using iptables. I am  using Keepalived and Conntrack-Tools for the "High Availability" and  connection tracking state table synchronization.
  What i want to achieve here is to make the synchronization of the  state tables to be selective. For instance, if i have 3 connections (A,  B, C) in the state table entry in the master, then i would want the  BACKUP 1 firewall to sync only connections A and B, and the BACKUP 2  firewall to sync only connections A and C.
  Is there a way to apply such a filter and to make the synchronization selective?

---

### Post by uautkarsh on 2013-07-15
I read somewhere that conntrackd has got the feature for selective replication.
But there's so less documentation that i cannot find anything.

---

