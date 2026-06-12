---
title: "Please Help a Frustrated n00b on his AAO :("
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by naeeme on 2009-01-24
Hello there!

Recently, after seeing all the problems my mom had on her laptop due to Windows, I decided to make the switch to Ubuntu! :p

Anyways, I had to use Wubi because my Acer Aspire One does not have a CD drive.

Now, here is the problem: I turn on the laptop, select Ubuntu, blah blah, log on... And I don't have an internet connection! (I'm on another laptop right now). I click on the internet icon (the two screens) and...there is nothing. 

So, while searching these forums, it seems that Ubuntu isn't recognizing my wireless card. What I did was "sudo lshw -C network" and it said network UNCLAIMED and network DISABLED. However, my wireless is on! I also went ahead and did "lspci -v" and found out that my card is "Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)".

I did more snooping around and saw some things about madwifi-project and such. I did "wget http://snapshots.madwifi-project.org...tar.gz" but Ubuntu said that "Resolving snapshots.madwifi-project...failed: Name or service not known."

According to other things I have read, I have to download some things and then find them with Ubuntu and install them so that my wireless card can be detected. But I just don't grasp how to download if I don't even have internet on Ubuntu! I can download it on Windows, of course, but I still have not seen how to install something on Ubuntu if I downloaded it in Windows.

What am I missing here? I really want to get Ubuntu working :(

Thank you!

---

### Post by naeeme on 2009-01-24
By the way, I'm glad I found these forums and I hope to post more as I become better with Ubuntu!

So...hello! :)

---

### Post by naeeme on 2009-01-24
Okay so I tried putting ndiswrapper on a flash drive from the working laptop and when I put it into the Acer Aspire One it's not even detected. What do I do?

---

### Post by AlexBellisBrown on 2009-01-24
What make or model is the WIFI card?:)

---

### Post by naeeme on 2009-01-24
Hey Alex, thanks for your reply :)

The make or model is "Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)"

Is it possible to download the driver on Windows and retrieve it on Ubuntu? Or should I do it another way? Keep in mind that I have absolutely no internet on Ubuntu.

---

### Post by naeeme on 2009-01-24
Does anyone know the solution? I don't want to go back to Windows :(

---

### Post by naeeme on 2009-01-24
Beautiful!

I got it working connected with an ethernet cable to my router.
I'll follow some guides on here and if it doesn't work I'll be back in this thread :)

---

### Post by naeeme on 2009-01-24
Okay I'm getting extreeeeeeeeeeemely frustrated =/

I downloaded madwifi-0.9.4.tar.gz. It is on my desktop.
In order to install it I have to navigate through terminal, find where it is, and install it using some commands.

The problem is, I do "cd" in Terminal but it doesn't get me anywhere! How can I find madwifi, which is on my desktop, in Terminal?

I tried getting nautilus but this is what it gave me:

> sudo aptitude install nautilus-open-terminal

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "nautilus-open-terminal"
Couldn't find any package whose name or description matched "nautilus-open-terminal"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done



WHY!?!?

---

### Post by naeeme on 2009-01-25
Bumpy!

---

### Post by Quarg on 2009-01-25
I wouldn't use madwifi if I were you, It's a lot more hassle than it's worth. I just install the linux-modules-intrepid-generic package (something to that effect) and blacklist the ath_pci module, and it works fine, because it's using ath5k.

---

### Post by kevdog on 2009-01-25
I would recommend the ath5k module also, however I think it is in the backports repository.  This is the easiest way to get things up and running very quick -- no compiling or messing with source code (which is actually what I like to do -- but no one else does).

---

