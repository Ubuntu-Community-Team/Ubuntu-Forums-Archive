---
title: "Need to buy PCI internal wireless networking card for desktop"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by xiaoya on 2011-07-23
Greetings, Ubuntu forum!
I am already running 11.04 on my laptop, but I am receiving a desktop computer for my birthday (and therefore selling the laptop). I plan to install 11.04 on it, however, my husband is the computer assembler, and I'm the ubuntu nerd, and he had some concerns that I thought might not be a big deal...hence, forum posting!

So, we consulted the wiki list of [wireless cards supported in Ubuntu]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), and we had a few questions.

1 - If it works for older versions of ubuntu, does that imply that it will work in Natty? (ex: [this guy right here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCI")...WMP54G Ver 4.1)
2 - Do you have any recommendations? This is the first time I've ever used an internal wireless card...the last networked computer I had used coax, so I'm a little behind on the wireless stuff, especially for desktops. I've used some laptops, but obviously, you don't really get to pick your cards for those.

Thank you in advance!

---

### Post by westie457 on 2011-07-23
> **xiaoya said:**
> Greetings, Ubuntu forum!
I am already running 11.04 on my laptop, but I am receiving a desktop computer for my birthday (and therefore selling the laptop). I plan to install 11.04 on it, however, my husband is the computer assembler, and I'm the ubuntu nerd, and he had some concerns that I thought might not be a big deal...hence, forum posting!

So, we consulted the wiki list of [wireless cards supported in Ubuntu]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), and we had a few questions.

1 - If it works for older versions of ubuntu, does that imply that it will work in Natty? (ex: [this guy right here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCI")...WMP54G Ver 4.1)
2 - Do you have any recommendations? This is the first time I've ever used an internal wireless card...the last networked computer I had used coax, so I'm a little behind on the wireless stuff, especially for desktops. I've used some laptops, but obviously, you don't really get to pick your cards for those.

Thank you in advance!

Hi it will work after a little tinkering. Do not use the driver suggested by Additional Drivers.

Instead open Synaptic Package Manager and mark these _b43-fwcutter_ with the _firmware-b43legacy-installer_
for installation. 
Wait for the dust to settle and any networks in range to be found then sign in.

Or you could do this in a terminal using ```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43legacy-installer

```

                  =====================================================================
Forgot two things

Firstly  Welcome to the Forums

Secondly  You will need a wired connection to be able to download the drivers for this little guy.

---

### Post by Terl on 2011-07-23
Actually, westie457's advice is for the Broadcom versions.  If you are getting this one:  WMP54G Ver 4.1 it uses a Railink chip.  That one should work straight out of the box.

---

### Post by westie457 on 2011-07-23
> **Terl said:**
> Actually, westie457's advice is for the Broadcom versions.  If you are getting this one:  WMP54G Ver 4.1 it uses a Railink chip.  That one should work straight out of the box.

Thanks for that Terl. I was looking at the link the OP put up.

---

### Post by xiaoya on 2011-07-23
Wow, thank you both! That was much easier than expected! :D

EDIT: In case you were wondering, I ended up getting [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833124115"), which was the WMP54G ver 4.1 that I had posted originally.

---

