---
title: "Ubuntu studio internet"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by PsychoElixir on 2010-09-19
I'll start off the bat by saying that I'm new to Ubuntu.

My computer is a brand new HP G62 that originally came with windows 7. A couple of days ago I installed Ubuntu onto my computer because I've played with it in the past and liked it, but then I heard about Ubuntu studio and I do a lot of audio recording so I reformatted my PC and installed that.

When I had regular Ubuntu I didn't have an issue with my internet, but now that I have Studios I cant even figure out how to access the network. I've been looking through other people who have posted but nothing that seems to help me. 

I tried to go to terminal and type network-manager-gnome and it does nothing for me..somebody please help

I should probably mention that I installed studios 10.4

That isn't my only problem by the way...but obviously the most important.

---

### Post by bkratz on 2010-09-19
Ubuntu Studio doesn't have network manager installed by default, as copied from this page

[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

quote
Ubuntu Studio Network Setup - Wireless connections and network manager are left out of the OS in Ubuntu Studio. This is intentional as it can interfere with audio processing. Support can be added from the Install DVD or synaptic.

---

### Post by PsychoElixir on 2010-09-19
My problem is that when I type in the terminal:

sudo apt-get install network-manager network-manager-gnome

it tells me that no such location exists...and network-manager is not listed in synaptic..so from the steps provided in that link, I cant even finish step one

---

### Post by bkratz on 2010-09-19
> **PsychoElixir said:**
> My problem is that when I type in the terminal:

sudo apt-get install network-manager network-manager-gnome

it tells me that no such location exists...and network-manager is not listed in synaptic..so from the steps provided in that link, I cant even finish step one

Sorry, I run 9.04 (because of intel video) and in that version I just checked and both show up in synaptic. I'll hook up my 10.04 and try there to see.

---

### Post by PsychoElixir on 2010-09-19
Thanks and sorry for the trouble...I'm installing a separate partition for regular Ubuntu so worst comes to worst I'll just use studio when i need to..however I would much rather figure out my network dilemma

---

### Post by bkratz on 2010-09-19
> **PsychoElixir said:**
> Thanks and sorry for the trouble...I'm installing a separate partition for regular Ubuntu so worst comes to worst I'll just use studio when i need to..however I would much rather figure out my network dilemma



After I hooked up my 10.04 version, I did a search for network
and found both there. See attachments ( if I did it right!)

---

### Post by PsychoElixir on 2010-09-19
that boggles my mind...would you have any idea why i wouldn't have it? I have it in my head (and I'm probably dead wrong) that I rather downloaded it wrong (which isn't likely) or I installed it wrong.

---

### Post by bkratz on 2010-09-19
No I have no idea--that is of course assuming  you have a working wired internet connection.

---

### Post by PsychoElixir on 2010-09-19
Wired Ethernet doesn't work neither. Both wired and wireless work on regular ubuntu

---

### Post by cchhrriiss121212 on 2010-09-20
If you have no internet connection then you will not be able to download anything, or view available packages. You can however, install network manager form the studio DVD:
[https://help.ubuntu.com/community/UbuntuStudioNetworkSetup](https://help.ubuntu.com/community/UbuntuStudioNetworkSetup)

---

### Post by poodoopealeoaph on 2010-10-01
I worked through all of the stuff on the page that the last person just posted but it didn't seem to work out. I have the network icon up but it just says "network-manager isn't running" i have all of the necessary drivers installed. I just need to figure out if there is some sort of code I need to run in terminal to get network-manager to run

---

### Post by poodoopealeoaph on 2010-10-01
wow, stupid me... I restarted my comp and it all connected up. thanks for the posts anyway. Would have never figured anything out without this post.

---

