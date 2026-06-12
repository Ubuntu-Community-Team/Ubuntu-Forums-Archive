---
title: "Software Center very slow"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 0004tom on 2010-10-06
I installed maverick for the third time last night, and decided to keep with it till the end of the testing cycle. Other then all the bug I know about that effect me, none are more irritating then the useless software center. 

In Lucid the software center worked perfectly as it should. Now with Maverick. If I try and open it, I can go and make a coffee before it appears on my screen. Trying to install a package from it.. HA no chance.. So I browse for the package I want to install, I click install.. nothing happens.. It just sits at the authenticate popup window doing nothing. I really haven't sat there long enough to see if it installs and finishes I just force quit the software-center and open up a terminal and run apt-get. 

Installing a .deb, your having a joke right? samething as a package from the repos, force quit, and run dpkg.

I've searched and couldn't find anything the same as this, is anyone else seeing this useless behavior from the software-center?

I'm just glad there keeping synaptic, atleast with this i have some kind of useable package management gui.

---

### Post by 23meg on 2010-10-06
I've edited your title to be descriptive of your problem. Your thread will attract less random off-topic posts this way.

---

### Post by VMC on 2010-10-06
> **0004tom said:**
> I installed maverick for the third time last night, and decided to keep with it till the end of the testing cycle. Other then all the bug I know about that effect me, none are more irritating then the useless software center. 

In Lucid the software center worked perfectly as it should. Now with Maverick. If I try and open it, I can go and make a coffee before it appears on my screen. Trying to install a package from it.. HA no chance.. So I browse for the package I want to install, I click install.. nothing happens.. It just sits at the authenticate popup window doing nothing. I really haven't sat there long enough to see if it installs and finishes I just force quit the software-center and open up a terminal and run apt-get. 

Installing a .deb, your having a joke right? samething as a package from the repos, force quit, and run dpkg.

I've searched and couldn't find anything the same as this, is anyone else seeing this useless behavior from the software-center?

I'm just glad there keeping synaptic, atleast with this i have some kind of useable package management gui.

Launch software-center from a terminal and see if any errors come out.

Also check some logs @ /var/log

---

### Post by M4570D0N on 2010-10-07
I've been getting the same issue with synaptic lately at seemingly random times. if i do anything, whether it's typing a search word, right-clicking a package, etc., the mouse cursor starts spinning like it's busy, then the window dims to gray and becomes completely unresponsive. If I minimize it and do something else, it will usually unfreeze after about 45 seconds, until I click on something or type something again. Usually, it's fine once I reboot, but after awhile it starts to do it again. While this is happening, I opened up the system monitor and it said Synaptic CPU usage was 110%. There's no reason that this should occur on a 64-bit intel core 2 duo.

---

### Post by NightwishFan on 2010-10-07
Packages install quite quick here, though I do notice it takes long to start. Long as in longer than before. 5-6 seconds is not long. Note I am using the deadline scheduler. I will try CFQ.

---

### Post by MacUntu on 2010-10-07
Just used it the first time in this cycle:

Cold: it took around 15 seconds to show the window, followed by 20 seconds of 60% CPU usage, followed by an update-apt-xapian-index run - another 15 seconds high load. Warm: took around 5 seconds to show the window, rest see above.

I'm glad I don't need it.

> **mgunes said:**
> Your thread will attract less random off-topic posts this way.

My off-topic posts aren't random. :-\"

---

### Post by simpleblue on 2010-10-07
It takes a little over 20 seconds to load for me as well.

Once running it does fine.

---

### Post by L_V on 2010-10-07
Change log:

> apt-xapian-index (0.39ubuntu1) maverick;

  * debian/postinst:
    - when upgrading, ensure the index is fully rebuild (in the       background) to ensure that we get updated information in /var/lib/apt-xapian-index/{index.values} and that the index fully utilizes the new plugins 

 Thu, 23 Sep 2010

---

### Post by forcecore on 2010-10-07
it is slow as hell for deb installations too and do not warn if it pulls pointless libraries in, my friend told one day what the heck my system is much slower and when i checked something was pulled in KDE system libraries that occupied system resources. From now i always remove SC and use synaptic and gdebi.

---

### Post by NightwishFan on 2010-10-07
True it does not warn, but it complies with the correct Debian standards for package managing. It does the same thing as synaptic. Also, if you install a KDE program, it likely needs all those libraries unless you disable installing recommended packages and install it minimally.

---

### Post by L_V on 2010-10-08
Downgrading apt-xapian-index to V0.38 should improve.

---

### Post by sendblink23 on 2010-10-08
SC works pretty snappy for me on 4 of my computers (1 netbook, 1 regular laptop, 2 gaming desktops)

what kind of computer do you have?

---

