---
title: "Suddenly lost the ability to view web pages yet networking is functioning"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by ThaddeusW on 2010-04-03
Solved!

I should have poked around a little harder but I remember that I was experimenting with an ssh proxy when a the hotel. Apparently when I setup the proxy settings in Chrome I must have clicked the "set system wide" button and set every browser to browse through the proxy. I even had to enter a password to change that setting. I thought I changed it back after experimenting but apparently I did not.

Original post:
Today I just started my Ubuntu 9.04 laptop to find that I can not browse web pages. I tried multiple browsers including Chrome, Firefox and Epiphany. Each one gives me the same error message:

Epiphany:
"www.google.com" dropped the connection. 
The server dropped the connection before any data could be read. The server may be busy or you may have a network connection problem. Try again later.

Firefox:
Connection Interrupted
The connection to the server was reset while the page was loading.
The network link was interrupted while negotiating a connection. Please try again.

Chrome:
This webpage is not available.
The webpage at [http://www.google.com/](http://www.google.com/) might be temporarily down or it may have moved permanently to a new web address.

So now most of you are ready to ask me to check my connection using ifconfig etc. But here is the rub: I can download updates, install software using apt-get, ssh, scp, download files with wget, ping web sites and browse the net using the text browser Links (so pretty much everything else works.) I cant figure out what has happened. The last time I used my laptop was this past weekend in a hotel using their wireless and then connecting using a captive portal. And everything worked fine. My only theory is the hotels captive portal might have messed up something but what that is is beyond me.

I tried using both wired and wireless connections and still the same thing. Re booting does nothing. So in order to surf the web I have to use my virtual box Windows XP image. So here I am typing this message in Firefox on windows XP in a virtual machine on my Ubuntu laptop that for some reason will not let me view websites.](*,)

What has happened? This honestly makes absolutely no sense whatsoever.

---

### Post by RedSingularity on 2010-04-03
Sounds like a dns problem.  You say you can ping web addresses in terminal?

---

### Post by jodela on 2010-04-04
I recognize (big) part of the problem.

I have a Xubuntu 9.10 Karmic that was working happily till 1 or 2 days ago.

Since then I have weird issues, very much along the lines of what you describe.

It started with not being able logging into hotmail. Or at least only very occasional. I have also a (curl based) script for that purpose (GetLive on sourceforge) that shows similar issues (i.e. it blocks/times out on certain addresses)

I can start facebook, but certain functionality doesn't work , apparently timing out. I can go to sourceforge but mostly I cannot login for the same reason.

All of above is mostly with firefox, but also curl thus. Sometimes it works slightly better with konqueror, but that's not always the case.

Ping (or anything else) seems to work pretty much correct. So it *appears* to be http (or https ?) related.

One of the things I tried to make it better is disabling ipv6 on booting, but it did not help.

I would be interested in hints towards solution as well. I don't get the finger behind it, but obviously there's something weird with networking for the moment.

My Windows portable behind the same Linksys router shows no issues whatsoever. Also not with firefox.

Any clues as how to find the issue ?

Jos

---

### Post by jodela on 2010-04-04
I want to add something that appears relevant to me.

As I said, I have another notebook in the local network, running windows, that does perfectly fine.

I now ran the 9.10 Xubuntu as a Live CD on that machine.

Using firefox I went to [http://www.sourceforge.net](http://www.sourceforge.net) and I could *not* login neither. Apparently I have also a netwerk timeout there.

So I have now 2 machines , one with the live cd, one fully installed and used for a long time that seem to show that same issue.

It works perfectly under windows. Ping doesn't show anyting specific to me.

Next experiment will be to remove the router (a Linksys WRT54GS) out of the equation, but I feel that I (we .. ?) are facing something weird.

Any pointers appreciated !

Jos

---

### Post by jodela on 2010-04-04
Don't ask me *why*. But apparently something changed, likely in the providers network topology.

Reducing MTU to 1450 on the network connection fixed everything back to normal.

(and that's reproduceable, i.e. on both linuxes, the live and the final).

HTH,

Jos

---

### Post by ThaddeusW on 2010-04-04
> **RedSingularity said:**
> Sounds like a dns problem.  You say you can ping web addresses in terminal?

Yup DNS works fine. I can browse the web in links and wget works using regular URL's. So its not DNS related.

Its as if there is some DNS setting, library or other setting that is strictly used by graphical web browsers that is messed up. Otherwise why would Links browse to google.com but the 3 GUI browsers don't. Same for wget.

I will look into it again when I am at work tomorrow.

---

### Post by jodela on 2010-04-04
ThaddeusW, can I ask where you are based ?

The solution I gave (lowering the MTU) seems to be a workaround for a hickup (i hope) in the Belgian ISP world.

---

### Post by ThaddeusW on 2010-04-10
Solved.

---

