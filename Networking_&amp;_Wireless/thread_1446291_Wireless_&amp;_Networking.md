---
title: "Wireless &amp; Networking"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by NZJohn on 2010-04-03
Hi
I'm new and having the same problems as many others with an Acer 3050, NO INTERNET< wireless or wired,
I tried ndiswrapper -l , not installed
then command not found.
Any help would be great!
NZJohn. Christchurch NZ

---

### Post by adam814 on 2010-04-03
I assume you're getting directions from some other post somewhere, if you're getting "command not found" you likely don't have ndiswrapper installed.  Try running "sudo apt-get install ndiswrapper-utils-1.9" to install it first, then continue per the instructions you have.

---

### Post by NZJohn on 2010-04-03
Thanks
I presume I need to download Feisty to get ndiswrapper? It's not installed or found in my ubuntu loaded only yesterday.
PS
I HAVE NO CONNECTIONS at all working...both cable and wireless are not funcional.

---

### Post by mcoleman44 on 2010-04-03
Do you have any drivers listed under system>Admin>hardware drivers?

---

### Post by adam814 on 2010-04-03
Well, that *does* complicate matters.  Maybe you could download the package from packages.ubuntu.com on another machine and store it on a USB drive or something similar?  You'll also need the windows driver(s) you plan to use with it too.

Are you really trying to install Feisty (7.04)?  It hasn't been supported for a long time, I'd recommend a newer version.

---

### Post by NZJohn on 2010-04-03
Tried checking drivers and the result..."No Proprietary Drivers are in use on this system"... 
Maybe I should have stuck with my shaky old XP. (I had a pirated version apparently which came with my used 3050 Acer, no discs, so I tried Ubuntu)!
I have been trolling solutions in the archives but if anyone knows how to sort this It'd be cool. Do I need to download new drivers???
I have a desktop too just as well.
Thanks Guys..PS Assume TOTAL ignorance of code.
J

---

### Post by pdc on 2010-04-04
suspect this is an atheros card; so it should work fine without needint ndiswrapper;

what does 

> /sbin/lspci

give you?

Tell us

a great diagnostic script is this 

[http://www.linux-tips-and-tricks.de/index.php/Netzwerktoolsrepository/View-category.html?ascdesc=DESC&orderby=dmdatecounter](http://www.linux-tips-and-tricks.de/index.php/Netzwerktoolsrepository/View-category.html?ascdesc=DESC&orderby=dmdatecounter)

download it from this link; run it 

this will give you answers; it is safe; the writer is a linux enthusiast; each problem has links, telling you what to do 

come back here though for help as you need it

also:

what does 

> uname -r in a terminal give you?

---

### Post by NZJohn on 2010-04-04
/sbin/lspci: ...No such file or directory
 
uname -r
brings up 
2.6.31-14generic
I'll try looking at your suggested file
Thanks
John

---

### Post by NZJohn on 2010-04-04
did you mean run 'collectNWData.sh'?

---

### Post by alexdelprogramador on 2010-04-04
> **NZJohn said:**
> Hi
I'm new and having the same problems as many others with an Acer 3050, NO INTERNET< wireless or wired,
I tried ndiswrapper -l , not installed
then command not found.
Any help would be great!
NZJohn. Christchurch NZ

hello

most of the cards dont need ndiswrapper to run under ubuntu.

mostly when the laptop is old


....um... type:

```
iwconfig
```

to know what chips you have.

most of the cases, you have to up the device, for example, if you have a wireless device called wlan0, you have tu up it like this:

```
ifconfig wlan0 up
```

There are cards wouldnt work if you dont type this command line.

---

### Post by NZJohn on 2010-04-04
Just tried 'ifconfig wlan0 up' and got...
SIOCSIFFLAGS: Permission denied
Bummer. I think the missing drivers, (there are none listed in my system}, are the culprit here as I cant turn on the wireless switch either, Acer has a switch (manual type) on front of laptop.
If I could get the cable working I can download drivers for the broadcom wireless I think?
Any ideas?

---

### Post by pdc on 2010-04-05
> lspci will tell us your card

---

### Post by framplinux on 2010-04-05
> **NZJohn said:**
> did you mean run 'collectNWData.sh'?

Why don't you just execute the script and post the contents of the resultfile? This will contain all the info people ask for (lspci, ndiswrapper, iwconfig, ifconfig and much more) and will help them to help you ;)

---

### Post by framplinux on 2010-04-05
Just detected an issue with the script on kubuntu. I set a PWD for root on my kubuntu system - but if there is no one defined (the default) the script fails. I just modified the script for *buntu distros to fall back to sudo if su fails. Just download the latest version of the script. Sorry for the inconvenience :redface:

---

### Post by NZJohn on 2010-04-05
Acer 3050 has 
Integrated 10/100 Network Card • Integrated Wireless LAN 
realtek 8139
Broadcom bcm 4318 802.11g wireless 
Tried the 'collect network data' repeatedly, dont know why it wont let me put  password in when it asks 'Plse entr the root password' after it runs it closes and I cant find and dont know where the results (if an)go to? It still asks for a password but wont let me put one in.
rolled thru ubuntu help bu no real help really
How do I install drivers. It says 'NO PROPRIETARY DRIVERS INSTALLED'
Any other ideas?

---

### Post by adam814 on 2010-04-05
That's the issue described in the post above, there's a bug in that script and it should use sudo instead of su.  framplinux reports that it's fixed the in the latest version

---

### Post by NZJohn on 2010-04-07
***Hey thanks mate.***
***I ran Ubuntu from a disc to delete some partitions to reinstall bloody WINDOWS,***
then tried again before giving up... 
and finally got both i/net connections [COLOR=magenta]***WORKING***[/COLOR] after some serious searches, trolling help again then attempts ACTUALLY WORKED after a 7th restart!!
[COLOR=lime]**_BLOODY BRILLIANT!_**[/COLOR]
FNG'S woes must be a pain.
Thankyou again, everyone who gave it a go! NZ John.

---

