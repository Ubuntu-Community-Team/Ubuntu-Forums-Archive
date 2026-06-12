---
title: "WUSB54GC easy configuration in Lucid or Ubuntu 10.04"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by svkndv on 2010-04-28
It was really a nightmare for me to configure WUSB54GC Linksys wireless adopter in Karmic ie ubuntu 9.10.

Yesterday I have downloaded and did a fresh install of 10.04 RC, After the first boot Wireless was not working I did following steps and it worked wonderfully.

sudo gedit /etc/modprobe.d/blacklist.conf

Added a line

blacklist rt2800usb

After the restart I got list of wireless point available around my area including mine. I just entered password my wireless(WPA) and instantly it started working.

---

### Post by dlanod on 2010-04-30
Awesome! Thank you for posting this. This worked perfectly for my wireless linksys usb, too. I was able to see all ssid's and connect to a WEP router.

---

### Post by dantata on 2010-04-30
Thank you, mate! :)

---

### Post by olilo on 2010-05-04
Thank you very much.

That solved my problem too (same model) after trying a lot of different possible solution.

---

### Post by meithan on 2010-05-04
So I'm curious: what is the kernel loading in place of the rt2800usb driver? Just type

```
lsmod | grep rt.*usb
```

in a terminal and post the result.

---

### Post by marianlibrarian on 2010-05-07
I did that and not so lucky for me. It looks and looks and it pops up window authentiation require by wireless network" and I enter the wep code that I know is correct and I click Connect and it just does that over and over and over and never connects.

:(

this is for a public library on line catalog inhouse computer. and it is closing time. I have no internet access at home so i wont see any responses till monday.

---

### Post by sierranovember on 2010-05-08
> **meithan said:**
> So I'm curious: what is the kernel loading in place of the rt2800usb driver? Just type

```
lsmod | grep rt.*usb
```

in a terminal and post the result.

This fix worked for me, too. I tried your snippet of code in the terminal and got nothing.

```

kerry@zeus:~$ lsmod | grep rt.*usb
kerry@zeus:~$ 

```

---

### Post by marianlibrarian on 2010-05-10
> lsmod | grep rt.*usb
rt73usb
crc-itu_t
rt2x00usb
rt2x00lib
mac90211

That is what I got when I typed: lsmod | grep rt.*usb

What does it mean? 

Do these results effect why this person's solution does not work for me?

---

### Post by marianlibrarian on 2010-05-10
blacklist rt2870 module

I added this to the instructions from the first post. Restarted the machine and...

I now am connected to the network.

However, it says that the computer is off line, not powered up, not connected. But at least the network now recognizes it.

one step forward.....

---

### Post by khgiese on 2010-05-10
Thank you for this great thread. 
I am a Ubuntu newb and trying to get a grasp on this system,
Even though i understand it very little compared to my Windows experience, I am hooked on Ubuntu.
in version 9.04 I had issue with my WUSB54GC and WUSB54GP devices and basically gave up on wireless till 9.10 came along.
I gave 9.10 a fresh reload on my Dell laptop and it worked prefect for all devices.

Any way I am babbling, my apologies.


This fix was way easy once explained out and compared to past attempts at fail drive builds.


/SALUTE

---

### Post by khgiese on 2010-05-10
Well it worked good for my Dell.
But on my home built PC, same model WUSB54GC.
Did the above steps added blacklist rt2870usb to the blacklist.conf but it don't activate.

It looks like the OS sees the device, but don't turn it on.

Here is what I get if i run the command listed above.
khgiese@khgiese-ubuntu:~$ lsmod | grep rt.*usb
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
mac80211              204922  2 rt2x00usb,rt2x00lib
crc_ccitt               1339  1 rt2800usb
khgiese@khgiese-ubuntu:~$ 

On the menu up top to the right I click on the network arrows icon i get Wireless network is grey'ed out and disconnected is the status.

Not sure what the difference is, but there must be something.

---

### Post by khgiese on 2010-05-10
Like I said in my first post in this thread, I am a Ubnutu newb.

I put the wrong line in the blacklist.conf file
I should have put blacklist rt2800usb not blacklist rt2870usb.


Thanks again for this thread post.

---

### Post by ip3t on 2010-05-25
i've the same problem as marianlibrarian:
> I did that and not so lucky for me. It looks and looks and it pops up  window authentiation require by wireless network" and I enter the wep  code that I know is correct and I click Connect and it just does that  over and over and over and never connects.

and

```
sudo -i lsmod | grep rt*.usb
```
the result is nothing.

..
but with ```

sudo -i lsmod | grep rt
gameport                9089  1 snd_ens1371
rt2870sta             461811  1 
parport_pc             25962  1 
parport                32635  3 ppdev,parport_pc,lp
agpgart                31724  1 intel_agp
scsi_transport_spi     21096  1 mptspi


```

what can i do?

---

### Post by marianlibrarian on 2010-05-25
Hi ipt3, I was going to send you a pm but your profile does not allow it. so I am posting it here:

Hi,

I struggled for several days until a solution was found for me. It may or may not help you, but here is the thread that describes what I did and did not do: (you may want to just scroll down to the bottom where the plain answer is :wink:)
[http://ubuntuforums.org/showthread.php?t=1479196]("http://ubuntuforums.org/showthread.php?t=1479196")

maybe this helps you too.

---

### Post by drunkncrew on 2010-05-25
I'm so glad you posted this thread. It worked perfectly for me. I just did a fresh install of KUBUNTU and couldn't get my wireless USB stick to work for anything. It's amazing this one little line of code did it. Thanks again!:guitar:

---

### Post by ip3t on 2010-05-26
@marianlibrarian:
could you make me a summary?

---

### Post by ip3t on 2010-05-27
is anybody try to explain me the solution?
it s difficult for me to hunderstand these many posts

---

### Post by nebcanuck on 2010-08-28
Just wondering if anyone is experiencing difficulty with connecting to WPA networks through this card. I can connect fine to WEP using the initial step in this thread, but I WPA connections are recognized but fail to connect ultimately.

Not a big deal, but it would be nice to have the higher security since most modern routers and cards support WPA just fine.

---

### Post by ip3t on 2010-09-17
i've already have the same problem... 
my router has only TKIP encryption.. i've read that the device works with only AES encryption active.. 

Did anybody try another solution?

---

### Post by poltr1 on 2010-09-19
Confirmed that this fix worked on Lucid running on a Dell Latitude CPxJ with a Linksys WUSB54GC v3.  Thank you!

---

### Post by UltimateCat on 2011-12-17
> **svkndv said:**
> It was really a nightmare for me to configure WUSB54GC Linksys wireless adopter in Karmic ie ubuntu 9.10.

Yesterday I have downloaded and did a fresh install of 10.04 RC, After the first boot Wireless was not working I did following steps and it worked wonderfully.

sudo gedit /etc/modprobe.d/blacklist.conf

Added a line

blacklist rt2800usb

After the restart I got list of wireless point available around my area including mine. I just entered password my wireless(WPA) and instantly it started working.

:) Just wanted to ask you so I have clairafication.  ( Because I'm a Newbie)
Typing those above ie: sudo gedit/......directly into the terminal worked wonderfully for you?   
I have Ultimate Ed 2.7 but I don't think it will cause conflict.....you?

---

### Post by wildmanne39 on 2011-12-17
Hi, it should be the same, if you need more help please start a new thread this one is old.
Thank you

---

