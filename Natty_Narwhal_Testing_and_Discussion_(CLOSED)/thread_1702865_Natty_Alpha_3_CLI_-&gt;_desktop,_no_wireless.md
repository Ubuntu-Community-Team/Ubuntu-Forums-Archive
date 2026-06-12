---
title: "Natty Alpha 3 CLI -&gt; desktop, no wireless"
date: 2011-03-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by gmargo on 2011-03-08
I used the Natty Alpha 3 Alternate i386 disk to install Natty to a new partition on my laptop.  

I installed the CLI version first.  Then installed the "ubuntu-desktop" package from the working CLI installation.  Every part of the installation went fine, except the wireless interface seems to be ignored.

This laptop runs Maverick in another partition, including wireless, just fine.

Why didn't installing "ubuntu-desktop" get the wireless working?
What package would I have to install/reinstall to get wireless working?

---

### Post by cariboo on 2011-03-08
Have you get the proper drivers loaded for your device? It would help if you gave us more info eg: make/model of wireless device.

---

### Post by meeso2k on 2011-03-09
Edit: Linux meeso-hp 2.6.38-5-generic #32-Ubuntu SMP Tue Feb 22 16:10:15 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


I am having the same issue, however I did not install via the CLI, but through the actual Alpha 3 ISO. 

Using the Broadcom STA Wireless Driver which was detected through the "Additional Drivers" application. 

Switching the kill switch to on/off on the laptop does not do anything nor does dmesg pick up anything. (On 10.10 it gives output that the kill switch press was detected)

03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

 *-network UNCLAIMED
             description: Network controller
             product: BCM4311 802.11b/g WLAN
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:03:00.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
             resources: memory:b8000000-b8003fff

---

### Post by cariboo on 2011-03-09
Try the instructions [here]("http://ubuntuforums.org/showthread.php?t=571188"), they've worked for me several times, especially with unclaimed issues.

---

### Post by gmargo on 2011-03-12
I'm still wondering how the wireless gets detected and set up for 
the NetworkManager to use. 

I'm defining "wireless works" as meaning "Network Manager icon shows
up in toolbar and detects my (and the neighbors') wireless networks".

I've done some more research; I now have 4 Natty Alpha 3 (+updates) installs:

```

#1: Alternate CD, CLI install,      then ubuntu-desktop -> no wireless
#2: Desktop CD,   standard install                      -> wireless works!
#3: Server CD,    standard install, then ubuntu-desktop -> no wireless
#4: Alternate CD, standard install                      -> wireless works!

```Note in particular the two Alternate CD results:  wireless works for one but not the other.

What bit of software causes that Network Manager icon to be present?

---

### Post by gmargo on 2011-03-12
I figured out something very important.  On those two installations where I got no Network Manager icon: it seems the Network Manager is running, but the icon itself is **invisible**!

I only found it by accident.  I was mousing (after a click) over everything in the tool bar to see all the pull-down menus, from right to left.  The Bluetooth icon was the left most, but when I moved the cursor to the left of that, the Network Manager menu showed up!  No Network Manager icon was visible on the toolbar at all.  After configuring the wireless, then the icon shows up as expected.

So why does the Network Manager sometimes put up an invisible icon?

Update: After the wireless is working, and then I disconnect, then the icon goes invisible again.

---

### Post by ClientAlive on 2011-03-22
Sincere appologies if I'm posting in the wrong thread. I'm fairly new here and since my situation involves Natty Alpha 3 I wasn't sure whether to post in a forum about my problem (there isn't much talk about Natty around here - that I've seen) or to post in a forum about Natty. Can someone please offer me some direction or re-direction, whatever the case may be?

I'm on a HP Pavilion ze2000 laptop (about 5 years old). I had a lot of trouble trying to install linux on this machine (went through 4 other distros before landing on Natty). Now I am running Natty live until I can at least connect to my router wirelessly with success. Also I'm only about 3 hours old working on linux now (I've never used it before tonight in my life and I just got this thing working with it).

I managed to find network connections, got it opened up, and called my isp to get information to configure my wireless. Those guys down there really don't have any experience with linux, I'm far from an expert in configuring network stuff, and (at first glance) linux seems to have a lot more to the network configuration than windows. (Lets just say it seems different).

So I managed to get my isp to send me an email with a butload of info on my router, settings, etc, etc, All the stuff I guy could possibly need - but: I need some guidance in putting the right pieces of information in the right places and any other tricky things a person who's never used linux before with this might need to know.

Thanks so very much for any help.

Sincerely,
Jake
):P

-------------------------------------

Gotta hit the sack right now then work in the morning. I'll be back before this time tomorrow though.

Thanks

---

### Post by cariboo on 2011-03-23
An alpha version is really not the way to learn how to use Ubuntu, it will sometimes break if you look at it the wrong way. I'd really suggest you try either 10.04 which is a long term support version, or 10.10, which is the latest release.

That being said, we really need to know what wireless chipset, your system uses. If you don't know, open a terminal, just click the applications icon (the one with the scissors and the triangle) and type ter in the search box if you are using Unity, or click the Ubuntu logo in the top left corner and Select Accessories->Terminal  if you are using the Classic Desktop and type:

```
lspci > hardware.txt
```

the above command will create a text file called hardware.txt, that you can transfer to a system with a working network connection. Paste the resulting file in your next post.

---

### Post by ClientAlive on 2011-03-23
Following is a a list of the distros I tried that wouldn't install and on two different computers before I cane to Ubuntu 11.04. I'll finish with what my chipset is and a link.
 
I have two machines, both HP, both Pavilion. One is a desktop and it is an a1253w, the other is the laptop I'm on and it's a ze2000. I started trying to install linux on the desktop, ultimately without success. It is curretnly without os. (I'll prob reload window on it later this afternoon - for the time being).
 
Here is a my installation history with these machines in order (everything listed would be the latest stable version):
 
The Pavilion a1253w (desktop)
 
xubuntu (install failed)
openSuSe (install failed)
ubuntu desktop 10.10 (install failed)
ubuntu netbook remix 10.10 (install failed)
 
The ze2000 (laptop)
 
ubuntu netbook remix 10.10 (live failed)
natty alpha 3 (live successful but buggy)
 
I can't tell you what the chipset is on my desktop but the chipset on this machine is 855gm.
 
Here is a link to my recent (previous) post on this forum that show what was discussed and how I arrived at this point.
 
[http://ubuntuforums.org/showthread.php?t=1711247](http://ubuntuforums.org/showthread.php?t=1711247)
 
The long and short of it is that Natty is the only thing so far that I have found that will just run on 'this' machine without some kind of painful workaround.
 
I can handle buggy for a couple mos as long as its nothing too serious.
 
What I would prefer to do at this point is to try and go ahead with Natty first; then, if that doesn't work, I'll go back to netbook 10.10 and try to do the workaround to get it to finish loading live setup and ultimately install.
 
What I would like to do next is (with Natty) make sure I have the wireless configured correctly and see what happens then. If that doesn't work I'd like to look for some simple tweak or way to get it to work. Then go from there.
 
Sound ok guys?
 
Thanks
Jake
 
------------------------
 
My router is a SMC Networks
Model Name: SMCD3GN
Software Version: 1.4.0.40-RES
Hardware Version: 1B
 
So far I've filled in a total of 6 fields under 2 tabs:
 
Under the first tab, "Wireless"
 
SSID (entered in)
Mode "Infrastructure"
Device MAC address (entered in)
MTU "Automatic"
 
Under the second tab, "Wireless Security"
 
Security "WPA & WPA2 Personal"
Password (entered in)
 
Is that the correct things to be entering? Is there something else I need to do after creating the account in order to enable it?
 
Also: this computer has a wireless button on it which can be turned on or off but I'm not sure it works in Ubuntu. I tried it and got the pop up about proprietary drivers (I don't think that's the exact words but that's what it was talking about). When I went to the app: "add additional drivers" though it didn't give me any option to dl any driver.
 
I also went to an app called "sytem test" and made it run a test on just the wireless connection (unchecked all the selections except the one for wireless under network). I've attached a picture of its result.
 
Can anyone please guide me on this? Much appreciation. Thanks in advance.

---

### Post by ClientAlive on 2011-03-25
cariboo907 sorry about the confusion with posting. I'm working on it right now and will get all the info you need. I see you posted in my thread under Networking and Wireless. I will go and stay there. I'm learning and won't make these same posting mistakes in the future. Thank you for your patience.
 
For convenience (if it helps) here is the link to that thread in Networking and Wireless: [http://ubuntuforums.org/showthread.php?t=1713085](http://ubuntuforums.org/showthread.php?t=1713085)
 
Sincerly,
Jake
:)

---

