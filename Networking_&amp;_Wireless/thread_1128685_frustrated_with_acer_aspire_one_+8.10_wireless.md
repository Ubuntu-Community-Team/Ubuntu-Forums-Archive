---
title: "frustrated with acer aspire one +8.10 wireless"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by iochinome on 2009-04-17
i can not seem to get the wireless working on my acer aspire one laptop running ubuntu 8.10- i have gone through the numerous tutorials that all have me install something different, and i can still not get internet on it. does anyone know of a tutorial that WORKS? i have install madwifi, ath_pci, all that crap... and nothing. i even have the 'windows wireless drivers' thing on it, but when i try to click on 'configure network' with 'netathw' or 'netathwx' highlighted, it just tells me 'could not find a network configuration tool.'

whats up? how to fix?
thanks

---

### Post by Daisuke_Aramaki on 2009-04-17
> **iochinome said:**
> i can not seem to get the wireless working on my acer aspire one laptop running ubuntu 8.10- i have gone through the numerous tutorials that all have me install something different, and i can still not get internet on it. does anyone know of a tutorial that WORKS? i have install madwifi, ath_pci, all that crap... and nothing. i even have the 'windows wireless drivers' thing on it, but when i try to click on 'configure network' with 'netathw' or 'netathwx' highlighted, it just tells me 'could not find a network configuration tool.'

whats up? how to fix?
thanks

what is your model and what wireless card does it come with? what does the output of the command lspci on a terminal look like?

---

### Post by iochinome on 2009-04-17
the model is an acer aspire one zg5 with an atheros ar5bxb63 wireless card. the output for lspci gives me:
a whole bunch of usb cards and stuff, then

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

does that help? thanks

---

### Post by Daisuke_Aramaki on 2009-04-17
> **iochinome said:**
> the model is an acer aspire one zg5 with an atheros ar5bxb63 wireless card. the output for lspci gives me:
a whole bunch of usb cards and stuff, then

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

does that help? thanks

you need the new hal, as reported in a madwifi ticket. so you need the latest madwifi-hal snapshot. Just check the following link, where it is described for Debian Lenny. But the method should be the same. Or have you seen that link already. Just refer the atheros wireless section and follow the procedure. 

[http://www.drewwithers.com/content/debian-50-lenny-x86-toshiba-satellite-a215-s4747]("http://www.drewwithers.com/content/debian-50-lenny-x86-toshiba-satellite-a215-s4747")

---

### Post by iochinome on 2009-04-18
okay, so now i went through that tutorial that 'reasoner' gives, about halfway down the page... and still nothing. what is supposed to happen? i still do not get the wireless icon in my toolbar... or any sign that my card has been recognized. how do you confirm that at least the device driver is working?

man... if these laptops ever get popular, there's gonna be hell to pay.

thanks for help

---

### Post by iochinome on 2009-04-18
now i have done that one that you give, as well, and still nothing...

---

### Post by Chokkan on 2009-04-18
I have an Aspire One and have had no problems with wireless and in fact it was refreshingly effortless to set up so don't lose hope :)

**However**, I'm not using Ubuntu on my Aspire, I'm using Arch. You might want to try the new Network Manager. I'm guessing it will be in Jaunty or you can just get it from their PPA. Instructions on how to do this are on their launchpad site. The Arch wiki is excellent so you ought to check it out too, even if you don't use Arch, it is very easy to follow.

[Network Manager PPA]("https://launchpad.net/%7Enetwork-manager/+archive/ppa") and some [helpful instructions]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories")

From the[ Arch Aspire Wiki]("http://wiki.archlinux.org/index.php/Acer_Aspire_One#Network"):
> AA1 wireless device is a rather new Atheros wireless chip not supported by Linux kernel until version 2.6.27. Before that an external module was required to be compiled and installed named madwifi. 

Your best bet may be to try out the Jaunty release candidate on a LiveUSB. 

Good Luck!

---

### Post by ddrichardson on 2009-04-18
Arch does work well on the Aspire One but so does Jaunty - 9.04 Netbook Remix has no problems with wireless, in fact I'm on it now.

---

### Post by Chokkan on 2009-04-18
Yes, I think the easiest thing would be to jump into Jaunty and the nice new kernel.

---

### Post by iochinome on 2009-04-18
so i should just install ubuntu 9.04 and my problem will be solved? sounds easy enough...

thanks for all the help!

---

### Post by iochinome on 2009-04-18
this is quite the odyssey...
to install jaunty, i did alt+f2 then update-manager -d, where it gave the option to update to 9.04, which i did. it gave me ridiculously slow transfer rates, about 10 kb/s, even though i am connected via ethernet cable! i did the same on my other laptop (wireless btw, hp, it worked out of the box with linux) and it was getting about 500kb/s! it told me it would take approx 1.5 days to complete the installation at that rate... can i blow away the old kernel and install the new one in a different way? this is taking waaaaay to long.

thanks!

---

### Post by Sarai the Geek on 2009-04-18
If it's a pretty new install and you haven't done much customizing that you're real attached too, it may be swiftest and least painless to simply back up your data and do a fresh install from a Jaunty beta CD. I suppose it goes without saying that you should download the necessary .iso on the computer with the faster connection. :)

---

### Post by ddrichardson on 2009-04-19
Give Netbook Remix a try, there's installation instructions [here]("https://wiki.ubuntu.com/UNR"). Don't upgrade to it though, do a fresh install because I know the most recent snapshot works almost flawlessly on the Aspire One.

I say almost because the WLAN light doesn't work in this release, which is fairly trivial.

---

