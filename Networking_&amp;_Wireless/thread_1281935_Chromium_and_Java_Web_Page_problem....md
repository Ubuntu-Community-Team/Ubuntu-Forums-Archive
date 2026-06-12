---
title: "Chromium and Java Web Page problem..."
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by vickoxy on 2009-10-03
Hi,
i just installed chromium 4.0.221.3 -Ubuntu build 27948- but have problem with my java based bank site-after login to my account, all i get is white screen.

Of course i have java installed.

Anyone knows if there is fix for this?

---

### Post by kreggz on 2009-10-03
I am failry sure Chromimum doesn't support Java yet. 

[http://code.google.com/p/chromium/issues/detail?id=5](http://code.google.com/p/chromium/issues/detail?id=5)

---

### Post by vickoxy on 2009-10-03
Well, hope they will fix it-really fast browser...

---

### Post by kreggz on 2009-10-03
You could always try Google Chrome Beta for Linux, not sure if Java works on that though.

[http://www.google.com/chrome](http://www.google.com/chrome)

---

### Post by vickoxy on 2009-10-03
> **kreggz said:**
> You could always try Google Chrome Beta for Linux, not sure if Java works on that though.

[http://www.google.com/chrome](http://www.google.com/chrome)

Unfortunately i can not download from that site anything...

---

### Post by giarca on 2009-10-04
Install sun-java6-plugin package through Synaptic and restart Chromium.

---

### Post by tuxxy on 2009-10-04
You may need to edit the command used to start chromium or enter this in terminal
```

chromium-browser --enable-plugins
```

---

### Post by renkinjutsu on 2009-10-04
> **vickoxy said:**
> Unfortunately i can not download from that site anything...

Google has their own repository set up for Ubuntu

[http://www.google.com/linuxrepositories/apt.html]("http://www.google.com/linuxrepositories/apt.html")


chrome is in the repository somewhere

---

### Post by darco on 2009-10-04
Java works just fine in Chromium....

---

### Post by vickoxy on 2009-10-05
> **giarca said:**
> Install sun-java6-plugin package through Synaptic and restart Chromium.

I have that installed-used it for firefox, but my e-banking site could not be open.

---

### Post by vickoxy on 2009-10-05
> **renkinjutsu said:**
> Google has their own repository set up for Ubuntu

[http://www.google.com/linuxrepositories/apt.html]("http://www.google.com/linuxrepositories/apt.html")


chrome is in the repository somewhere

Well, i use their daily ppa versions:

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/) jaunty main 
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/) jaunty main 

So, i think i could be just all right to have all work.

Still, as said, my e-banking java site could not open...just blank page...

---

### Post by vickoxy on 2009-10-05
> **tuxxy said:**
> You may need to edit the command used to start chromium or enter this in terminal
```

chromium-browser --enable-plugins
```

I have it also done-but nothing.
Flash is working perfectly, but only java/or some java pages are problem... i can open page for e-banking, i can login but that there is blank page...

---

### Post by thecow on 2009-10-05
What banking site do you use?

---

### Post by vickoxy on 2009-10-05
[www.netbanking.at](www.netbanking.at)

So, i tested java at javatester.org and it shows proper version 1.6. So, my bankking site is opening, and i can login, but after that -blank. So, i think it is sort of bug in java, because if it wouldn´t be installed, i couldn´t open login page.

---

### Post by thecow on 2009-10-05
Have you run this:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts


?

---

### Post by thecow on 2009-10-05
> **vickoxy said:**
> [www.netbanking.at](www.netbanking.at)

So, i tested java at javatester.org and it shows proper version 1.6. So, my bankking site is opening, and i can login, but after that -blank. So, i think it is sort of bug in java, because if it wouldn´t be installed, i couldn´t open login page.
Ah i was going to see if the bank website would let me test out their online software to see if it works on my computer.  However I dont speak the language and it seems like they dont even have that

---

### Post by vickoxy on 2009-10-05
I am missing only sun-java6-fonts-trying to install it but the synaptic is slow-post it later.

Thanks

---

### Post by vickoxy on 2009-10-05
> **thecow said:**
> Ah i was going to see if the bank website would let me test out their online software to see if it works on my computer.  However I dont speak the language and it seems like they dont even have that

They have english version of site ([https://www.sparkasse.at/sPortal/sportal.portal?_nfpb=true&_urlType=action&LABEL_HEADER_sh=facf7fc745ebd754042a2083be610f6c&LABEL_HEADER_zz=3633.413492824656&LABEL_HEADER_pc=1&cci=Channels/netbanking/0netbanking_start_pg_SuperSize.akp&desk=sparkasseat_de_0009&navigationId=nav_gd_netbanking.xml&&popup_w_webc_url=Channels/netbanking/0netbanking_start_EN_pg_SuperSize.akp&popup_desk=sparkasseat_de_0008&otherPopup=1&_windowLabel=LABEL_POPUP_1](https://www.sparkasse.at/sPortal/sportal.portal?_nfpb=true&_urlType=action&LABEL_HEADER_sh=facf7fc745ebd754042a2083be610f6c&LABEL_HEADER_zz=3633.413492824656&LABEL_HEADER_pc=1&cci=Channels/netbanking/0netbanking_start_pg_SuperSize.akp&desk=sparkasseat_de_0009&navigationId=nav_gd_netbanking.xml&&popup_w_webc_url=Channels/netbanking/0netbanking_start_EN_pg_SuperSize.akp&popup_desk=sparkasseat_de_0008&otherPopup=1&_windowLabel=LABEL_POPUP_1)), but to try software-i do not know

I installed java-fonts, but still nothing. Just blank page...

---

### Post by vickoxy on 2009-10-05
And of course-java is working normal under firefox, opera or epiphany

---

### Post by giarca on 2009-10-05
Check in about:plugins if the java plugin is loaded. If loaded the problem is not Chromium doesn't load the plugin but my java6.15 plugin doesn't open my bank applet. So you can open another thread Java related.

---

### Post by vickoxy on 2009-10-05
> **giarca said:**
> Check in about:plugins if the java plugin is loaded. If loaded the problem is not Chromium doesn't load the plugin but my java6.15 plugin doesn't open my bank applet. So you can open another thread Java related.

Thanks!

---

### Post by anjames on 2010-09-12
So... it says solved, but I didn't see any working solution?

I have the same problem using the costco photo center uploader just showing a blank pane where the applet should be.

Javatester.org shows that I have the latest 1.6.0_20 applet loaded, and so does about:plugins, and I have all of the packages listed above:

```
$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
sun-java6-fonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Hopefully I can get this fixed, otherwise I'll never be able to send my poor old grandma some vacation photos!

...edit...

After killing all my browsers and restarting them, it works suddenly! Looks like the java runtime needs everything closed to plug in. Who knew?

My grandma will be happy now. :-)

---

### Post by birkopf on 2011-02-24
If I can help - there is something I noticed. I was sure that JAVA isn't working on Chromium as well, but it does!

Install Java
Install icedtea plugin

It works. Only issue is the YOU DONT SEE IT LOADING. When you go to java applet or website just give it a minute or two and it will load! Chromium doesn't show anything in the place of java applet when not loaded or when loading...

---

