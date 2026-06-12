---
title: "Need an idiot proof guide to setting up wireles  on an acer aspire one"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by Whodyacryem on 2009-02-06
Hey I'm 100% new to linux and its workings. Seriously I only installed it 5 minutes ago so don't assume I know anything (I dont). I have an Acer aspire one and I need to know how to get the wireless working (drivers, setting up the connection etc). I dont currently have a connection to the internet at all on the laptop in question so all files will be downloaded on this machine and transfered via USB stick.

Thank you for any help given.

---

### Post by basketcase on 2009-02-06
Does that have the realtek or ralink wifi card?  The best thing I ever did for my MSI Wind was replace the wifi card.

---

### Post by danni-la on 2009-02-06
this link has detailed instructions...

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

I however found the easiest way (via lan internet connection) was to install the backports

sudo aptitude install linux-backports-modules-intrepid-generic

this was the easiest and most reliable on my machine and so far no breaks. The madwifi drivers are supposed to be better but I couldn't get them to work on my machine.

Cheers Danni

---

### Post by superprash2003 on 2009-02-07
if you still have problems go to the terminal(Applications->Accessories->Terminal) and type **lshw -C network** and post output here ( copy and paste)..

---

