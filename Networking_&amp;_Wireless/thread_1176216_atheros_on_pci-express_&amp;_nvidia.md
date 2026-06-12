---
title: "atheros on pci-express &amp; nvidia"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by maciejso on 2009-06-02
If someone called me a novice, when it comes to linux, I'd probably get offened, but after struggling for xxx hours with atheros and nvidia I think I really am, even though I've been using linux for a few years.
I need your help linux gurus, otherwise I'll get mad.

The hardware I'm struggling with is:
     1.Wireless card with an Atheros chipset, 
       AR242x 802.11abg Wireless PCI Express
     2.Graphics card, NVidia
       nVidia Corporation NV44A [GeForce 6200] (rev a1)

I can get them working seperately with no problem at all, I mean if I swap the graphic card or if I get rid of the wireles card, but in this particular combination the latter is not working what drives me mad, particularly as I'm a big fan of both linux and open source software.
I've spent an incredible number of hours on investigating this issue with no results, so please help.
I have to add that graphic card works properly, but I'm only having issues with wirelesss card when I'm using this graphic card.

I've tried all sorts of madwifi,ath5k, ath9k drivers but they all generate the same errors(see below).

For some reason the output of dmesg / lspci / iwconfig  generates too many smiles(!) and I was not allowed to post them as they were, so I decided to attach these outputs as files, forgive me that.
Cheers

---

### Post by t0mppa on 2009-06-02
There's a checkbox on the post message screen where you can disable smilies. Beats me why there has to be so many of them enabled by default, since they often get in your way. Anyway, you can use [code] tags to get past the issue and also avoid posting a very long message by getting a text box with a scroll bar on it for the lengthy outputs like dmesg.

A quick search finds quite a few other reports of this problem without any fixes offered. Should probably go file a bug report about it or hype up one, if it already exists. Unless of course, someone finally has a fix for this.

---

