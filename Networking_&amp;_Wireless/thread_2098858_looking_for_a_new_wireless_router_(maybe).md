---
title: "looking for a new wireless router (maybe)"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by nobodyfamous on 2012-12-27
My wife just got a [System76 Gazelle Professional]("https://www.system76.com/laptops/model/gazp8") and the wireless acts strangely - and I think it is just incompatible with our "routers"

If the laptop is plugged in (power) it will connect and work well.  As soon as it is unpluged (power) and running on batteries the ping speed (to google.com) goes from about 58-60ms to like 250-300ms and starts dropping packets.

The same test at our fire hall causes the ping time to increase from about 59ms to 150ms, but no packets get dropped.

so. . . What is a compatible router?  The laptop has a Centrino Wireless-N 1030 in it.

More details you can skip if you want;
The home network works fine with my iMac, and an Acer Aspire One running MINT.  Booting this laptop with MINT (live disk) yields the same issue.

The 2 wireless devices I have, and tried are a Siemens Gigaset SE567 (crap) and an Apple Airport Express (Apple :-s)  The fire hall has a D-Link DIR-### (517 I think)

The issue of dropped packets and slow ping speed is ONLY when the power cord is disconnected. (so when the wireless card is in some sort of power save mode)

Again my question is What do you recommend for a router?  (I already tried a small handful of fixes, but I think it is a hardware incompatibility as it works fine at the fire hall)

---

### Post by Bucky Ball on 2012-12-27
> **nobodyfamous said:**
> 
If the laptop is plugged in (power) it will connect and work well.  As soon as it is unpluged (power) and running on batteries the ping speed (to google.com) goes from about 58-60ms to like 250-300ms and starts dropping packets.

This suggests the computer works fine with your router and is not incompatible (_highly_ unlikely that it is incompatible anyhow, regardless of all this). When plugged in, no problem. The problem occurs when the laptop is on batteries. I'd be looking there rather than at a new router. If it was incompatible with the router it wouldn't work at all, plugged or unplugged. Perhaps the battery is going (is it fully charged?) and not able to power up the wireless card adequately. Just a guess.

> **nobodyfamous said:**
> 

so. . . What is a compatible router?



Pretty much any router. Never heard of one that isn't. The router is simply giving you a signal to connect, nothing to do with your operating system ...

---

### Post by nobodyfamous on 2012-12-27
> **Bucky Ball said:**
> Perhaps the battery is going (is it fully charged?) and not able to power up the wireless card adequately. Just a guess.

Pretty much any router. Never heard of one that isn't. The router is simply giving you a signal to connect, nothing to do with your operating system ...

This Laptop is brand new, and the battery is good.

I thought that was the case with WiFi and routers, but I spoke with the support guy at System76 and he said that apple stuff just doesn't work well with Ubuntu, which says drivers to me.

Either way, I am looking at one of these [Asus RT-N66U]("http://www.memoryexpress.com/Products/MX37448")'s but was wondering about the use of the USB ports to "host" an external drive to use for backups from Ubuntu.  Will it work?

---

### Post by Bucky Ball on 2012-12-28
USB external drive plugged into your computer you mean? Yes, it will work.

---

### Post by nobodyfamous on 2012-12-28
no, I mean the external usb drive plugged into the router, it will share the drive as a NAS - upon further reading it looks like it uses SAMBA, and says it works with Linux, OS X, and crappy. . . I mean Windows.

---

### Post by irv on 2012-12-28
I purchased the [ASUS RT-AC66U Dual-Band Wireless-AC1750 Gigabit Router]("http://www.amazon.com/gp/product/B008ABOJKS/ref=oh_details_o03_s00_i00") on Dec 12th, but sent it back. The reason was that the wireless speeds were no faster then my Linksys.(about 22Mbps). The wire was about 40Mbps which is what my Internet speed is. I too was thinking about the USB for network drives. I just order a [New-Media sharing device black - POGOP21]("http://www.amazon.com/gp/product/B005FNDJHS/ref=oh_details_o00_s00_i00") for $20 to share my Hard drives on my network and also maybe use there service for cloud storage. I just order this yesterday so I don't know how it will work out.

I don't believe your problem with your wifi is a router problem. Is there any way you can try a different wifi card in the laptop? Trouble shooting is just a process of elimination. It would be nice to eliminate the wifi card first. Just my thoughts.

---

### Post by nobodyfamous on 2012-12-28
I can not swap out the card in the laptop - I may have to send it back.  I don't want to, such a waste of money.

Can anyone else do this same test with their laptop. . . open terminal, run "ping google.com" let it go for about ten rounds and then stop it ^c

Unplug the power cable, so the WiFi card runs in it's power save mode and repeat the ping test.  What do you get?

---

### Post by kurt18947 on 2012-12-28
There is an issue with some newer Intel wireless cards and N speed.  If you search the networking and wireless forum,  I suspect you can find threads.  If not, in the networking forum search under username 'chili555'.  I've seen a few threads he was active in.  The fix is to disable 'n' support on problematic Intel wifi cards.  Not a great solution for those wanting faster wifi but as of now the only game in town.

Here are the results of the test you requested.  This is on a Thinkpad X61 with Intel 4965 AGN PCI card.

Plugged in - Min. 46  Max 72

Battery - Min. 45  Max 55

---

### Post by Bucky Ball on 2012-12-28
> **kurt18947 said:**
>  Not a great solution for those wanting faster wifi but as of now the only game in town.

But a perfect solution if your router isn't capable of wireless N, which many still commonly used aren't. ;)

Definitely try that, find out how to disable wireless N on the card.

---

### Post by nobodyfamous on 2012-12-28
I can't find the thread again, but I did try disabling the N capabilities, but the problem persisted, so that was not it.  I also tried some random blacklist of an acer thing, that also did not work.  I just found [another "solved" thread]("http://ubuntuforums.org/showthread.php?t=1877120&highlight=Centrino+Wireless-N+1030") that deals with the encryption (moves from hardware to software)

The fire hall has an un-encypted network, so that may be the difference - I will do a few more tests.

---

### Post by irv on 2012-12-28
I have been following this thread, and have been learning a few things, but it still leaves me with a few questions.
Looking at the ping readings, I would think that Internet speeds would have a real bearing on your reading on the ping test. I know you are just looking for a different reading from plugin to unplugged. Just for the record this was my reading, but I have a very fast Internet.
Plugged in 16.2 - 13.3 ms
Unplugged  14.5 - 13.5 ms
I would think if your wifi card is working properly you would not see a much of a difference in the reading no matter what Internet connection you are on.

---

### Post by nobodyfamous on 2012-12-28
yes, it's a huge difference (ping speed) on mine and lost packets, which should never happen.

The actual download speed is not much slower even unplugged IF it works at all!  The lost packets and slow ping speed render the internet almost useless.  We really noticed it trying to video chat (online gaming would also be very effected, if your into that - I am not)

---

### Post by irv on 2012-12-28
See how this works. Go to this [Site]("http://speedtest.hbci.com/") and do a speed test plugged an unplugged, and see what the difference is.
Here is mine.
[ATTACH]229251[/ATTACH]   [ATTACH]229252[/ATTACH]

---

### Post by kurt18947 on 2012-12-28
I've had a couple more thoughts

1.  This is a new machine.  Have you talked to system76?

2.  Is there a way to disable power management when on battery just for a test?  If the wifi card works well when plugged in but doesn't work when on battery, it seems the only thing changing is the machine's power management or the wifi card's power management.

---

### Post by IWantFroyo on 2012-12-28
You might have an issue with acpi messing with your wireless. Wait a moment while I try to find the command to disable that.

Edit: Couldn't find. :(
Still, I remember some people having a problem with this a while back. I had it, too. The acpi workaround helped. I'm too lazy to search through any man pages, though...

---

### Post by mringer on 2012-12-29
I think that you may have some power-save setting that sometimes 
causes your wireless to nod off when running on battery. If so, 
then it seems unlikely that a new router will do you any good. 

I would suggest that you take your laptop to some place that 
provides wi-fi access & try it on their router.

---

### Post by nobodyfamous on 2013-01-01
I could have sworn I posted dl speeds and that I was away for the last few days.  Anyhow, in another thread

> **isantop said:**
> If you're having problems, then it's likely a fail(ed|ing) card. Go ahead and open a support ticket, and we can get a new card out to you.

And I did call them right away (System76)  The guy on the phone said to do a few tests on other networks, so I did.  I had the same ping speed slow down problem - where no one else who posted results did.

I will be opening a support ticket with System76.

Thanks for everyone's help.  I guess I won't be getting a "cool" new router. . . not that I could afford one anyway.

Once I get a new card put in I will post the results.

---

### Post by nobodyfamous on 2013-01-04
Well this was extreamly disapointing - System76 wants me to pay $75.13 to have a "$36.00" part sent to me, and if I don't ship the old one back to them in 14 days they will charge me the $36.00 for it.

After about 2 minutes of Google -> Amazon -> shopping cart I found the exact same card shipped to me for less then $12.00!

I am already sorry I ever did business with System76, and only after 2 weeks with the new laptop.

):P Sytem76, I won't make that mistake again.

---

### Post by Bucky Ball on 2013-01-04
I hope you have let them know how you feel about all this. Disappointing story.

---

### Post by nobodyfamous on 2013-01-04
I did.  Told them in the support thread I was disapointed and they can keep their card.

Now that I am needing to order a new card - do I "upgrade" or just stay the same.  Some more quick searching came up with the [Intel Centrino Ultimate N 6300]("http://www.memoryexpress.com/Products/MX30760") and it is listed as in use in other certified Ubuntu systems.

BUT it has connections for 3 antennas, the 1030 in the Laptop now only has 2 antennas.  Can I use just 2 of the 3? Will it reduce any advantage the card may have had?

Maybe I should just replace it at the $12.00 cost.  Suggestions?

---

### Post by carson86 on 2013-01-08
when I was looking for the routers, I read this article that listed a few great models, maybe it can do you a favour

[http://www.wirelessrouterhome.com/best-wireless-router-review/](http://www.wirelessrouterhome.com/best-wireless-router-review/)

---

### Post by Bucky Ball on 2013-01-08
> **carson86 said:**
> when I was looking for the routers, I read this article that listed a few great models, maybe it can do you a favour

[http://www.wirelessrouterhome.com/best-wireless-router-review/](http://www.wirelessrouterhome.com/best-wireless-router-review/)

Please read rest of thread and particularly the posts just before yours. It has been clearly established this has nothing to do with the router (and rarely if ever does). All routers should be compatible and the problem generally lies elsewhere. Thanks.

---

### Post by nobodyfamous on 2013-01-14
Just to sum up, the WiFi card is dying, and thats the problem.

The issue, System76 wants a lot of money for a cheap card (for shipping)

another issue, the cd/dvd drive has also quit - so I called them, again, to see what I can do with my lemon, namely send it back as it is less then 30 days old.

Turns out they can just add the Canadian Warranty Shipping Coverage so for only $23.00 shipping is covered both ways for the parts. (all of them for the 1 year warranty)

I am happy again.  I will still put the new "upgraded" card in the laptop and report back.  I just wanted to say, I am less upset with System76 now.

---

### Post by nobodyfamous on 2013-01-18
Just a final update, System76 has "given" me (I had to pay for it of course, and it magically went up to $35.00 before they could add it:mad:) the shipping warranty, I have yet to collect on it yet, but it looks good to go. (just moving ahead really slowly)

In the mean time, I had already ordered an Intel Centrino Ultimate-N 6300 A/B/G/N it showed up today and I popped it in.

Just removed the large access door, removed the old card, put in the new one, noticed an extra (the 3rd) antenna wire, so I attached that as well to the new card (has 3 rather then 2) and put the door back on.  Took maybe 5 minutes, if that.  Booted up and everything worked.

I did the ping test and it is virtually unchanged with the power cord plugged in or not.  So problem solved, the Laptop is now wireless again.

P.S.
Loving Ubuntu! (unix operating system with easily replaceable hardware, so long crApple!)

---

