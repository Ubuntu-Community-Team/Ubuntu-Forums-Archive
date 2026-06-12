---
title: "I downloaded ndiswrapper so that I can try to get my trendnet tew-444ub wireless adap"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by IslanderSteve on 2010-04-17
I downloaded ndiswrapper so that I can try to get my trendnet tew-444ub wireless adapter to work with my windows xp through ubuntu with a dual boot. I would appreciate any help in setting up the ndiswrapper. I am stuck where it says to put in the tar zxvf ndiswrapper-version.tar.gz command.

---

### Post by bkratz on 2010-04-17
> **IslanderSteve said:**
> I downloaded ndiswrapper so that I can try to get my trendnet tew-444ub wireless adapter to work with my windows xp through ubuntu with a dual boot. I would appreciate any help in setting up the ndiswrapper. I am stuck where it says to put in the tar zxvf ndiswrapper-version.tar.gz command.

You do realize that ndiswrapper is available in synaptic, right? Just go to system>>administration>> Synaptic Package Manager and search for ndisgtk.  It is the front end for ndiswrapper and will automatically select all the appropriate files when downloaded ( there are two others).

After download go to System>>Administration>>Windows wireless drivers and select it.

The only reason to download the .tar file is if you want to build your own version for some particular reason.

---

### Post by nilbus on 2010-04-29
I didn't have to use ndiswrapper to get my TEW-624UB USB card working. 

This post got it working for me:
[http://ubuntuforums.org/showpost.php?p=8786509&postcount=16]("http://ubuntuforums.org/showpost.php?p=8786509&postcount=16")

---

