---
title: "Everything is giant! How do I get better resolution?"
date: 2009-01-31
forum: Multimedia Software
---

### Post by person9 on 2009-01-31
I just installed Ubuntu using Wubi, so I run Vista on this laptop too. I love Ubuntu, but right now the only options for graphics resolution is 800x600 and 640x480. Incredibly frustrating.

Since I'm new to Ubuntu (about 5 minutes ago), I'd like to know how to deal with drivers in it. How do I get the appropriate ones? I have some kind of nVidia graphics card.

---

### Post by Tim Drallmeier on 2009-01-31
whats is your laptop? please give some specs.. manufacturer, model, and so on...

---

### Post by person9 on 2009-01-31
It's a new (June) HP dv2745se, nVidia graphics (dont know what kind off the top of my head), Broadcom WLAN (as you can tell, the wifi is working fine), 3 gigs RAM, "250 gig" hard drive but started with 160 and has about 140 gig right now, AMD Turion 64 x2 processors, ... 

Running Windows Vista (no SP1) as the other OS, used the Wubi install for Ubuntu. Is there any other info that'd be helpful?

---

### Post by Tim Drallmeier on 2009-01-31
hmm.. im betting that you have the 7150M Nvidia card... I have the same problem with my laptop, a DV2845Se. and havent gotten it to work, but, for starters, lets try this. go to system, admin, and then to hard ware drivers. Open this up, and then click to install and run the drivers. Let me know if this works.

---

### Post by whaevr on 2009-01-31
K I'm not running Ubuntu but go to System in the gnome panel and then either Administration or Preferences and their should be something there for hardware drivers.

Try that.

Edit: Suggested at the same time lol.

---

### Post by TheLaughingMan84 on 2009-01-31
Use envy to get your nVidia graphic drivers.

```

sudo apt-get install envyng-qt envyng-core

```

---

### Post by person9 on 2009-01-31
Ok thanks everyone. Here's what happens: it's suggesting two drivers for my nVidia.

nVidia Accelerated Graphics driver (version 173)
nVidia Accelerated Graphics driver (version 177) [recommended].

I click "Enable" on either one, and I have already typed my password. It appears that it's about to connect and start downloading, but it comes up with an error message. 

Ugh I was going to paste what it says but now that dialog box froze and I have to go somewhere. I will post again in about 10 minutes what it says.

---

### Post by whaevr on 2009-01-31
I would recommend you do what TheLaughingMan84 suggested and use Envy to install it. It'll get the latest driver and do everything for you automatically. 

Forgot about Envy..haven't needed it since I don't use Ubuntu anymore =P

---

### Post by person9 on 2009-01-31
SystemError: Failed to lock /var/cache/apt/archives/lock


^thats what it says.

---

### Post by whaevr on 2009-01-31
Hmm do you have Synaptic running? Or are you downloading updates?

---

### Post by yanom on 2009-01-31
this WILL work:

```

sudo apt-get install envyng-qt envyng-core

```

but that installs the Qt version of envyng. The Qt version depends on more libraries that Ubuntu doesn't have installed by default. So you should get the GTK version:

```
sudo apt-get install envyng-gtk envyng-core
```


It would be a different story if you had **K**ubuntu, but you have **U**buntu

---

### Post by person9 on 2009-01-31
> **whaevr said:**
> Hmm do you have Synaptic running? Or are you downloading updates?

I don't know what Synaptic means, so probably not. :) And I finished downloading updates already.

---

### Post by person9 on 2009-01-31
What exactly is this "Envy" I'm being instructed to use? I'm open to trying it but I dont know what to do when someone's like, "Use this. Code: Bla bla blah." 
What do I do with this "Code?"

Sorry, Ive never used this before at all! :)

---

### Post by whaevr on 2009-01-31
Have you tried running:
```

sudo apt-get install envyng-gtk envyng-core

```

In terminal, and then using Envy to install your driver?

Go to Applications, then accessories, then terminal. Paste that command in it.

---

### Post by person9 on 2009-01-31
ohhh i get it. I'm at band practice now and i'll try later and post my results. thanks!

---

### Post by person9 on 2009-01-31
Ok I pasted that code in to Terminal, and ran it, and it did a bunch of text stuff and then finally was finished. So now I'm like, ok.. what do i do?

Is Envy an application now? or what?

---

### Post by person9 on 2009-01-31
**** PROBLEM SOLVED ******
At 11:23 pm tonight, I did the same thing I had been doing all afternoon.

I had pasted that Envy script in terminal, run it, and then after being confused, run a script to remove it.

The recommended proprietary driver has been downloaded without explanation now, and I am not complaining.

Thank you EVERYONE for your suggestions, I considered *all* the things that were posted.

---

