---
title: "Dell 1520 Wireless-N Card Driver Issue"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by binoyjayan on 2010-09-17
I installed Ubuntu 10.04 in my Dell Studio 1558 laptop recently. 
The wireless LAN is not enabled. Can some one point me to where I can possibly find 
drivers for my wireless network card.

My wireless card is "Dell 1520 Wireless-N Card"

Thanks

---

### Post by Fafler on 2010-09-17
First we need to knwo what card you actually have. Open a terminal and type

lspci | grep Wireless

---

### Post by MaindotC on 2010-09-17
Fafler thank you for offering help but there is a more complete  [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) that shows each step you need to take in order to troubleshoot your wireless card.  Please let us know if you have any difficulty and precisely where so we can better help you.

---

### Post by binoyjayan on 2010-09-18
Thank you Fafler and strAlan for your quick responses.

I tried executing the command "lspci | grep Wireles" but it did not give any output.

strAlan,

Thanks for the link. I'll give it a read.

---

### Post by OooBuntuRox on 2010-09-24
> **binoyjayan said:**
> Thank you Fafler and strAlan for your quick responses.

I tried executing the command "lspci | grep Wireles" but it did not give any output.

strAlan,

Thanks for the link. I'll give it a read.

Same here. No results. I am trying to upgrade a 15n/ 1545 with a wifi-g card to wifi-n card. Does anyone know of any cards that dell sells for the 15n/ 1545 for wifi-N?

Or possibly a card that intell sells? Does the Intel 5100 work with Ubuntu 10.04 or above and the Inspiron 1545/ 15n?

Thanks, OooBuntuRox, :guitar:

---

### Post by binoyjayan on 2010-09-24
hi OooBuntuRox,
 
I'm struggling understanding the ubuntu troubleshooting guide. may be u should also give it a read. let me also know if u com 2 know something..

---

### Post by bkratz on 2010-09-24
> **binoyjayan said:**
> hi OooBuntuRox,
 
I'm struggling understanding the ubuntu troubleshooting guide. may be u should also give it a read. let me also know if u com 2 know something..

Where are you having difficulty with the guide?  Perhaps we can help. Anyway you might see this thread it may help you.  I believe it was post 4.

[http://newyork.ubuntuforums.org/showthread.php?t=1555430](http://newyork.ubuntuforums.org/showthread.php?t=1555430)

---

### Post by OooBuntuRox on 2010-09-24
> **binoyjayan said:**
> hi OooBuntuRox,
 
I'm struggling understanding the ubuntu troubleshooting guide. may be u should also give it a read. let me also know if u com 2 know something..

I just looked at that command again and tried: **Sudo lspci **(in terminal at the prompt) instead. You should get a list of all your hardware. Network cards are at the bottom for me.

What is the link to the guide you are talking about? I don't even know where that is. I've just been googling and doing searches on this site. Then, Piecing things together. On a wing and a prayer :rolleyes:

Is this LINK what you are talking about: [http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)

Please take a look at my thread too. It will help you to see my thoughts better. FYI: I am using an Inspiron 15n/ 1545 not a studio like you.

[COLOR=Red]LINK to my thread:[/COLOR]
[http://ubuntuforums.org/showthread.php?p=9882723#post9882723](http://ubuntuforums.org/showthread.php?p=9882723#post9882723)

By the way, My Inspiron didn't come with a WiFi-N card. It came with a WiFi-G card. I can't find a WiFi-N card suggested for the 1545/ 15n at the Dell site. Tech support isn't sharing much info either. They don't seem to like discussing Ubuntu very much. I ask a few questions and they leave the chat session abruptly. One tech did comment they are only trained in Windows. So I feel lucky to have received any help from them about Ubuntu.

Thanks, for the suggestion.

OooBuntoRox, :guitar:

---

### Post by Chris1274 on 2010-09-24
> **OooBuntuRox said:**
> Same here. No results. I am trying to upgrade a 15n/ 1545 with a wifi-g card to wifi-n card. Does anyone know of any cards that dell sells for the 15n/ 1545 for wifi-N?

Or possibly a card that intell sells? Does the Intel 5100 work with Ubuntu 10.04 or above and the Inspiron 1545/ 15n?

Thanks, OooBuntuRox, :guitar:
I know that the Studio 15z comes with an Intel wireless card, so I can't see why it wouldn't work with an Inspiron 15xx as well.

---

### Post by MaindotC on 2010-09-24
> **OooBuntuRox said:**
> Same here. No results. I am trying to upgrade a 15n/ 1545 with a wifi-g card to wifi-n card. Does anyone know of any cards that dell sells for the 15n/ 1545 for wifi-N?

Or possibly a card that intell sells? Does the Intel 5100 work with Ubuntu 10.04 or above and the Inspiron 1545/ 15n?

Thanks, OooBuntuRox, :guitar:

The [4965]("http://www.intel.com/p/en_US/support/highlights/wireless/4965agn"), along with almost all Intel wireless cards, have full Linux support.  That doesn't ALWAYS work but a majority of the time it does.

---

### Post by binoyjayan on 2010-09-24
> **bkratz said:**
> Where are you having difficulty with the guide? Perhaps we can help. Anyway you might see this thread it may help you. I believe it was post 4.
 
[http://newyork.ubuntuforums.org/showthread.php?t=1555430](http://newyork.ubuntuforums.org/showthread.php?t=1555430)
 
 
i read that post before. but didnt help me much..

---

### Post by binoyjayan on 2010-09-24
> **OooBuntuRox said:**
> I just looked at that command again and tried: **Sudo lspci **(in terminal at the prompt) instead. You should get a list of all your hardware. Network cards are at the bottom for me.
 
What is the link to the guide you are talking about? I don't even know where that is. I've just been googling and doing searches on this site. Then, Piecing things together. On a wing and a prayer :rolleyes:
 
Is this LINK what you are talking about: [http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)
 
Please take a look at my thread too. It will help you to see my thoughts better. FYI: I am using an Inspiron 15n/ 1545 not a studio like you.
 
[COLOR=red]LINK to my thread:[/COLOR]
[http://ubuntuforums.org/showthread.php?p=9882723#post9882723](http://ubuntuforums.org/showthread.php?p=9882723#post9882723)
 
By the way, My Inspiron didn't come with a WiFi-N card. It came with a WiFi-G card. I can't find a WiFi-N card suggested for the 1545/ 15n at the Dell site. Tech support isn't sharing much info either. They don't seem to like discussing Ubuntu very much. I ask a few questions and they leave the chat session abruptly. One tech did comment they are only trained in Windows. So I feel lucky to have received any help from them about Ubuntu.
 
Thanks, for the suggestion.
 
OooBuntoRox, :guitar:
 
 
 
no i am talking about the ubuntu hosted troubleshooting guide
 
 
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by MaindotC on 2010-09-25
Well can you describe what it is your having trouble with?  It's probably just terminology that requires some understanding.

---

### Post by OooBuntuRox on 2010-10-01
> **strAlan said:**
> The [4965]("http://www.intel.com/p/en_US/support/highlights/wireless/4965agn"), along with almost all Intel wireless cards, have full Linux support.  That doesn't ALWAYS work but a majority of the time it does.

[SIZE=2]Thanks on that info. I will have to look closer at the 4965 to make sure the physical dimensions are the same as my card. I believe my is described as a HALF-mini card. So it may be smaller than the 4965. If not, it sounds like the 5100 would work. I like the idea of going with an Intel card. Being that they support the card, already include a driver in recent versions of Linux, and have a repository for upgrades too. Doesn't seem as resrictive as the Broadcom/ Dell proprietary driver situation. My guess is that Intel may offer support for a longer period of time being that they actually make the board.
[/SIZE]
[SIZE=3]OooBuntuRox,[/SIZE] :guitar:

---

### Post by OooBuntuRox on 2010-10-01
> **binoyjayan said:**
> no i am talking about the ubuntu hosted troubleshooting guide
 
 
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

You're right, I SHOULD read that guide. Thanks :). One step at a time. I'm still configuring the primary harware. But I WILL read it. No slackers over hear. ;) Thanks again.

OooBuntuRox, :guitar:

---

