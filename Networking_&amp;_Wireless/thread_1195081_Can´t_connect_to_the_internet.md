---
title: "Can´t connect to the internet"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by Nanodaniel on 2009-06-23
I´m using wireless internet and it´s turned on but it doesn´t seem to detect anything. When I switch over to windows it connects fine. Someone told me that maybe I need a driver. I have an Hp Pavilion Notebook Zv6000. Does anyone know of any driver needed to connect that computer to the web?
Thanks and GOD bless!

---

### Post by jonobr on 2009-06-23
Hello 

[Here]("http://ubuntuforums.org/showthread.php?t=278233") is a search result I got for your setup showing a staff emeritus admitting defeat with this model of laptop.

However, he/she had a problem with the graphics and you did not mention that, so I dont think you will have the same problem.

COuld you post what type of wireless card you are using?

If its the broadcomm as seems to be reffered to in this post,
using b43-fwcutter from synaptic may get you going.

---

### Post by Nanodaniel on 2009-06-27
I've discovered That connecting directly with an Ethernet cable it runs perfectly. But it doesn't connect through the wireless as the wireless doesn't work because when I press my wireless button it doesn't turn on. So how do I turn on the wireless hardware so that Ubuntu recognises it? Do I need some kind of driver? Thanks for your last reply Thank-you in advance.
GOD bless

---

### Post by The Toxic Mite on 2009-06-27
Go to Applications > Accessories > Terminal, and type in the following command:

```
lshw -c network
```

Post the results when you're done. :)

---

### Post by philcamlin on 2009-06-27
what comes up when you type ifconfig :popcorn:

---

### Post by Nanodaniel on 2009-10-10
Thanks guys. It just started working one day after instaling some ubuntu updates. Sorry since the last time I wrote I had never gotten back on this thread. It didn't occur to me that  you would keep on giving advice. Sorry. As you see it's just my first cup of Ubuntu...

---

