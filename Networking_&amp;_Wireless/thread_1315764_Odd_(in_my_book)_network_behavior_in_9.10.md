---
title: "Odd (in my book) network behavior in 9.10"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by ST3ALTHPSYCH0 on 2009-11-05
Well, I thought that my upgrade to 9.10 had totally decimated my home network.... turns out that I was only partially right. 

First things first, machines in the network

My main pc:
Usually runs Win 7 Ultimate x64 ed
Dual boots Ubuntu 9.10 x64 ed
Shared HP printer
Password protect on filesharing off
toggled Firewall to zero effect

Family internet PC:
Running Ubuntu 9.10 x86 ed
Samba 4 installed and configured

Wife's work lappy:
running Vista home basic x86

Alright, while running Jaunty, I had full read/write access both directions between the family machine and the main machine. Upgraded to Karmic and couldn't see either from either.
Today I decided to start playing with this again. Installing SAMBA 4 instantly gave me full access to the family machine from my Win7 machine. However, I still couldn't see my windows network from my family box.
I changed workgroups on my main machine, and made a corresponding change on the family box. One reboot of windows later and I can now see my windows network(s for now, til the wife is off work for the day), but when I try to access the main computer it tells me "failed to retrieve share list from server". However, I can navigate directly to my shares by entering the address in the navigation bar in the file browser (i.e. smb://blair-pc/multimedia).
It seems obvious to me that the OSes are willing to play nice (mostly), but Win 7 is still on the fence about full sharing.

Hopefully, a few things that I found can help someone else, and hopefully someone else can help me finish fully configuring my network.

Thanks


*********************EDIT************************
Alright, I tried a reboot on the family box just in case.
I forgot one thing. I have to start out by going through the "connect to server dialog". I have to have the full path to one share entered, and when I first try to access it, the computer tells me that it couldn't mount it. However, if I select it then from the places menu,it opens right up and I can navigate to all shares by typing the path in the navigation bar as described above.

---

### Post by ST3ALTHPSYCH0 on 2009-11-09
Any networking gurus out there? (aka: bump)

---

