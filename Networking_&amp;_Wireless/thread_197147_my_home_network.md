---
title: "my home network"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by dragonflyFZX on 2006-06-15
hi all,

i want to set up the following network, i have been searching the how tos and forum, but no luck.  The trial and errors result too frequently in a total freeze of the computer that is also functioning as a web server...

i have a laptop that is connected to the net using a thompson speedtouch adsl ethernet router.  That laptop has a second pcmcia network card, which i want to use to connect it to my new laptop.  I have two questions for which i could not find the answer (or the answer was too difficult for me to understand)

1. How can i share the internet connection of the first laptop with the new laptop?

2. How can i share files and folders between the two computers?

---

### Post by lkagan on 2006-06-15
My first suggestion would be to go to the store and buy a cheap little router.  That will make life much much easier for you.  The latest release of Ubuntu may include an 'internet sharing' option that I haven't seen yet.  But for Linux in general, you'll have to set up your first system as a router so that it can forward requests on the second systems behalf.  I just did a quick search and it looks like Firestarter can accomplish this for you.  See [this link]("http://www.ubuntuforums.org/showthread.php?t=195252").

Good luck,

Larry

---

### Post by dragonflyFZX on 2006-06-15
ok, thanks for the pointer, i will install firestarter and see if i can get anywhere then.  I also had another question.  Will i have to use a normal UTP cable or an X-wired UTP?

---

### Post by lkagan on 2006-06-15
I've never done this in practice, but if I remeber correctly from my Network+ certification, you'll need a crossover cable.  You'll definately want a second opinion on that. 

Larry

---

### Post by Slim Odds on 2006-06-15
[quote=lkagan]I've never done this in practice, but if I remeber correctly from my Network+ certification, you'll need a crossover cable.  You'll definately want a second opinion on that. 

Larry[/quote] 
Yes, to directly connect two ethernet ports, you would use a crossover cable.

---

### Post by dragonflyFZX on 2006-06-19
this internet connection sharing thing has been a nighmare up to now.  I have been trying every single howto on this forum to no avail.  Here is the setup again:  I have an ubuntu laptop connected to a thompson ethernet adsl router, which gets it ip from the isp using dhcp (this is also an internet server which can not be disconnected).   I have a second ethernet pcmcia card in this laptop, which is connected to another laptop's ethernet connection, the one i actually use as my main machine.  I have tried, as suggested, to set the ip of the second ethernet card of the first laptop to something static like 198.162.0.1 and the one on the second laptop to something static like 198.162.0.2 and the default gateway on 198.162.0.1, but cant connect to the internet on the second laptop...   Not in linux, not in windows...  As a matter of fact, the first laptop often completely freezes when i try to connect it to the second.

Tried the firestarter suggestions, everything.  Is there someone who can help me?  What commands do i have to use to see what the problem is?

---

### Post by lkagan on 2006-06-19
Did you use a crossover cable?

---

### Post by dragonflyFZX on 2006-06-19
yes i do, see above

---

### Post by lkagan on 2006-06-19
You didn't mention the crossover cable explicitly so I figured I would just double check.  Once again, simply buying a cheap $20 router would do the trick but if you want to really get your hands dirty, you'll have to manually enter iptables rules.  [This link]("http://www.haxial.com/faq/routerconfig/linux/") might help.

---

