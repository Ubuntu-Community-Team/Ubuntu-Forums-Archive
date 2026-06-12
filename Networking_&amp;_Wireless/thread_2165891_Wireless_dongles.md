---
title: "Wireless dongles"
date: 2013-08-06
forum: Networking &amp; Wireless
---

### Post by duan2 on 2013-08-06
So I was cruising around my local MicroCenter and noticed they had on sale one of these USB wireless dongle.  Since my VAIO is 7+ years old it has the older wifi slower speed spec'd unit inside.  If I were to buy this and just plug it into the USB port it should just work right and take over my existing wifi on board.  I know it's seems like an obvious question but I'm sure xubuntu has that PnP feature in it right?

[http://www.microcenter.com/product/373032/W311M_150Mbps_Wireless_N_USB_20_Adapter](http://www.microcenter.com/product/373032/W311M_150Mbps_Wireless_N_USB_20_Adapter)

[IMG]http://c773974.r74.cf2.rackcdn.com/373032_926592_01_top_thumbnail.jpg?1375831264996[/IMG]

---

### Post by Petro Dawg on 2013-08-06
I have a computer approximately the same age as yours running Xubuntu using a Belkin wireless USB dongle very similar to the one you have listed without any issues.  

Never used Tenda brand before so have no idea if that particular one will work, but I expect it will.  According to my quick internet search that brand/model does appear to be Linux compatible.  Worst case, you lose $10.

Also, you might have to adjust some settings to turn off the on-board wireless, but it shouldn't be too much of an issue (if any at all).  Likely (just an educated guess) you may end up with two sets of wireless networks listed (with wlan0 and wlan1), just pick the one being received by the dongle.

---

### Post by wildmanne39 on 2013-08-06
I did not see anything at there site that said linux is supported, it all depends on the chip.

---

### Post by Petro Dawg on 2013-08-07
A google search pulls up these on the first page of results.

From [here]("http://www.tenda.cn/tendacn/DownLoads/show.aspx?downid=916") (tenda driver support for model W311M)
> 1.This driver fits for Windows/Linux/Mac OS.

From [here]("http://finddealsfor.me/products/Tenda-W311M-150Mbps-Mini-Wireless-N-Nano-USB-Adapter-SKU-CN0078X-FocalPrice-p988074") (third party sales)
>   * Compatible with Windows 7/Vista/XP/2000/, MAC OS and Linux

From [here]("http://www.focalprice.com/CN0078X/Tenda_W311M_150Mbps_Mini_Wireless_N_Nano_USB_Adapter.html") (third party sales)
> [FONT=Verdana][FONT=Verdana][FONT=Verdana]Compatible with Windows 7/Vista/XP/2000/, MAC OS and Linux[/FONT][/FONT][/FONT]

I would say it is most likely compatible.

I did notice that the site provided by the OP isn't consistent on which model they are selling... W311M or W311U?  However, I also found similar listings for W311U stating it's Linux compatible.

---

### Post by duan2 on 2013-08-07
thank you for the replies, i'll have to double check at the store to find out if it's a W311M or U

I have a wifi physical switch on the laptop I can turn the onboard wifi off 

Im having a blast w/ xubuntu and a STEEP learning curve.  I haven't used my macbook air tonight so that's a sign LOL

---

### Post by kurt18947 on 2013-08-07
> **duan2 said:**
> thank you for the replies, i'll have to double check at the store to find out if it's a W311M or U

I have a wifi physical switch on the laptop I can turn the onboard wifi off 

Im having a blast w/ xubuntu and a STEEP learning curve.  I haven't used my macbook air tonight so that's a sign LOL

I imagine it depends on the model but with Thinkpads, turning off the little network slider switch disables all wireless networks, internal and USB.  Something to keep in mind.  According to wikidevi, the Tenda W311M uses the Ralink 5370 chip which should be plug 'n' play on 13.04 and I think 12.10.  I'm not certain it'd be plug'n' play on 12.04. I suspect not, you may need to compile the driver for 12.04. Same source says W311U uses the Ralink 3070 chipset.  I have a micro/nano adapter using the 5370 chipset and it works, no experience with the 3070 chipset.

---

