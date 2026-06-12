---
title: "[HTPC] Jetway Ion Top - wireless option question"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by bedege on 2011-01-31
Hi fellow ubunteros
I'm considering building a HTPC based on Atom / Ion architecture. This machine would mainly be for watching movies (DVDs) and internet programs (hulu, amazon on demand) running Ubuntu or other Linux flavors.

I've started a wish list (see [here]("http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=13346331")) based on Jetway's Ion Top D525/Ion2 machine available from Newegg. It comes in several flavors: the -525 proposed by Newegg, the -525D that has a DVD drive and finally the -52WD with the same DVD drive + a wireless card in the Mini PCI-E slot. That last reference is the one I'm looking for, when Newegg only proposes the first reference, ie no DVD nor wireless.

If I was to buy the plain model from Newegg, what wireless solution would you recommend? Jetway does carry a wifi/bluetooth mini pci express adapter (see [here]("http://www.mitxpc.com/proddetail.asp?prod=HCWIFI037AN-F")) that comes in a bundle with an antenna. How well supported are the proposed chips from Atheros, ie AR9285 (802.11 b/g/n) and AR3011 (Bluetooth 2.1)? Would you favor that option or an USB stick?

Any feedback on the overall build as described in my wish list or the choice for wifi-n?

Thanks

Benoit

---

### Post by khamil8686 on 2011-01-31
id recommend wireless n, i had wireless g set up with dd-wrt on it and could get high def movies streamed wirelessly (probably with the dd-wrt maybe, im not sure) and i had troubles with wireless HD movies and called netflix and they said i should get a wireless N router to stream HD movies since wireless G wasnt really able to do HD (no idea how i got it to work though) i switched to wireless n and have had no trouble whatsoever streaming HD :)
maybe find a blu-ray drive instead of the dvd drive? i think DVI might be able to do 1080P (not sure, dont quote me :P) then you could play bluray discs too (also i have done no research on if bluray drives are supported by linux or not, most likely have a driver somewhere since linux supports such a wide range of hardware)

---

### Post by bedege on 2011-02-01
Thanks for your comments. I fully agree that I plan to get a wifi-n adaptor. My cable modem is wifi-n capable, thus it makes good sense to go that way.
OTOH, my concern is more about the wifi adapter interface: mini PCI-E directly on the MB, with an external antenna, or a USB stick/dongle?
Any recommendation or past experience re. Linux compatibility? ;)

Benoit

---

### Post by khamil8686 on 2011-02-01
i did some googling and from what i saw most people recommend a wireless card as opposed to a dongle, points i saw made are that its faster, you dont have conflicts with other usb devices, something about no interference because the circuitry and chips arent so close together, ive used mostly wireless cards in computers because they have changeable antennas so i can mess with getting more signal by moving them around or getting different antennas, a company ive always had good quality products and have had great linux compatibility is linksys products, ive flashed a couple of routers with dd-wrt and i have a wireless linksys card thats worked just fine out of the box since 8.10 intrepid ibex (might have worked before then, thats just the first version of linux i used and then made the switch over :) and i normally recommend the linksys cards to people, i looked at the wireless card you listed in your first post and it looks good, the only thing i wonder about is why its only a single small antenna. wireless n works by sending multiple signals out through a larger frequency band (2.4Ghz and 5Ghz i believe) and im not sure if the single antenna would cause interference and thus poor signal or not, so you might have to get a different antenna if wireless signal isnt good enough but it does look like it has a rp-sma connector which is easy to find 3rd party antennas for :)

---

### Post by bedege on 2011-02-01
Thanks for your feedback. I'll check if there are any Linksys mini pci-e wifi cards on the market (possibly with the right pigtail and antenna) :p

---

