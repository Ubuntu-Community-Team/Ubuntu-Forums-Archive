---
title: "Help loading ndiswrapper"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by vbdad43 on 2010-01-05
New to Ubuntu (just loaded 9.10) and trying to install the NDIS wrapper so I can use my USB wirless adaptor. Executed the command 
 
sudo apt-get install ndiswrapper-utils-1.9 as read in one of the forums and received the following error: 
 
E: couldn't find package ndiswrapper-utils-1.9 
 
both the tar version and the “unzipped”version are on my desktop but I'm not sure they are installed and I don't know what to install. I've clicked every file in every folder most seem to be instructions not what I know as executables. Any help would be appreciated. I'm brand new to this so go easy on me.

---

### Post by bkratz on 2010-01-05
> **vbdad43 said:**
> New to Ubuntu (just loaded 9.10) and trying to install the NDIS wrapper so I can use my USB wirless adaptor. Executed the command 
 
sudo apt-get install ndiswrapper-utils-1.9 as read in one of the forums and received the following error: 
 
E: couldn't find package ndiswrapper-utils-1.9 
 
both the tar version and the &#8220;unzipped&#8221;version are on my desktop but I'm not sure they are installed and I don't know what to install. I've clicked every file in every folder most seem to be instructions not what I know as executables. Any help would be appreciated. I'm brand new to this so go easy on me.


If you have a wired connection the easiest way is to go to 
System>>Administration>>Synaptic Package manager   (password)
Hit reload then search (in the search box)for  

ndisgtk----tick it

It will automatically load the other dependencies (the ndiswrapper stuff) and provide you with a graphical interface under System>>Administration>Windows Wireless Drivers

---

