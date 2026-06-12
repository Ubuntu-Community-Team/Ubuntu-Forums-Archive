---
title: "&quot;Spiky&quot; internet connection"
date: 2012-02-09
forum: Networking &amp; Wireless
---

### Post by mushashi on 2012-02-09
Starting a couple of weeks ago, downloads from the internet are spiky - they'll go fast, then slow, then fast, and so on until either the download completes or it times out.  

Wireshark indicates a few warnings, mostly that segments are getting lost and a few suspected fast retransmissions.  Which, hey, is probably the problem.

I'm using Chromium (v. 16.0.912.77 right now) on 11.10.  Interestingly, Firefox downloads behave some of the time (No clear pattern as to succeses). Pings to the router while downloading are constant, around 2ms with no spikes.    If it makes a difference, the connection is using the sky2 driver.

How do I narrow down what's causing things to go bad?

---

