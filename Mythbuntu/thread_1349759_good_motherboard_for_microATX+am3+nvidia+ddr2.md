---
title: "good motherboard for microATX+am3+nvidia+ddr2"
date: 2009-12-08
forum: Mythbuntu
---

### Post by reformy on 2009-12-08
hi all
i bought an AMd Athlon II X2 245, a 2G DDR2 800, and an Antec nsk2480. Now I need a good mother board for all this... My original plan was to buy gigabyte MA78GM-US2H, but it has an ATI and I know that's no good with ubuntu.
Does someone has a recommendation for a motherboard for this? It must be microATX and NVIDIA (with HD, doesn't has to be the latest), and ready for am3 and ddr2.

thanks..
yair

---

### Post by ghostborg on 2009-12-08
I am running a MA78GM-S2H with a Phenom II X4 920 , originally I was running it with an AMD Athlon 64 X2 but upgraded so I could encode faster. The board has an ATI HD3200 which does run if you install the ATI Catalyst control center from the ATI website. AMD owns ATI so I think you will find more boards with the ATI/AMD combo. I recently had an update come down through the Update Manager which broke my system so I disabled the onboard ATI video and installed a cheapo Nvidia card I had just because I have better luck with Nvidia than with ATI using Ubuntu. I am one of those people that keep coming back and trying ATI products but end up with Nvidia.
I think that is the definition of insanity. 

BTW the Athlon 64 X2 ran well.
In fact I just purchased another MB
GIGABYTE GA-MA785GM-US2H RT to put it in.

---

### Post by lidex on 2009-12-08
Have a look here:
[Newegg]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010200022%201070947010%201071048571&name=Phenom%20II%20%2f%20Phenom%20%2f%20Athlon%20II%20%2f%20Athlon64%20%2fSempron")
AMD integrated video seems to be predominant, but what's to stop you from installing an nVidia card?

---

### Post by SiHa on 2009-12-09
I've just built a new frontend (9.10, 32bit):

Gigabyte GA-M85M-US2H
Athlon II X2 250
2.5" IDE 80GB HDD
1GB DDR667
Scythe Shuriken cooler

For mobo details, see [[COLOR="blue"]_here_[/COLOR]](http://www.linuxtech.net/features/best_linux_htpc_motherboards.html) and [[COLOR="Blue"]_here_[/COLOR]](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ClassValue=Motherboard&ProductID=3140). It has onboard nVidia 8200, and handles 1080i using VDPAU with 18%CPU load. Total power for this, with a 2.5" HDD is ~52W. And it's completely silent (I upgraded the PSU fan to a 12cm one as well)

HDMI audio in MythTV works OOB, by simply selecting ALSA:HDMI in the sound options. I had to tweak a little to get ot working in the rest, but it was simple enough in the end.

All in all I'm very happy with this setup.

---

### Post by reformy on 2009-12-09
Thanks guys,
I've decided to start with the original board (MA78GM-US2H) and if I don't manage to get the ATI working, I'll add an nvidia card.

yair

---

