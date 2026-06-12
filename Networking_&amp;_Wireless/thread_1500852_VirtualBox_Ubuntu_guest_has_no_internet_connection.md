---
title: "VirtualBox Ubuntu guest has no internet connection"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by xefix on 2010-06-03
Hi, all

I'm new to VirtualBox and Linux, so I've run into a bit of trouble trying to set up an internet connection. My host is Windows XP, and my guest is Ubuntu 10.04. I am attempting to connect using NAT (I need simple internet access for browsing web pages and downloading/updating packages), though I have tried other types of connections and none have worked. I am using version 3.2.0 of VirtualBox, so a lot of instructions that I've found online don't apply to me because they are for slightly older versions. The official VirtualBox guide hasn't been helpful either because it says that NAT is supposed to work without any set up, but it doesn't, in my case. 
I don't really know what other information to provide - please let me know. Also, I know almost nothing when it comes to networks, so please be specific! Thank you!

---

### Post by Jeroensum on 2010-06-03
If you go to the Network settings for the VM, is the tickbox "Enable network adapter" ticked? If not, then tick it :)

If it has been ticked, open up the 'advanced' options by clicking the blue arrow and plz tell what the Adapter Type setting is set to. Also, check if the "Cable connected" tickbox has been ticked, if not, tick it!

---

### Post by xefix on 2010-06-04
Thank you, Jeroensum - it turned out to be a firewall issue at work, as VirtualBox was working just fine on the same laptop at home.

---

