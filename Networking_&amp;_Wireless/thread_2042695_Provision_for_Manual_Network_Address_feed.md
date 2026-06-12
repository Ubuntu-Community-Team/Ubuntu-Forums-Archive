---
title: "Provision for Manual Network Address feed"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by srinifritter on 2012-08-15
Hello,
     I was earlier having a problem with my system getting connected with network either wired or wireless mode. I generally use Windows but due to my project and other needs I use Linux Ubuntu 11.04. 
     Recently, I encountered a problem all of a sudden when I noticed my system wouldn't connect with the ethernet for no reason. There was no alert or anything as such. I with the help of my friend finally came up with a solution to this problem that would enable network connection in Windows system. The method involved changing the NETWORK ADDRESS i.e. PHYSICAL ADDRESS manually. I used these following steps to repair:

1. I went to the device manager
[IMG]https://lh3.googleusercontent.com/-zYc0Xm1suUA/UCttxeM-_zI/AAAAAAAAEnk/ZAv4hOzpvv8/w326-h236-n-k/device%2Bmanager.png[/IMG]

2. Then, I clicked on the driver properties to open this dialogue box.
[IMG]https://lh5.googleusercontent.com/-69cACboQMZs/UCttxfJoE0I/AAAAAAAAEno/j_7szPZt59I/w325-h236-n-k/device%2Bsettings.PNG[/IMG]

3. I clicked on Advanced and checked the Network Address. There was no entry and it was left blank.
[IMG]https://lh3.googleusercontent.com/-kK3yEEeAxOQ/UCttxVzeqLI/AAAAAAAAEng/PMzUBuGGZEQ/w617-h484-p-k/Network%2BAddress.PNG[/IMG]

4. I immediately copied a Physical address which i knew :P into that blank and activated it.
[IMG]https://lh5.googleusercontent.com/-SWsI4D3wQnY/UCttyM8pq2I/AAAAAAAAEn0/CM9e2onkO5M/w218-h242-n-k/save%2Bperfect.PNG[/IMG]

   After this I noticed my system got connected to the network and into internet. I wanted to resolve this problem once in for all so formatted my system and reloaded windows and to my horror :confused: I noticed that the problem recurred. So, I had to repeat these steps again and again to get connected to network and to learn that I have a serious problem with my system which has somehow lost it's physical address or is failing to notice it. Meanwhile, in Ubuntu 11.04 I have no provision to manually change the address so, I am stuck :mad:. 

   Thus, I need your help... please help me here... :/

---

### Post by chili555 on 2012-08-15
>  Meanwhile, in Ubuntu 11.04 I have no provision to manually change the address so, I am stuckPlease click on the Network Manager icon, select Edit Connections and Wireless and try adding to Cloned MAC address. Please see attached.

---

### Post by srinifritter on 2012-08-15
> **chili555 said:**
> Please click on the Network Manager icon, select Edit Connections and Wireless and try adding to Cloned MAC address. Please see attached.
chili555
Sir, after going through what you said. I tried it out in my system but the problem is, when I open the edit connection and try to change an entry.. the SAVE button does not activate and thus I cannot modify or create a network connection with input of CLONE ADDRESS.


[IMG]https://lh5.googleusercontent.com/-ZRhFYJJXMUM/UCvCm_CWXhI/AAAAAAAAEoc/snHgaovNgQo/w211-h249-n-k/Screenshot-Editing%2BSrini.png[/IMG]

---

### Post by chili555 on 2012-08-15
Often, you cannot save because Network Manager thinks you have not entered enough information. Perhaps it wants the real MAC address as well as a cloned address. You can find the real MAC address with:```
ifconfig
```Here is a sample from my machine with certain details disguised:> eth0      Link encap:Ethernet  HWaddr [COLOR="Red"]x0:de:fx:3e:b2:x4 [/COLOR] 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 


---

### Post by srinifritter on 2012-08-15
Thank you for your prompt reply. I have tried typing "ifconfig" in the terminal to note the MAC address but I have not found any entry as such. I have attached a screen shot of the same. 

[IMG]https://lh6.googleusercontent.com/-GUu-YrSCYZc/UCvFxmsQlvI/AAAAAAAAEpA/FFrttStqvBQ/w478-h307-n-k/Screenshot-sriniubuntu.png[/IMG]

---

### Post by chili555 on 2012-08-15
You don't seem to have an ethernet interface at all. I doubt your problem is cloned MAC at all. Let's troubleshoot. Please post:```
lspci -nn | grep 0280
```> Please click on the Network Manager icon, select Edit Connections and Wireless and try adding to Cloned MAC address. Please see attached. I meant wired not wireless.

---

### Post by srinifritter on 2012-08-15
> **chili555 said:**
> You don't seem to have an ethernet interface at all. I doubt your problem is cloned MAC at all. Let's troubleshoot. Please post:```
lspci -nn | grep 0280
```I meant wired not wireless.

On writing this code:

```
 lspci -nn | grep 0280 
```

I get the following response:
[IMG]https://lh5.googleusercontent.com/-kgEzTkINT2k/UCv0eXLw5XI/AAAAAAAAEpg/ye0IQiNMwwA/w478-h307-n-k/lspci.png[/IMG]

---

### Post by chili555 on 2012-08-15
I don't seem to be able to keep my wireless and wired straight today! Sorry. Are you trying to get wired or wireless going? If wireless, it's going to be a bit difficult without a wired connection. Do you have the install disk? The needed files may be there. Please post:```
lspci -nn | grep 0200
```

---

### Post by srinifritter on 2012-08-15
It's fine sir, replying to so many on web will surely get you confused at times. 
For my system both Wireless and Wired are down, both wont work. You let me know when to connect what.. either wired or wireless and I would like to let you know that I don't have install Disk of Windows or Ubuntu. I only have Realtek Drivers which also didn't work when I installed them earlier ( I forgot to mention this earlier).

As u said I executed the code:

```
lspci -nn | grep 0200
```

the response is as follows:
[IMG]https://lh5.googleusercontent.com/-5oH7J1Z-Quc/UCv6VEu9YuI/AAAAAAAAEqA/2E-joqHCEXI/w422-h249-n-k/Realteck.png[/IMG]

---

### Post by chili555 on 2012-08-15
That one should be easy. Please do:```
sudo modprobe r8169
ifconfig
```Now do you have a wired ethernet interface, usually eth0? If so, please see if you can connect.

If not, let's look for errors:```
dmesg | grep r8169
```

---

### Post by srinifritter on 2012-08-16
Sorry for replying late. There is power shortage here so I couldn't work for long. 
By the way I have now the output for those codes, after ifconfig the connection did not happen to eth0, so I ran the other code as you said. Here is the output. 

1. On running the code till ```
 ifconfig 
```

[IMG]https://lh6.googleusercontent.com/-QgR7oJxJElQ/UCx0ik1HwsI/AAAAAAAAEqg/_IfnEyf8DoA/w403-h269-n-k/sudomod.png[/IMG]

2. The connection did not occur.

3. So, I ran the following:

```
 dmesg | grep r8169 
```

[IMG]https://lh5.googleusercontent.com/-95AWfEYTZs0/UCx0q12F2mI/AAAAAAAAEqw/ODtoccvE_-w/w404-h269-n-k/errorcheck.png[/IMG]

---

### Post by chili555 on 2012-08-16
We see that the driver r8169 loads nice and early in the boot process as it should and it even creates an interface eth0. We wonder why it goes no farther and why the eth0 interface dies. Let's look in the logs for eth0 and the PCI bus number for clues:```
dmesg | grep -e eth0 -e 03:00
```Quite a mystery we have here!

---

### Post by srinifritter on 2012-08-16
> **chili555 said:**
> We see that the driver r8169 loads nice and early in the boot process as it should and it even creates an interface eth0. We wonder why it goes no farther and why the eth0 interface dies. Let's look in the logs for eth0 and the PCI bus number for clues:```
dmesg | grep -e eth0 -e 03:00
```Quite a mystery we have here!

Yes sir, it indeed is. When I boot my system the start up screen shows "SERIAL KEY MISSING" in the bottom. 
As you said I executed the code and here is the result.

[IMG]https://lh3.googleusercontent.com/-YV-RlMOChM4/UC0C58duQLI/AAAAAAAAErQ/ebd-55SSAo0/w497-h373/dmesgboot.png[/IMG]

---

### Post by chili555 on 2012-08-16
I am fairly certain that the line 'no compatible bridge window' is part or all of the issue. I just don't know what to do about it! I am searching on Google for a fix and suggest you do so too. 

Can you please try a live CD for Ubuntu 12.04 to see if the problem persists? > Recently, I encountered a problem all of a sudden when I noticed my system wouldn't connect with the ethernet for no reason. There was no alert or anything as such. Since there seems to be a problem in both Windows and Ubuntu, I wonder if it's a problem in the BIOS. Can you please try looking in the BIOS to see if there are any settings that look peculiar. You might also reset the BIOS to defaults to see if the issue is resolved.

---

