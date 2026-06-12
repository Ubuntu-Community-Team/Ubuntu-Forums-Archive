---
title: "ubuntu 10.10 64-bit wireless usb adapter recommendation?"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by aidan. on 2011-01-02
hello,

i'm running ubuntu 10.10, and am in need of a wireless usb adapter. the reason is, my router's (which is downstairs) wireless connection isn't strong enough to reach upstairs - despite being wireless n - albeit not 5 ghz (dual band). 

so i'm looking for an ubuntu-compatible wireless n usb adapter. i'd like that that wouldn't give me any hassle/disconnect often. it's going to be used, so my xbox 360 can connect to it for xbox live - my 360 is sat right next to my pc.

i've done a bit of searching, and came across the following - i don't even know if some are compatible, but i think edimax models are? despite not officially stating so on their product range website.

[http://www.amazon.co.uk/dp/B002VGQQAE/ref=asc_df_B002VGQQAE1661592?smid=A1AUCPBF2P18HS&tag=googlecouk06-21&linkCode=asn&creative=22218&creativeASIN=B002VGQQAE](http://www.amazon.co.uk/dp/B002VGQQAE/ref=asc_df_B002VGQQAE1661592?smid=A1AUCPBF2P18HS&tag=googlecouk06-21&linkCode=asn&creative=22218&creativeASIN=B002VGQQAE)

[http://www.trusthardware.co.uk/products.asp?partno=EW-7622UMN](http://www.trusthardware.co.uk/products.asp?partno=EW-7622UMN)

[http://www.broadbandbuyer.co.uk/Shop/ShopDetail.asp?ProductID=8885](http://www.broadbandbuyer.co.uk/Shop/ShopDetail.asp?ProductID=8885)

[http://www.amazon.co.uk/Edimax-EW-7718Un-802-11n-WiFi-Adapter/dp/B000VK9BZ4](http://www.amazon.co.uk/Edimax-EW-7718Un-802-11n-WiFi-Adapter/dp/B000VK9BZ4)

[http://www.amazon.co.uk/Edimax-EW-7717UN-WiFi-802-11n-Adapter/dp/B001AIJX54](http://www.amazon.co.uk/Edimax-EW-7717UN-WiFi-802-11n-Adapter/dp/B001AIJX54)

[http://www.amazon.co.uk/AirLink-101-AWLL6075-300Mbps-Wireless/dp/B002RCKDEC/ref=sr_1_2?ie=UTF8&qid=1293998838&sr=8-2](http://www.amazon.co.uk/AirLink-101-AWLL6075-300Mbps-Wireless/dp/B002RCKDEC/ref=sr_1_2?ie=UTF8&qid=1293998838&sr=8-2)

[http://www.amazon.co.uk/TP-Link-TL-WN821N-Wireless-USB-Adapter/dp/B00194XKXA/ref=sr_1_4?ie=UTF8&qid=1293998838&sr=8-4](http://www.amazon.co.uk/TP-Link-TL-WN821N-Wireless-USB-Adapter/dp/B00194XKXA/ref=sr_1_4?ie=UTF8&qid=1293998838&sr=8-4)

i don't know if any of these are easy to configure/reliable on ubuntu 10.10 64 bit, so i'm wondering if anyone on here has any recommendations?

---

### Post by wintersfolly on 2011-01-02
Hi Aidan 

You have 2 options; 

1 - a USB Wireless Adaptor as you have suggested
I use the Belkin F5D7050 V4000 Zydas Wireless Adaptor with Ubuntu 10.10 (Maverick) - works really well. However, it was an absolutely nightmare and impossible to configure using the default Network Tool. I installed wicd, then it was ridiculously easy. I never managed to configure the wireless connection with the default Network Tools found under System->Administration by the way.   

In terms of what is supported, here is a list that should help you decide what to go for: 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

2 - Alternatively you can opt for a Wireless Universal Range Extender/ access point - I have used a Belkin WURE with Ubuntu 10.10. It works OK but the data throughput and overall performance is rather poor.  The only benefit (and it's debatable) is that you will connect via RJ45 to the WURE, so no configuration from Ubuntu point of view.  Debate aside, below is a link to the model I have tested and it works.

[http://www.google.co.uk/products/catalog?hl=en&biw=1280&bih=602&q=wireless+network+range+extender&um=1&ie=UTF-8&cid=16179430980433093281&ei=t_wgTYT0Dc2BhQfWn623Dg&sa=X&oi=product_catalog_result&ct=result&resnum=1&ved=0CBwQ8wIwAA#ps-sellers](http://www.google.co.uk/products/catalog?hl=en&biw=1280&bih=602&q=wireless+network+range+extender&um=1&ie=UTF-8&cid=16179430980433093281&ei=t_wgTYT0Dc2BhQfWn623Dg&sa=X&oi=product_catalog_result&ct=result&resnum=1&ved=0CBwQ8wIwAA#ps-sellers)


I would strongly encourage you to install wicd. This can be done through the Synaptic Package Manager:
System->administration->Synaptic Package Manager

in the "search" index/box, type wicd, mark for installation and then Apply

You should then find wicd under Application->Internet

I hope this helps. 

Regard, 
John aka wintersfolly

---

### Post by aidan. on 2011-01-02
hello john,

thanks very much for your detailed reply - it's much appreciated. i used wcid about 3 years ago on a custom distro for my asus eee pc 701 netbook - quite liked it. 

i think i'll stick to a wireless usb adapter, and read the compatibility list you linked to.

again, thanks very much for your reply :)

---

### Post by wintersfolly on 2011-01-02
Hi again Aidan, 

wicd saved me from insanity :) 

Good luck with the USB adaptor, I agree it's the right option. 

John

---

### Post by seenthelite on 2011-01-03
D-Link DWA-160.A1 Works on 10.10 64 bit. I had the adapter plugged in when I installed the operating system and it detected my access point on the first boot.

---

### Post by Shellbak3 on 2011-04-24
Is the D-Link DWA-160.A1 adaptor easy to install on a machine with Ubuntu up and running?

---

### Post by scott092707 on 2011-09-08
Hi.  I just got                       the **Edimax EW-7622UMn** USB adapter.
This is a 80211 b/g/**n**, with 2T2R up-to-300Mbps speed (whatever network I am using
is giving me 130Mbps).
As of Ubuntu 10.10 with update to Linux 2.6.35-30, this “just works”.
  Earlier, there were problems with firmware (?) not being present, and/or in the proper spot.
  The file  **rtl8192sfw.bin**  should be in the directory ** /lib/firmware/RTL8192SU**
I checked, and it was there, so I proceeded to try to connect and use the internet, and all was good.
  [If not, it apparently can be downloaded from a link at the site:
  [http://www.tuxamito.com/joomla/index.php/en/component/content/article/100-realtek-rt8192](http://www.tuxamito.com/joomla/index.php/en/component/content/article/100-realtek-rt8192)
 unzipped (  gzip -d rtl8192sfw.bin.gz  ) or probably use the Archive Manager GUI.
 and copied to the right place:
 (  sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU/rtl8192sfw.bin  )
 but I did not do any of this, as it was already in place.]


_The following is probably already known to y'all, but if not..._

  Click on the Network Connections icon in the upper right, and select the network to which to connect.
  It will ask for the network's password, if it is a secure network.
  It may also ask for a system keyring password – just enter your Ubuntu password.
  If you right-click on the icon and select Edit Connections, you can select the network and
  click on “Edit”, check “Connect Automatically”, and it will connect to that network whenever
  you boot the computer – it will still ask for the Keyring password, if it did before.

Hope this helps someone...

-Scott

---

