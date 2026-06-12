---
title: "Any good guides for configuring ATi Crossfire (9.04)"
date: 2009-04-28
forum: Multimedia Software
---

### Post by wiznillyp on 2009-04-28
Are there any good how-to's or other guides for setting up Crossfire in Linux (specifically Ubuntu Jaunty)?

All I found was [this]("http://www.phoronix.com/scan.php?page=article&item=amd_crossfire_linux&num=1") which is more of a review than a how-to.  I have two 4850s on a board with a P35 chipset (Yes... I know).

Also, for other that have done this, how does it work for you?

---

### Post by HappyFeet on 2009-04-28
A search on google for **Ubuntu ATI Crossfire** yields no results. That's not a good sign. It probably can't be done.

---

### Post by wiznillyp on 2009-04-28
> **HappyFeet said:**
> A search on google for **Ubuntu ATI Crossfire** yields no results. That's not a good sign. It probably can't be done.Well, people do have it done, such as the article I linked to.

And yes, I definitely tried a web search before posting here.  Not luck either.

Finally, CT??  West Hartford here!

---

### Post by baczynskims on 2009-04-28
I would like to know as well. I have two hd 3850s on a 790fx dfi board. I tried the proprietary drivers that I am notified automatically through ubuntu. I also tried installing the 9.4s from amd. Both install, but neither of them will load the gui. I can only get to the command prompt on boot. I then do sudo aticonfig --initial and reboot. I then get what looks like the login screen , but with only a few lines of random graphics filled. So essentially the desktop is useless then as far as a gui. I also tried envyng with the same results. Is this issue because of crossfire or simply having that card?

---

### Post by wiznillyp on 2009-04-28
Well, I got Crossfire to work.  I used the aticonfig tool.

To get the ATi drivers to install correctly, I just used the 9.4 Cats and installed them EXACTLY as instructed on ATi's website.

---

### Post by baczynskims on 2009-04-29
when you say you used aticonfig, what exact command did you use. I would assume you downloaded and installed the drivers from amd and then did the sh command? After that did you boot to nogui? That's what I am getting right now. After I install the drivers no matter if it is through the ubuntu integrated way, amd's official driver package or envyng, I still end up at the command prompt and aticonfig --initial does not work. I am getting frustrated because this worked fine in 8.10 but I really like everything else about 9.04

---

### Post by seoolas on 2009-05-04
> **wiznillyp said:**
> Well, I got Crossfire to work.  I used the aticonfig tool.

To get the ATi drivers to install correctly, I just used the 9.4 Cats and installed them EXACTLY as instructed on ATi's website.

1. Did you do an automatic installation or a custom one?
2. Did you indeed launch the terminal and used: /usr/bin/aticonfig --initial
3. Does 9.4 Catalyst provide the "enable crossfire" check box like in the windows version?

Thanks for replying (beforehand anyway...)

---

### Post by Melcar on 2009-05-04
Once you have the driver installed just run aticonfig on a terminal to get all the available commands.  Near the end of the list are the Crossfire command options.  CCCLE still lacks a control box for Crossfire, so only by way of the command line can you get it to work.

Edit:

```
Multiple display adapter options:
  Following options are used for querying and setting up multiple
  display adapters that are installed for multihead or Crossfire
  configurations.
  --lsa, --list-adapters
        Lists all detected and supported display adapters.
        The default adapter (used when --adapter is not specified)
        will be indicated with a "*" next to it.
  --adapter=ADAPTERLIST
        Selects which adapters returned by --list-adapters should
        be affected by other aticonfig options.  ADAPTERLIST contains
        either a comma-seperated sequence of the index numbers of the
        adapters to be affected or else contains the keyword "all" to
        select all the adapters.  If --adapter is missing, only the
        default adapter will be affected.
  --lscc, --list-crossfire-candidates
        Queries the driver to determine the pool of available devices that can
        can be chained together for CrossFire.
  --lsch, --list-crossfire-chains
        Lists the CrossFire chains that are currently defined along with their
        enabled state
  --cfa, --add-crossfire-chain
        Defines a new CrossFire chain.  --adapter should contain the adapter
        chain definition, with the master adapter being the first entry and
        the slave adapters being the subsequent entries in order of priority.
  --cfd, --delete-crossfire-chain
        Delete and existing defined CrossFire chain.  --adapter should list the
        master adapters of the chains to be deleted.  --adapter=all will delete
        all chain definitions.
  --cf, --crossfire={on|off}
        Enables/disables CrossFire support on the currently defined CrossFire
        chains.  --adapter should list the master adapters to be enabled or
        disabled.
  --cfl, --crossfire-logo={on|off}
        Enables/disables the appearance of the CrossFire Logo when rendering
        in CrossFire mode

```

---

### Post by wiznillyp on 2009-05-04
> **baczynskims said:**
> when you say you used aticonfig, what exact command did you use. I would assume you downloaded and installed the drivers from amd and then did the sh command? After that did you boot to nogui? That's what I am getting right now. After I install the drivers no matter if it is through the ubuntu integrated way, amd's official driver package or envyng, I still end up at the command prompt and aticonfig --initial does not work. I am getting frustrated because this worked fine in 8.10 but I really like everything else about 9.04When I installed the drivers, I followed the step-by-step instructions on the AMD site.

Using the "restricted drivers" nonsense did not load the GUI, just like you.

As far as crossfire goes, I used 

sudo aticonfig --cfa --adapter=all
sudo aticonfig --cf on

Then rebooted.

BTW, sorry about not responding, I forgot to subscribe to this thread.  (fixed my settings to auto-subscribe now)

---

### Post by wiznillyp on 2009-05-04
> **seoolas said:**
> 1. Did you do an automatic installation or a custom one?I followed the installation instructions right from the site.> 2. Did you indeed launch the terminal and used: /usr/bin/aticonfig --initialYes, please see my above reply.> 3. Does 9.4 Catalyst provide the "enable crossfire" check box like in the windows version?No, as far as I know, there is only a CLI for enabling crossfire.  aticonfig --cf on/off. Good Luck

---

### Post by FarmerGiles on 2009-06-12
May I correct the last line for enabling crossfire...

should be:

aticonfig --cf on --adapter=all

you should then get a message that crossfire is enabled and will be active when X restarts


Hope this helps ;)

---

### Post by lemn8 on 2009-08-09
> **FarmerGiles said:**
> May I correct the last line for enabling crossfire...

should be:

aticonfig --cf on --adapter=all

you should then get a message that crossfire is enabled and will be active when X restarts


Hope this helps ;)

This is getting me a black screen after rebooting. I've had to turn --cf off again then the problem was partly solved.

---

### Post by lemn8 on 2009-08-09
> **lemn8 said:**
> This is getting me a black screen after rebooting. I've had to turn --cf off again then the problem was partly solved.

So this is the way i did it and it still works.

sudo aticonfig --adapter=0,1 --initial
sudo aticonfig --cfa --adapter=0,1
sudo aticonfig --cf on --adapter=0,1

And then reboot...

---

