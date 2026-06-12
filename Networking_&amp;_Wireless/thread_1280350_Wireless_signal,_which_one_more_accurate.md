---
title: "Wireless signal, which one more accurate?"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by csh on 2009-10-01
Please look at the attached screenshot (taken in 1440 x 900 resolution).

I installed the gnome-netstatus-applet package.

I am using D-Link DW-110 USB WiFi Adapter.

The NetworkManager icon showed that my wireless signal strength is only 71% while Network Monitor (gnome-netstatus-applet) showed that my wireless signal is 94%.

Which one more accurate?

---

### Post by kidders on 2009-10-04
Hi there,

Signal strength percentages are really more of a matter of opinion than fact, similar to CPU usage percentages. They're both abstractions that can be computed in a variety of different (but equally legitimate) ways, and don't really reflect anything meaningful per se. For example, if the meter in your menu bar tells you you have 100% signal strength one minute, and 50% the next, all you can interpret from that is that your signal quality has gotten worse ... How *much* worse is a question you can't answer, nor can you really quantify how strong "50%" really is.

These numbers are usually intended as guides. For example, over time you may discover that when the meter in your menu bar says anything lower than 30% your internet connection goes funny. If you install a third signal strength meter, you may well wind up with yet another set of figures.

If you look into it, you may for example discover that one meter is using a logarithmic scale to convert from dBm to percentages, where the other is using a more linear one. Some people might see such an inconsistency as a bug ... then again, others may not.

I hope that helps.

---

