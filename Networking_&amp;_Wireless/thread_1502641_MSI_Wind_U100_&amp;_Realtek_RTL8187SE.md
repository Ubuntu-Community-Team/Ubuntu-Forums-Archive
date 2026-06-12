---
title: "MSI Wind U100 &amp; Realtek RTL8187SE"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by guscpu on 2010-06-05
I recently bought the MSI Wind cheap off Ebay and installed a dual boot with Ubuntu UNE/Windows XP. Its a great little laptop unfortunately I have the rubbish battery which i may upgrade.

One of the biggest problems I've had from what was surprisingly a painless install of UNE was trying to get the wireless working. I use WPA encryption (network name not broadcast) incidentally.

I got my card to eventually work and it works without fail now wherever I connect at home or at friend's houses. I have to give credit to someone else who had this suggestion but I cannot find the link to his site to give due credit. As I am a complete Linux newbie I also cannot be of much help apart from verifying the workaround below works :)

1.
Start by installing the graphical version of ndiswrapper in the Ubuntu Software Centre you can find it under "Windows Wireless Drivers"

2.
Next you will need to download the Windows XP driver for the card from Realtek

3.
Go to System->Administration and then "Windows Wireless Drivers". Enter your password.

4.
Navigate to the file "net8187se.inf" and apply and then restart.


After I rebooted my card still didn't work you might be luckier. What I have to do each time after the computer boots/wakes up is to 

A.
Go to the wireless applet on the top panel and disconnect, then wait for a message to pop-up to confirm disconnection. 

B.
Again clik on the wireless applet and this time select your wireless network, pray for a short bit and hey presto it connects!!

One site which shows what to do step by step which is not the one I originally used but is even better is....

[http://www.chazco.co.uk/post.php?po=37](http://www.chazco.co.uk/post.php?po=37)

Hope this helps

Gus


MSI Wind U100 user
& Linux idiot :P

---

