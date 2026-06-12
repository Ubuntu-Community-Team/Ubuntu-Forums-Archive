---
title: "Thinkpad T30 can't connect with Internet"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by emeraldgirl08 on 2009-04-20
Hi. I installed 8.10 today in my IBM Thinkpad T30 and can't hook up to my wireless router. The wireless card will detect the router but I cannot hook up to it. I've gone to edit and entered in the password but it still won't log me on.

This is the type of card I have.

Cisco 350 Series Mini PCI
Device class: Net
Device description: Cisco Systems PCI Wireless LAN Adapter
Driver provider: Cisco
Driver date: 5-4-2004
Driver version: 3.8.26.0
Device status: Enabled

I hope someone who has had experience with cisco wireless and T30's can help me out!

---

### Post by Brewfreak on 2009-04-20
Hello emeraldgirl08:

Have you tried connecting via wire to your wireless router?  And if so, have you verified that you have the latest drivers?  You might need proprietary drivers installed.  After you have done a system update (<system><administration><update manager>)while connected via wire, check in <system><administration><hardware drivers> to see if you have any proprietary drivers installed.  Once this is done you should be able to connect via the wireless card by right click on the network icon on the panel bar and selecting enable wireless.  After this everything should work and the system should prompt for your ssid and passphrase etc.  Let me know if this works.  Good luck!
BTW, I have a t30 ubuntu 8.10 with a cisco wireless card and it works just fine.

---

### Post by emeraldgirl08 on 2009-04-20
Brewfreak.

I'm just waiting for my lil' brother to get done playing his Wolfenstein then I'm going to do updates with the cable! I kinda figured that I'd have to do a bunch of updates but wasn't 100% sure. 

You got a T30 too??? Is there a good site that can tell me how to jazz up my Linux and make it kick Windows Heinee??!!!

:D

Thank you!

---

### Post by Brewfreak on 2009-04-20
Emeraldgirl08:

You already are kicking windows a## with plain old ubuntu.  I haven't done any jazzing up of my system.  I use it for work to connect to an AS400 and a work exchange mail server but roam around the synaptic package manager to see all the goodies available for the low low price of nada! There is also google search for any particular needs you may have.  Enjoy!

---

### Post by emeraldgirl08 on 2009-04-21
This OS is a true test of patience... or luck.

I downloaded 275.4 MB of updates!

:shock:

I did all that and forgot to follow your directions for proprietary drivers! I do remember seeing something under that tab but it told me there were none. Now that I'm back on Windows I can't just go back and fix this! 

Someone else is using the ethernet cable (yeah we only have one :P) I tried looking but couldn't find one laying around the house. I'll do this proprietary stuff tomorrow. I do have one other thing. Why is there two versions of 8.10 at boot? There is one that is 8.10 2.6.27.11 and 8.10 2.6.27.7. Which one is the latest? Thanks.

---

### Post by emeraldgirl08 on 2009-04-21
I'm a total NOOB!

I'm really about to throw the proverbial towel in! I could either keep posting my exploits with this and hope it solves other T30/Cisco aironet 350 mini-PCI user maladies or go back to Windows. 

I'm going to keep at it.

This is a link to a post that is for older versions of Ubuntu and I would have thought they would have fixed this bug by now.

[Cisco Aironet Problems]("http://ubuntuforums.org/showthread.php?t=417254")

This stuff is from two years ago!!! With all the brainiacs involved in making this a community effort- Why has no one been able to post easy to follow directions for this??!!!

I realize people are busy but if anyone can PM me or anything to guide me through this I'd appreciate it very much.

Thank you.

---

### Post by chili555 on 2009-04-21
There are two versions at boot because your system has two different kernels installed; the original off the CD and one that you got in all those updates. This mechanism is very useful because if you install an updated kernel and something doesn't work correctly, you can boot into the older kernel and troubleshoot. I have a T40 laptop with about ***six*** kernels on it! If you are a developer, it has other uses as well.

Your Aironet is supposed to work with a driver module named *airo*. First, let's run a terminal command that will tell us if it's loaded and your card is ready to run.```
sudo lshw -C network
```The output will show your ethernet and wireless data, including drivers.

The reason there is no newer Aironet guides on the 'net is that there aren't many cards left in use, since they don't do 802.11g nor n and, depending on the firmware, can't use WPA encryption. Even mine is on the shelf, having been replaced by a more modern card.

Post the output from this command and we'll get you going.

---

### Post by emeraldgirl08 on 2009-04-21
Chili. 

Thank you. I am going to log off of Windows and restart. I'll be back with that info in a little bit.

---

### Post by emeraldgirl08 on 2009-04-21
**Okay. This is what I got.**   
[SIZE="2"]
[I]*-network:0 DISABLED    
description: Wireless interface
  product: Cisco Aironet Wireless 802.11b      
    vendor: AIRONET Wireless Communications
   physical id: 2    
bus info: pci@0000:02:02.0
logical name: eth1   
 version: 00      
serial: 00:02:4a:8f:34:54
width: 32 bits      
clock: 33MHz
capabilities: pm vpd bus_master cap_list ethernet physical wireless logical       
configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 module=airo multicast=yes wireless=IEEE 802.11-DS[/I][/SIZE]

       **And then it goes on to show my ethernet properties there. Does that shed any light on my dilemma?**

---

### Post by chili555 on 2009-04-21
Yes, it tells us that your wireless is happy and healthy. So now let's look at the connection difficulty. You click the Network Manager icon and you see your router and are you asked for any encryption details? WEP, WPA, Klingon? Is there encryption set up on your router?

Hmmm...I don't like this at all:> *-network:0 DISABLED Is the wireless key combination, Fn+F5, perhaps toggled off? Please let us see:```
sudo cat /var/log/messages | grep -i kill
```Thanks.

---

### Post by emeraldgirl08 on 2009-04-21
Chili. These are screenshots taken from Ibex. 

[[COLOR="Blue"]Pic 1[/COLOR]]("http://i209.photobucket.com/albums/bb101/msprinnydancer/Misc%20Pics/wirelessnetworkshows-1.jpg")

This shows that I am getting a wireless signal.

[[COLOR="Blue"]Pic 2[/COLOR]]("http://i209.photobucket.com/albums/bb101/msprinnydancer/Misc%20Pics/Screenshot-WirelessNetworkAuthentic.jpg")

And this shows what happens when I click on the wireless tab. Note how the connect and option to change wireless security is grayed out???

I've gone to properties and tried to edit it but am confused and think that if it was meant to work- it would have worked as soon as I logged on to Ibex. This would mean the problem is in the realm of software programming... right?

I'll run that terminal and bb in a little bit. 

And yes we have WPA-PSK encryption. From what I read this is a problem and if so how could I remedy this?

---

### Post by Brewfreak on 2009-04-21
Emeraldgirl08:

You can fix your encryption compatibilities by logging in to your wireless router and reconfiguring the encryption so that your router uses wep 128 hex encryption.  It might be less secure and you have to redistribute the key to all users so they can reconfigure their respective wireless defaults.  While you are at it enable the 802.11 a/b/g wireless compatibility in your router.  Good Luck!

---

### Post by emeraldgirl08 on 2009-04-21
**Re: Chili**

I wasn't aware that I could toggle wireless on and off with Fn & F5.

I termed your command and got this:

[invalid option]("http://i209.photobucket.com/albums/bb101/msprinnydancer/Misc%20Pics/Screenshot.jpg")

I'm a newbie so I wasn't sure how to type in the (I) pipe symbol between the 'messages' and 'grep' part.

What exactly is this command going to bring up?

---

### Post by chili555 on 2009-04-21
> I wasn't aware that I could toggle wireless on and off with Fn & F5.It may not be Fn+F5; it may be some other combination or a physical switch. In rare cases, the wireless is always on.> What exactly is this command going to bring up? The command is going to bring up kernel messages, but limited to those relating to 'kill switch' or 'rfkill.' The presence, or especially absence of any such messages will tell us a lot.> I'm a newbie so I wasn't sure how to type in the (I) pipe symbol between the 'messages' and 'grep' part.The pipe symbol is over on the right on the same key with \. It may look like two vertical lines, but it types out as |.

---

### Post by emeraldgirl08 on 2009-04-22
:)

I got the wireless working!

It came with a sacrifice tho. I had to lose the WPA-PSK and switch my router to WEP. 

It's dismaying to use a less secure connection- period!

Other than that I plan on changing out my mini-PCI card for a WPS-PSK compatible one. Preferably with g networking instead of b only :)

Hope this helps out someone!

:KS

---

### Post by chili555 on 2009-04-22
> I plan on changing out my mini-PCI cardPlease check this before you swap out that card: [http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card](http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card)

Please notice that the T30 is an affected model.

---

