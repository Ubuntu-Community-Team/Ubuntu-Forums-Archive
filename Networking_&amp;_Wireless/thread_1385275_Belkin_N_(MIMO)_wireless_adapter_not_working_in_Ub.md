---
title: "Belkin N (MIMO) wireless adapter not working in Ubuntu 9.10"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by apple_head on 2010-01-19
Hey

I have just installed Ubuntu 9.10 alongside Windows 7 and it is not picking up my Belkin N wireless adapter?? So I went to go and download the Windows Wireless Drivers (ndiswrapper) software so I can install my adapter and the download center just says "Not available in the current data" and wont let me download it?

Also I tried to download my nVidia drivers from software center and it said the same thing? 

Never before have I had a problem with Ubuntu until now :(

So can anyone point me in any directions as to how to get these installed???

Many Thanks.

---

### Post by bkratz on 2010-01-19
I just checked and I can get ndiswrapper from synaptic, but you may have a different source selected. Anyway, you can get it this way also.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

By the way do you actually need ndiswrapper? If you post the output of 
lspci  (that is LSPCI in lowercase) perhaps there is an alternate method.



Edit: you might want to go to synaptic and select settings repositories and select a different download from source.

---

### Post by apple_head on 2010-01-19
Ok Thank you :) I'll give it a go.

I tried using synaptic but I can't seem to find any download link or search boxes (I'm a noob to Ubuntu :P ).

---

### Post by bkratz on 2010-01-19
> **apple_head said:**
> Ok Thank you :) I'll give it a go.

I tried using synaptic but I can't seem to find any download link or search boxes (I'm a noob to Ubuntu :P ).

When you bring up synaptic you should see a screen that says synaptic package manager at the top and buttons for reload--mark all upgrades and a drop down menu for settings.. The search box is called quick search at the top of the screen. Press reload .  Just type in (in the search box)
ndis and by the time you type that in it will find ndisgtk and two ndiswrapper files.  mark ndisgtk for installation. It will automatically load the other two files too. The setup screen in found under system>>Administration>>window wireless drivers

---

### Post by apple_head on 2010-01-19
> **bkratz said:**
> When you bring up synaptic you should see a screen that says synaptic package manager at the top and buttons for reload--mark all upgrades and a drop down menu for settings.. The search box is called quick search at the top of the screen. Press reload .  Just type in (in the search box)
ndis and by the time you type that in it will find ndisgtk and two ndiswrapper files.  mark ndisgtk for installation. It will automatically load the other two files too. The setup screen in found under system>>Administration>>window wireless drivers

Hi, Brilliant got them installed and working =D

Thank you for your help =)

---

### Post by bkratz on 2010-01-19
> **apple_head said:**
> Hi, Brilliant got them installed and working =D

Thank you for your help =)

Congratulations!  Please go to the thread tools and mark the thread as [solved] in case it helps someone else.

---

