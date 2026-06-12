---
title: "Zyxel NWD2205 wifi usb card"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by n3le on 2011-06-12
Hi, does anyone has experience with Zyxel NWD2205 wifi usb card. Is it working under ubuntu and is it possible to create ap with this wifi usb card. Tks :)

---

### Post by arihut on 2011-07-30
Hi,

I Bought this Zyxel NWD2205 and wasn't able to use it right a way.

-I googled a bit and [founded]("http://www.wikidevi.com/wiki/ZyXEL_NWD2205")[1] that it uses Realtek  rtl8192cu       
-I downloaded driver from [Realtek[2]]("http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") ,use search if link not working 
-Unpacked downloaded zip
-Went to terminal, made myself as root, moved to unpacked directory, added execute bit to install.sh   (chmod a+x install.sh)
-Started install script "#./install.sh"

After those steps my computer was able to use this NWD2205. I haven't really look any special features. I was wery happy when Ubuntu said that connection speed is 300Mb/s

Hope above has some help. 

-Ari-

[1] [http://www.wikidevi.com/wiki/ZyXEL_NWD2205](http://www.wikidevi.com/wiki/ZyXEL_NWD2205)
[2] [http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

---

