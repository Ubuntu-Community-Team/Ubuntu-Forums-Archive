---
title: "Gigabyte blues"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by mhenriday on 2011-12-27
I've recently rebuilt my main desktop, installing a new **Gigabyte GA-990FXA-UD3** motherboard, processor, PSU, RAM, and an CD/DVD-reader. Everything works fine on this dual-boot (64-bit Ubuntu 11.04, Win7 Pro) box with one exception : I am connected to the internet via an 12-24 Mb/s ADSL connexion from Glocalnet (actually Telenor) here in Stockholm, which customarily provides speeds of 15-16 Mb/s downstream and 0.85 Mb/s upstream, fairly good for this type of connexion. However, I've noticed one strange thing - if I first boot into Win7 and then reboot into Ubuntu, my connexion speeds drop to around 2 to 3 Mb/s downstream, with a corresponding drop in upstream speeds, as seen in this [**_[COLOR="Blue"]screenshot[/COLOR]_**]("https://picasaweb.google.com/100679967346308558745/Bredbandskollen20111225?authkey=Gv1sRgCIulzKnNr8Le5wE#5690900789038148882")....

I've been running dual-boots on this connexion for years and never before encountered this problem. I suspect it has something to do with network-card settings, but can't imagine what ; after all, I do get proper speeds when I boot directly into Ubuntu (the default) in the morning. Gigabyte doesn't offer any non-Windows drivers for the motherboard on its website - or if they do, I have been unable to discover them. I should be very grateful for suggestions that would allow me to toggle freely between the two OS ; while I myself much prefer the Ubuntu, I need to be able to boot into Win7 in order to be able to help others with problems on Windows boxes....

Henri

---

### Post by mhenriday on 2011-12-29
Not that this thread has generated an overwhelming amount of traffic and responses, but for the record : My mistake was that I had searched for a solution on **Gigabyte**'s website : instead, given the fact that the network card that comes with the mainboard is a **Realtek rtl8111E**, the latter's website was the obvious place to have searched. In any event, downloading the version 8168 driver and following the installation instructions found on this [**_[COLOR="Blue"]webpage[/COLOR]_**]("http://askubuntu.com/questions/79346/how-can-i-install-the-realtek-rtl8111e-version-8168-driver") on the ***Ask Ubuntu*** site, sufficed to resolve my problem. So I am definitely a happy camper now, thanks to the kind chap on the ***Ubuntu Sverige*** website who pointed me in the right direction !...:D

Henri

---

### Post by Elep.Repu on 2011-12-31
This is great. Thank you.

---

### Post by mhenriday on 2012-01-04
> **Elep.Repu said:**
> This is great. Thank you.

Glad you found it helpful !...

Henri

---

