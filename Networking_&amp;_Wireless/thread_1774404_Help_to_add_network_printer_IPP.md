---
title: "Help to add network printer IPP"
date: 2011-06-03
forum: Networking &amp; Wireless
---

### Post by X_Splinter on 2011-06-03
Hey guys I been searching in the internet and I cant find the solution to my problem.

So I have a HP office-jet Pro L7680 connected to the router, I download and installed the drivers (tested- working via USB)

Now I want to use it via Network (it works in all win computers) but I dont know how to config it.

Via router interface I can see the IPP address. 

Can anyone help out?

---

### Post by X_Splinter on 2011-06-03
I just found how to do it.

But It doesnt print corretly, It print a bunch of letters on the sides of the paper and nothing else

---

### Post by JKyleOKC on 2011-06-03
In your browser, use this link: [http://localhost:631](http://localhost:631) which will open the home page for your CUPS daemon. Ubuntu installs CUPS (Common Unix Printer System) by default, "localhost" always refers to your own machine, and CUPS listens on port 631.

On that page, select the "Add Printer" button. This will launch a wizard for you to follow, which includes all that's needed to install your network printer.

Once it's installed, you can use that same link to manage it as needed, similar to the "Printers" area of Windows. I've created a shortcut for it on all of my systems.

---

### Post by X_Splinter on 2011-06-03
JKyleOKC thanks for the info I didnt had to use it.

Since I got Ubuntu communication with the printer but had strange prints but I got do was in the properties of that printer in the Administration-Printing I change the "brand & model" I choose the printer model and selected the driver I had installed.

Now it is working 100%

[Solved]

---

