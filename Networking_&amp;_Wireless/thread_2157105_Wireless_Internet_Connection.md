---
title: "Wireless Internet Connection"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by pdg1986 on 2013-06-24
Dear friends,

I have recently installed Ubuntu 13.04 on my Asus K53 Laptop. However I was unable to install my internet driver. I am from India and using Reliance Netconnect. The install.sh script is showing error "Can not continue without qt3 runtime library". I am unable to install the same without internet. In this regard if you could point to me how I can download those packages alongwith dependencies offline (if at all possible) and install them manually, I'd be very much grateful, otherwise I will have to say goodbye to using Linux on my laptop. 
Also if I use KDE Linux distros, like Opensuse, Kubuntu, etc. will this problem still arise? 

Regards

---

### Post by praseodym on 2013-06-24
Hi,

please check these outputs:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
```

---

### Post by pdg1986 on 2013-06-24
> **praseodym said:**
> Hi,

please check these outputs:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
```

I'm sorry I can't do that as I uninstalled my Linux install. I want to be able to fully be able to use it before I can continue again. 
I have been able to mount my device and it is detecting and I can even access the folder to install the device driver, however it requires the aforementioned details.

Regards

---

### Post by Bucky Ball on 2013-06-24
So do you still want help with this issue or not? If no I shall close the thread. Thanks. ;)

---

### Post by pdg1986 on 2013-06-24
> **Bucky Ball said:**
> So do you still want help with this issue or not? If no I shall close the thread. Thanks. ;)

The fact that I registered to the forum and posted this topic should answer your question, the rest is your decision. Thanks for the warm hospitality so far. :)

---

### Post by wildmanne39 on 2013-06-24
Hi, you can run the commands from the livecd or liveusb, but anything you do will be gone when you reboot.

In almost all cases we can get the wireless to work but it is best after you have installed ubuntu.
Thanks

---

### Post by Elfy on 2013-06-24
> I'm sorry I can't do that as I uninstalled my Linux install. 

It's going to be hard for anyone to help you if you've not got a linux install ;)

Once you've got it reinstalled, run the commands and post the output .

As far as downloading packages offline that's not going to be possible - but you can get them from outside an install. 

You can get packages from here as necessary - [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You might also like to have a look here - I've seen similar issues here in the past - I did a quick search on an 'ubuntu' search engine that I use - [http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=reliance+netconnect#gsc.tab=0&gsc.q=reliance%20netconnect&gsc.page=1](http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=reliance+netconnect#gsc.tab=0&gsc.q=reliance%20netconnect&gsc.page=1)

---

### Post by Bucky Ball on 2013-06-24
> **Elfy said:**
> It's going to be hard for anyone to help you if you've not got a linux install ;)



This what I meant. Was wondering if you still want help as you don't have Ubuntu installed. ;)

---

### Post by AguNnamdi on 2013-08-02
It is actually easy to set up.(in ubuntu)
1. Go to Network Connectiions
2. Click Add
3. Choose which VPN is applicable to you(mine is mobile broadband as  I am using internet modem from my service provider).
4. Click on create.
5. Get your 'Broadband provider's name','billing' etc from your service provider-mine is ZTE WCDMA Technologies MSM and continue
6. Choose your country and click continue.
7. Choose your provider from the list.
8. Choose your billing plan.(check the pack of the product you purchased,normally contained  there).Or go to windows and look at your service providers interface  'network settings' for these information)
9.Create your network.
10. Insert your modem and look at the top of your desktop(connections tab), you should see your newly created network(suffixed with '1').Click on it to connect.
11. Enjoy your browsing...

---

### Post by igodspeed on 2013-08-17
This does not seem to work with reliance netconnect. Can you confirm it worked for you.

---

### Post by Bucky Ball on 2013-08-18
@CharlieFP: Your visit has been cut short, so good you were going anyway. Here's hoping you have the civility not to hijack threads on your next forum and actually bother to ask for help with your problems rather than simply vent your frustration. 

You have one post on these forums and you complain. You've never even attempted to ask the community for help or stated you have an issue until now. That's what we're here for, to help, not for you to hijack threads, complain and generally be a pain. Understand your frustration but you could have just asked for help. Bye for now. ;)

PS: If you have an issue you want help with, then come back after you cool off. Ten days should do it. I have issued an infraction reflecting this for insulting staff with your senseless comment regarding my post. (Incidentally, further profanity will get you ejected permanently). If you have an issue with this infraction, please post in the ***Resolution Centre***, but you will need to wait until your infraction is over.

Thanks,
BB

* [QUOTE=CharlieFP] I abhor the idea of putting more money in Gates' pocket, but you give me no choice...[/QUOTE] 

Non-sensical and borne of frustration. You haven't asked for help, had nothing to do with the community til now and we give you no choice??? You've always got choice and you chose to wade through pages of information you didn't understand about a new OS with no help whatever then get on here to complain it is the forum community's or Linux or Ubuntu's fault somehow that you haven't been able to get your modem working. Truly bizarre.

---

