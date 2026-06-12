---
title: "firefox problems"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by origr15 on 2009-04-20
why is it so , that when i press on the firefox icon a window opens but it kinda is in stuck (i have no good word for it) for 3 seconds and then it loads my homepage ?

oh and some webpages it loads so slowly and a lot of hte time when i scrol down on a page it does nothing and after a few seconds (it can actually get up to half a minute) it starts moving? it's very anoying .

i have a very strong pc and ubuntu 9.04 RC 32 bit , my friend who has ubuntu 8.10 says this doesnt happen to him , it's not related to that that im using 9.04 because it used to happen to me all the time even in my old pc even from the time of 7.04...

please i beg anyone to help me because i really dont want to go back to windows. :) :D

---

### Post by coffeecat on 2009-04-20
> **origr15 said:**
> it's not related to that that im using 9.04 because it used to happen to me all the time even in my old pc even from the time of 7.04...

Which suggests we need to look at your internet connection.

One thing that springs to mind is that possibly your router is not handling IPv6 addressing properly (IPv6 is enabled by default in Ubuntu). This can happen with older routers, or with older firmware. It's not an issue in Windows XP (but is in Vista), because in XP IPv6 is disabled.

Two things: post details of your modem-router. What sort of internet connection are you using, adsl or cable, or something else?

Now try this:

Open Firefox. Type 'about:config' in the address bar (no quotes). Click OK on the 'Here be dragons' message. Type 'ipv6' (again no quotes) in the filter. One line should appear starting 'network.dns.disableIPv6'. Change the false at the end of the line to true. Now close Firefox and restart. If that solves the problem, we need to find a better fix. If it doesn't, then sorry, forget everything I've said about IPv6.

---

### Post by origr15 on 2009-04-21
the one thing that im 100 precent sure is that its not relates to my internet connection beacause my internet itsleft is fast and opera is moving just fine the problem here is with firefox and what i mantiond before.

oh and i have a 3 mega internet cable connection. that really doesnt have problem - i download stuff just fine and surf on opera fine but the problem is with firefox

---

### Post by coffeecat on 2009-04-21
<sigh> - well if you can't be bothered to try out a simple and quick test to exclude one problem, I can't be bothered to suggest the other two possibilities I had in mind.

---

### Post by Motw on 2009-04-21
Type **ifconfig** in your terminal. Theres a load of text, but if it contains "MTU: 1500" you should put that to 1492. Ive had the same problems and it seems that a lot of people are bothered with this.

PS. I think you should look at the IPv6 too. If youre too lazy to do that we shouldnt be even bothering to help.

---

### Post by adster101 on 2009-04-21
Just a thought but do you have the Firebug extension installed? I had exactly the same problems until recently and figured out that it was Firebug causing the problem.

If you have it installed then disable it and see if it makes any difference.

---

### Post by granareiv on 2009-04-21
> **origr15 said:**
> why is it so , that when i press on the firefox icon a window opens but it kinda is in stuck (i have no good word for it) for 3 seconds and then it loads my homepage ?

oh and some webpages it loads so slowly and a lot of hte time when i scrol down on a page it does nothing and after a few seconds (it can actually get up to half a minute) it starts moving? it's very anoying .

i have a very strong pc and ubuntu 9.04 RC 32 bit , my friend who has ubuntu 8.10 says this doesnt happen to him , it's not related to that that im using 9.04 because it used to happen to me all the time even in my old pc even from the time of 7.04...

please i beg anyone to help me because i really dont want to go back to windows. :) :D


Maybe you have these problems due to any add-on or plugin. Find out if disabling or uninstalling some of them you can work with no problems.

---

### Post by origr15 on 2009-04-21
i dont have firebug. and the only extansions i have are google toolbar and greasemonkey but the problem were before i installed them..

i think the problems are with flash in firefox because theres a website that has a lot of flash stuff in it and it used to get really slow with all the problems i described but when i installed script on freasemonkey that disabled the flash ads the site became fast and normal , oh and today i tried to play some videos on a site and firefox has serious problems with sound and lagging while opera displayed them perfactly..

what's 1492?

oh and dont take it personaly but i know it's internet stuff i really do im not a "pro" but im not a noob im really not.. belive me when i say its softwere trouble... but i have no problem check what u said , but i dont know what 1492 is - what is it?

---

### Post by origr15 on 2009-04-21
MtU:1500 

it does say that , what should i do?

---

### Post by cloo on 2009-04-21
I was having a similar problem. Did the ipv6 change suggested by coffeecat. End of problem.

Thanks!

---

### Post by coffeecat on 2009-04-21
> **cloo said:**
> I was having a similar problem. Did the ipv6 change suggested by coffeecat. End of problem.

Not quite cloo. You've solved Firefox, but the IPv6 problem may (or may not) affect other parts of the system when accessing the internet. Since the OP isn't interested in IPv6 ( :wink: ), may I suggest you start your own thread to get to the bottom of what's going on and fixing it properly? Please post all relevant information. I'll look out for your thread if you choose to start one.

---

