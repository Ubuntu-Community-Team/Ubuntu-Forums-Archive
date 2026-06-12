---
title: "wired connection works but only by pppoeconf"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by Viansi on 2010-01-03
Hello,

It's been a while since i've been trying to deal with this problem but it was useless. I've found many related problems to this, most unsolved and those who had solution wouldn't work for me. I have few mates who have the same problem and still didn't find a solution as well. Here's the problem:

Both on my Desktop and Laptop, the network manager won't recognize that there is a cable pluged on the computer so that it would start my connection. The solution to make it work is pretty simple and its everywhere: use pppoeconf. 

Altough that does the trick to make my internet work, i get another problem that i found out to be related to this one, which is: I can't use VPN. Which make me assume that one problem is related to the other, is that on my laptop, which has wireless internet, ubuntu will recognize it and then i can simple use vpn. My desktop, on the other hand, isn't that lucky and does not have wireless, so i can't just use vpn. So far, i've been using vpn on windows when needed, but switching systems is really a pain, not to say i'd rather do that on ubuntu.

Few other suggested solutions were to use 'wicd' and other network managers, altough for some people that did work accoding to what i saw on boards, that didn't really work out for me as well. Wicd coldn't recognize it either. Other suggestion was to check on some txt file on ubuntu, erase few information and let it 'fill up' automatic, it didn't work as well(sorry i don't remember all details on this one).

This problem happened on: 
First, wubi for ubuntu 9.04
Ubuntu 9.04(normal install.)
Ubuntu 9.10
Happened both on my Desktop and my notebook, but the same version i installed on both of them were used on other computers and they did work on them so i strongly believe it has to do with the os itself.

Please let me know if you need hardware details and specially how i can have access to them so i can post them here.

P.S: I'm looking for this solution currently **for Ubuntu 9.04** since i had a lot of other problems with 9.10(I couldn't even close the laptop it would make me reboot the whole system :( ). 

Thank you very much!

~ Carlos

---

### Post by Viansi on 2010-01-17
Hello again,

Seems after all these months there wasn't any reply at all, is that there is no solution for this problem..? I'm sort of disappointed.. :/

---

### Post by MarkC502 on 2010-01-17
Your problem may be as follows ( sounds like it to me anyway )

You are using a DSL modem from your ISP which requires pppoe login to work by default. ISP's always ensure it works with windows -- never Linux. 

Fortunately there is a simple solution that once applied actually give you better security as well as lessens the amount of access your ISP has to your internal network ( WIN WIN ). They are called "routers" and you can obtain one for 50$ US , once obtained you can bridge your router to your DSL modem. This in effect makes the modem just a modem and your new router becomes the brains of the operation so to speak. In the router you can configure it to do your pppoe login for you to the modem and any PC you plug into that router will pull DHCP creds and get on the internet regardless of any pppoe capability on that PC. In effect you will then be communicating from your PC to the router via TCP/IP and no pppoe anything needed any-more.

You can then forget pppoe exists and just have a nice safe home network.

I strongly recommend the Linksys 54gl model as it is 50$ at newegg and runs on linux firmware. It also has the most support for 3rd party firmwares such as DD-WRT or OpenWRT. 

Hope this info helps.

---

