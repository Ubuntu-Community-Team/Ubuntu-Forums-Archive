---
title: "Plug-and-Play USB Wireless Adapter for 11.04?"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by Griegfan on 2011-06-01
Greetings from Arizona, USA:

Is there a true plug-and-play USB wireless adapter that is known to work well with Ubuntu 11.04 (32-bit)?  

Background: 
* HP Pavilion zv6000 or zv6100 (Older notebook being used for business purposes. It came with Windows XP Home Edition.)
* Installed Ubuntu 11.04 (32-bit)
* PROBLEM: Don't have WiFi as well as another item or so.  Novice Ubuntu user.
* Ran this in terminal: sudo lspci
* 03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller (rev 03)

I have not performed a lot of research on this problem, but what little I've done tells me I could spend a fair amount of time trying to get WiFi to work on this notebook.

If a user-tested, literal plug-and-play USB wireless adapter exists for Ubuntu 11.04, it might be cheaper time-wise to just buy it rather than try to get my existing hardware to work.

Thank you.
Griegfan

---

### Post by westie457 on 2011-06-01
> **Griegfan said:**
> Greetings from Arizona, USA:

Is there a true plug-and-play USB wireless adapter that is known to work well with Ubuntu 11.04 (32-bit)?  

Background: 
* HP Pavilion zv6000 or zv6100 (Older notebook being used for business purposes. It came with Windows XP Home Edition.)
* Installed Ubuntu 11.04 (32-bit)
* PROBLEM: Don't have WiFi as well as another item or so.  Novice Ubuntu user.
* Ran this in terminal: sudo lspci
* 03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller (rev 03)

I have not performed a lot of research on this problem, but what little I've done tells me I could spend a fair amount of time trying to get WiFi to work on this notebook.

If a user-tested, literal plug-and-play USB wireless adapter exists for Ubuntu 11.04, it might be cheaper time-wise to just buy it rather than try to get my existing hardware to work.

Thank you.
Griegfan

Hello, do you have internet access with an ethernet cable?

If so then go to this link
[http://ubuntuforums.org/showthread.php?t=1604868&page=24](http://ubuntuforums.org/showthread.php?t=1604868&page=24)

Read post #240 and follow the instructions. This should get your on-board wireless working. This explains more clearly the cure I found with the Broadcom 43xx wireless chip.

Good luck.

About the wireless USB dongle. The Edimax EW-7711UTn works out of the box using the Ubuntu shipped RT drivers. There are others. I use the dongle on my desktop pc as it did not have wireless built-in.

---

### Post by Griegfan on 2011-06-01
> **westie457 said:**
> Hello, do you have internet access with an ethernet cable?

If so then go to this link
[http://ubuntuforums.org/showthread.php?t=1604868&page=24](http://ubuntuforums.org/showthread.php?t=1604868&page=24)

Read post #240 and follow the instructions. This should get your on-board wireless working. This explains more clearly the cure I found with the Broadcom 43xx wireless chip.

Good luck.

About the wireless USB dongle. The Edimax EW-7711UTn works out of the box using the Ubuntu shipped RT drivers. There are others. I use the dongle on my desktop pc as it did not have wireless built-in.


Thank you very much for the response.  I have Internet access with an ethernet cable, so I will read through post #240 later today.

If after a certain amount of time I don't see a light at the end of the tunnel (or the tunnel looks too long and dark), I might just go get a USB adapter.  

However, I don't want to trade one set of problems for another.  If you or anyone else has a moment, could you answer this question:  Would a USB wireless adapter work as well as a notebook's internal WiFi?

Thank you again.
Griegfan

---

### Post by westie457 on 2011-06-01
Hi, I am no expert on this subject and there are more knowledgeable people out there. IMHO a USB dongle depending on whether it's capabilities (that is 802.11 a/b/g/n) will be at least the same as the in-built wifi.

Internet speed which is governed by your ISP will generally be slower than network speed between 2 computers at home. This speed is decided by the slowest link in the chain, whether it is the router, the cable, the built-in wifi or the USB dongle. The fastest wireless speed is on 802.11n which is capable of transfer speed upto 300 MBs a second. 802.11g speed is about 54 MBs a second. Either of these is usually faster than most ISP's let us have.

The Edimax USB dongle I mentioned in my earlier reply is 802.11n capable and is backwards compatible with the earlier standards. Also it might be faster than your Broadcom 43xx chip which might top out at 802.11g which is the same as my built-in wireless.

I hope this is easy for you to understand. I have tried to keep it simple and clear.

---

### Post by Griegfan on 2011-06-03
> **westie457 said:**
> Hi, I am no expert on this subject and there are more knowledgeable people out there. IMHO a USB dongle depending on whether it's capabilities (that is 802.11 a/b/g/n) will be at least the same as the in-built wifi.

Internet speed which is governed by your ISP will generally be slower than network speed between 2 computers at home. This speed is decided by the slowest link in the chain, whether it is the router, the cable, the built-in wifi or the USB dongle. The fastest wireless speed is on 802.11n which is capable of transfer speed upto 300 MBs a second. 802.11g speed is about 54 MBs a second. Either of these is usually faster than most ISP's let us have.

The Edimax USB dongle I mentioned in my earlier reply is 802.11n capable and is backwards compatible with the earlier standards. Also it might be faster than your Broadcom 43xx chip which might top out at 802.11g which is the same as my built-in wireless.

I hope this is easy for you to understand. I have tried to keep it simple and clear.


Thank you again, Westie457.

I was hoping my post would generate many replies from happy 11.04 users who have found a true plug-and-play USB WiFi product.  I am not sure what to make of this lack of response.  

(I called the number provided at the Edimax site and it appears they don't sell product at retail.  I am hoping to find a product that I can just run down to Frys Electronics and buy.)

I skimmed over post #240 from the link you provided.  

To a new user who is not super technical, I will tell you quite honestly that it looks like a near-unbelievable amount of effort to get my notebook's internal Wifi working on Ubuntu -- an effort which might not even end successfully.  

It is a little sobering that the thread has #326 posts.  I jumped to that final 326th post (posted 12 hours ago), and this was the first sentence:  "Has anyone been able to fix the frequent disconnects problem with the broadcom wifi?" 

To me, it's not unreasonable to ask myself, "What chance does a newbie like me have of making this work?"  

I have a hope (maybe a naive hope) that there's a 11.04-friendly USB WiFi device at Frys just waiting for me -- a device that will be plug-and-play, NOT plug-and-pray.

Griegfan

---

### Post by westie457 on 2011-06-03
Hello, here is my solution to getting Broadcom 43xx wireless working.

I also had this problem of wireless not working with the Broadcom STA Wireless driver after up-grading to 'Natty Narwhal' on my Acer laptop with a Broadcom 4311 wifi module. A big thank you to all who posted before me even though the suggestions put forward did not work. However I found a work around this problem and I hope others may find it useful.
The solution in my case worked using a network cable and 'Synaptic Package Manager'. This is what I did:-
1) In Additional drivers I de-activated the STA driver
2) In 'Synaptic' I then removed them completely.
3) Went back into Synaptic and found 'b43-fwcutter' and 'firmware-b43-installer'. I installed both packages because I was not sure which one was needed.
4) After a reboot wireless signed in to the router and the cable removed

In your case I would use 'firmware-b43legacy-installer' instead of the one in my solution.

From start to finish this should take about 10 minutes. There have been no dropped connections on my laptop. This fix was applied about 5 weeks ago.

The Edimax USB dongle was bought from my local Asda store in the United Kingdom, I believe they are owned by Walmart a US company. No harm in looking around your local one. 

Another option is buy one the same make as your router.

One question I am going to ask you. Dows your laptop have USB 2 ports as standard or are they USB 1? I am asking because I cannot remember when USB 2 took over from USB 1 as the standard.

Good luck and whichever option you choose is the right one.

---

### Post by bkratz on 2011-06-03
@westie457  from the op's first post

Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller (rev 03)

The rev 3 uses the b43 driver just like you. If it was the rev2 then he would need the 'firmware-b43legacy-installer'.

See the table on this page
[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

---

### Post by westie457 on 2011-06-03
> **bkratz said:**
> @westie457  from the op's first post

Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller (rev 03)

The rev 3 uses the b43 driver just like you. If it was the rev2 then he would need the 'firmware-b43legacy-installer'.

See the table on this page
[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)
Thanks for the info. As stated earlier I am no expert and can only go by personal experience. Hopefully I have not stuffed up 'griegfan' s laptop with some useless information. 
I break my system often enough and try not to break other peoples systems.

Something new learnt today!!!

---

