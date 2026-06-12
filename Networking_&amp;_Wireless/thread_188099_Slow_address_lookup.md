---
title: "Slow address lookup"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by ghetto on 2006-06-03
Hi,
I've just installed Dapper wtih 99% of success, really happy :-) the only problem I have is with the wifi internet connection. Every time an application (firefox, thunderbird, synaptic or whatever...) try to access an internet resource, it take a while to begin transferring data.
Don't know if it's clear, for example I put [www.google.com](www.google.com) in firefox and the browser look up for 30 second or more before it start downloading the page, after this it download at full speed.
This is a great annoyance when accessing web pages that request differents urls (for example osnews.com), in this case to complete the download of the page take minutes...
With synapting is the same, the download of packages start afer 30 - 40 second, and then everything go well.

I'm using a laptop with centrino chipset and integrated intel wifi card.

I hope my english is not too bad!!

Thank you for any help

---

### Post by toorima on 2006-06-03
try disable ipv6 in firefox to see if that is the problem

open a new tab, type about:config in the adress bar and search for network.dns.disableIPv6. Set the value to true and it should be ok

if that helps disable it for the whole system

edit /etc/modprobe.d/aliases file

find

alias net-pf-10 ivp6

and change it to

#alias net-pf-10 ivp6

and type the following 3 lines

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ivp6 off

---

### Post by ghetto on 2006-06-03
[QUOTE=toorima]try disable ipv6 in firefox to see if that is the problem

open a new tab, type about:config in the adress bar and search for network.dns.disableIPv6. Set the value to true and it should be ok

if that helps disable it for the whole system

edit /etc/modprobe.d/aliases file

find

alias net-pf-10 ivp6

and change it to

#alias net-pf-10 ivp6

and type the following 3 lines

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ivp6 off[/QUOTE]

That's it!! Thank you a lot, I haven't thinked about ipv6...

Now all I have to do is enjoy this fantastic os!

Compliments to all the ubuntu team for a so impressive work!!

---

