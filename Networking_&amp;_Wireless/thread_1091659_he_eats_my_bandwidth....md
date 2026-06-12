---
title: "he eats my bandwidth..."
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by WOOHOOHOO on 2009-03-09
Hi,

I'm a generous guy and let my housemate use mybroadband for free. Sadly he has a fetish for movies and he soaks up all my bandwithand makes internet access slow. I keep unplugging him from the router, but he knows when i do it.  I have a few q's please:

1 - How do i make my computer the 'dominant' one with regards to me getting priority share?
2 - Since changing from XP to Ubuntu, i no longer needed to install the Virgin Media CD to set-up the modem/router. But, my internet is a lot slower (even without the BW whore upstairs attached). What can i do to make it faster (i use latest mozilla with faster fox, and several tweaks in the auto:config). I forgot the username i setup when i had it on XP, and i don't know how to change it/reset. And ideas?
3 - I want to use Bittorrent, the one supplied on Ubuntu. I used i ok, but chaged the ports to see if it would help following advice from other forum. What is my best choice of port. And which port do you change, as there are 2 different ports (one is listening something)?

Thanks on advance.

I use:

Ubuntu 8.10 Intrepid.
Router: netgear g-router, WGR414
NP: Virgin.

I'm still leaning the commands etc, so please give as much detail as poss.

Thank you

---

### Post by jonobr on 2009-03-09
For the hogging stuff,
Its your connection,
kick him/her off,

see [here]("http://http://ubuntuforums.org/showthread.php?t=1066616") also, for some advice.

Downloading at night, I though was the better option

---

### Post by puppywhacker on 2009-03-10
first of all, I did also shared my internet for free once. People just don't understand they are abusing a good deed.

there are a couple of things you can do
1. use "squid" as an http proxy and deny all other traffic, you can rate-limit squid.
2. use "iptables" ratelimiting
3. use "tc" traffic control to assign a bandwith group

---

### Post by Helios1276 on 2009-03-10
Put him in the DMZ til' he fries ;)..joke..kinda.

But really I feel your pain, I have a housemate who is kind of a technophobe but that doesn't prevent him from using his precious macbook on a connection he did not pay for. I even put up with his constant requests for support when he lost connection etc ..until I bought a server and he demanded I disconnect it as he blamed it for his inability to connect a couple of times...some people!

---

