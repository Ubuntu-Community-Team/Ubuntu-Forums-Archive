---
title: "What should I do?"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by Vignesh S on 2009-07-23
I recently bought an old IBM Thinkpad R31 (non-wireless model). Since wifi is a necessity to me, I want to enable wireless on it. There is an empty mini-PCI slot that is just asking for a wifi card. But apparently, I have no idea if the wireless card will work. I think it should, but all I need to know is this:

Do mini-PCI wifi cards have the antenna inside of them? If not, how do I connect the wifi antenna to the right places so I can get wifi to work? If the answer is that this is impossible, then that is not really an issue, because I can just pop in a PCMCIA wifi card.

Finding a wifi PCI card that works on Ubuntu is also not much of a big deal. I just want to know if a PCI wifi card has the antenna self contained within it

---

### Post by chili555 on 2009-07-23
Perhaps this will help: [http://www.thinkwiki.org/wiki/Category:R31](http://www.thinkwiki.org/wiki/Category:R31)

As you can see, some of these came with wireless cards: > #  MiniPCI slot with one of the following:

    * none (empty)
    * IBM High Rate Wireless LAN Mini-PCI Adapter with Modem 

I suggest you look in the slot to see if you have the two antenna wires that snap on to the Mini-PCI card. The antenna is built into the laptop, not in the card. If you click on the link, it says the card was a Prism 2.5 card and shows part numbers that will assist you in finding one. Prism 2.5 is very well supported in Ubuntu; it will, most likely, plug and play. It is, however, old school in that it only does 802.11b, that is, 11Mb/s speeds and only does WEP and not WPA. If those limitations are acceptable, then I am sure Ebay can have one to you in a few days for cheap.

Other cards may fit and connect, but not work. Check here: [http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card](http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card)  

Otherwise, I'd suggest PCMCIA.

---

### Post by cfjohnso on 2009-07-26
A minor correction to your statement.

> **chili555 said:**
> Prism 2.5 is very well supported in Ubuntu; it will, most likely, plug and play. It is, however, old school in that it only does 802.11b, that is, 11Mb/s speeds and only does WEP and not WPA. If those limitations are acceptable, then I am sure Ebay can have one to you in a few days for cheap.

The original firmware of the prism 2.5 card would only do WEP encryption. If you update the flash it handles WPA2 quite nicely. I have this mini-PCI card in my old T30. I followed the instructions [here]("http://linux.junsun.net/intersil-prism/") to do the upgrade. Yes, it is still 802.11b only, 11Mb/s is plenty for my purposes.

---

### Post by shel-hall on 2009-07-26
One additional consideration ... many IBM Thinkpads will not boot if an "unrecognized" MiniPCI card is installed.  Either the cards or the BIOS can be hacked to allow other cards, but it's Another Dam' Thing to worry about.  I believe lists of workable cards and pointers to the hacks can be found over on the above-mentioned Thinkwiki.

-Shel

---

### Post by Vignesh S on 2009-07-26
I decided to get the PCMCIA card. Too much to worry about with the BIOS hacking and all.

---

### Post by Vignesh S on 2009-09-06
Change of mind. Decided to go for the internal wifi card. The reception on the PC card is just crap, partly because it doesn't have a large enough antenna. There are a few difficulties with this though:

1. Getting around the BIOS if that turns out to be a problem (hopefully, it shouldn't be, but there are a few tricks up my sleeve for that)

2. Probably the biggest problem. The internal wifi antennae. I don't know if my laptop already has them, and I don't know how to find out if I do. I probably don't, and that will mean dismantling the laptop to get the antennae in the right places.

3. The card's compatibility with Ubuntu. This is a piece of cake compared to the other two problems though, especially the second. However, this has me the most on edge because if there is no possible solutions to get it working, then the other two steps would have been in vain (and I'll have to get a new wifi card, and possible fix the first prob up).

However, the holidays are just around the corner, and I am set to do a lot of computer fixing in that time. So, the main question here. How do I find out if I already have wifi antennae installed?

---

### Post by chili555 on 2009-09-06
> 2. Probably the biggest problem. The internal wifi antennae. I don't know if my laptop already has them, and I don't know how to find out if I do. I probably don't, and that will mean dismantling the laptop to get the antennae in the right places.I have never seen an R31, however, I have fooled around inside two T23's, a T40 and a T60. Your R31 has a little door on the bottom that houses the MiniPCI card. Please see attached. Open it up and see if the antenna wires are in there.

---

### Post by Vignesh S on 2009-09-08
I now know that there are no wifi antennae inside this laptop, and I am going to fit them in, so that I can have the PC card slot free for USB 2.0 ports and other misc uses (this laptop really is ancient. only USB 1.1) 

Stripping down the laptop is not going to be a problem, thanks to a hardware maintainence manual I came across on the internet on Lenovo's website. I'll see if the wifi antennae I bought will fit, but if it doesn't, I now have the part numbers that go with it.

Anyways, I ordered a wifi card. It is an atheros chipset, so that means that I can easily implement the hack off the Thinkwiki site. 

The chipset is AR5BMB-44. I think that it supports "super g  i.e. 108 mbits.

Anyone have any idea if Atheros chipsets work "Out of the Box"? Or if they work with ndiswrapper? I think that it is well supported via the madwifi driver or something like that.

I am pretty certain that there is a way to get it to work. After all, I spent forever trying to get wifi to work on the Medion Akoya mini E1210 (it uses the Ralink RT2860 wifi card) Managed to get it to work, though I could have done it in 5 minutes if I knew how to use ndiswrapper back then. :-). Compared to that, this should be a piece of cake. :-)

---

### Post by Vignesh S on 2009-09-08
Almost forgot, the picture of the wifi card.

---

### Post by Vignesh S on 2009-09-09
<bump>
All I need to know is if Atheros chips, especially the Atheros AR5BMB-44 chipset, will work in Ubuntu. :-(

EDIT: It is (see attachment). All I now need to know is if my useful tricks will work when I get the wifi card...

---

