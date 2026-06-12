---
title: "networkmanager - how to set the number of attempts at connecting to a network"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by schadenfreude1 on 2010-05-06
Greetings - 

Can someone please help me set the number of retries networkmanager attempts to connect  to a network to infinity?

I live in an area of Australia were wired internet dare not tread (or so say the ISPs). My only real choice is 3G wireless broadband, and even that is iffy at times. Often late at night the network towers do "something" (reset, maintenance, etc. - no idea) and the internet drops out, networkmanager tries to reconnect, fails, tries again, (etc. etc.) until it ultimately gives up, requiring human intervention when the towers are done with whatever it is they are doing. This happens frequently, and I'd like to have networkmanager keep trying "forever" until it connects so I don't have to restart the connection each morning.

Where would such a thing be set? How does networkmanager know when to give up?

Any clues will be received with gratitude. Thanks!

---

### Post by hayden92 on 2010-05-06
Hi schadenfreude1,

I don't know how to do this with GNOME NetworkManager, but it's really quite easy using 
"iwconfig"

Have you ever read 'man' pages before? If so, type "man iwconfig" and look for the option "retry"
You can set the minimum number of retries to 20 by specifying:
```

retry min limit 20

```
Or if you would prefer it to try to connect for 10 minutes after losing connection:
```

 iwconfig eth0 retry lifetime 600

```
(It's in seconds)


If you need more help, please ask,

Hayden M

---

### Post by schadenfreude1 on 2010-05-06
Thanks Hayden,
iwconfig is an option, but my preference is to use networkmanager because this is a mythtv box that is used by technophobes who prefer to click on things rather than open up shells, edit files, restart processes etc. if something goes haywire. Networkmanager is a thing of beauty in that regard.

Basically I'm looking for something like a /etc/networkmanager.conf file (not the xml NetworkManager.conf that which doesn't lead me to "the" place where details are set). I'm confident that tweaking details is possible 'somewhere'. That 'somewhere' is what I'm after.
Thanks again.

---

### Post by hayden92 on 2010-05-09
Ok, well here is what I'd do, because I can't find the solution! 
(This may not be the most efficient way of going about it):

  Write a simple script that connects you to the network (i.e.):
```
iwconfig wlan0 essid "network-name" key s:opensesame retry min limit 50
```
Or something along those lines.

  Make it executable, place it in the "~/bin/" directory.

  Put it in the "Startup Applications" list so that it automatically connects upon startup.

  An then if you really want, add a little launcher in a panel that executes the "connecttowrieless" script that you just made (This way all the 'technophobes' have to do is the clicking!)

  Like I said, it's probably not the most efficient option, but I can help write the script for you if you don't know how.

  Hope this helped,
    Hayden Micallef

---

### Post by pdc on 2010-05-10
this seems ideal for wireless hayden but will it work for 3G broadband, which is what schadenfreude1 seems to be using?

---

### Post by alexfish on 2010-05-10
> **schadenfreude1 said:**
> Thanks Hayden,
iwconfig is an option, but my preference is to use networkmanager because this is a mythtv box that is used by technophobes who prefer to click on things rather than open up shells, edit files, restart processes etc. if something goes haywire. Networkmanager is a thing of beauty in that regard.

Basically I'm looking for something like a /etc/networkmanager.conf file (not the xml NetworkManager.conf that which doesn't lead me to "the" place where details are set). I'm confident that tweaking details is possible 'somewhere'. That 'somewhere' is what I'm after.
Thanks again.

Hi 

try looking in the ppp options file : /etc/ppp/options

trying to edit the network managers config files will render your connection void and also the file , reason security ; 

to see what the options are:

Code:

egrep -v '#|^ *$' /etc/ppp/options

---

