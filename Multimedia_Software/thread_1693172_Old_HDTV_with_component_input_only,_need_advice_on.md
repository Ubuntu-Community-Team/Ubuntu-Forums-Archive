---
title: "Old HDTV with component input only, need advice on what card to get"
date: 2011-02-22
forum: Multimedia Software
---

### Post by mwh36 on 2011-02-22
Hello, 

Long time Ubuntu user, but it's been a couple years. 

My friend had an old Dell Dimension E251 lying around and I said I'd help him turn it into a media center of sorts. The old 52" HDTV he wants to plug it into has a broken vga input and no HDMI, so our only real option is component or (heaven forbid) S-video.  He can afford to get a new video card if it's relatively cheap, and I'm not really sure what would be our best option. Does anyone have a card in mind that would be relatively hassle free? I considered getting a card with HDMI output and using one of those HDMI to component converters, but my research suggests that that won't work. Any ideas? Are there old cards with component out, or is there a card that makes this relatively easy to achieve?

---

### Post by BicyclerBoy on 2011-02-23
If you have PCIe slots..

Most of the new video cards still have VGA via DVI-I.
Some may be able to output component via a connector adapter or by external converter/adapter.

ASUS nvidia 9400GT 512MB has DVI VGA & component.
It works fine with VDPAU.
I would suggest the 9500GT 512MB is better choice because it can do 2x advanced de-interlacing.
You need to be very careful with which exact model you get.. 

If you can find a VGA to component converter you should get a GT220 or GT430.

You may need a custom modeline to get the best out of an old HDTV.
You will need to add an option "UseEDID" "False" to xorg.conf file.

---

### Post by wkulecz on 2011-02-23
I've a Viewsonic VMP-70 media player box, if all he wants to do is play media files I'd suggest this as a simpler option as it has component output (what I use) and it works great playing downloaded video from YouTube and other media files, especially nice with DVD rips. You can generally find this for ~$80 and and a USB2 hard drive for the media files and you've a nice easy to access media library with no messing around other than putting the files you want on the USB drive.

The VMP-70 is an embeded Linux product and supports ext3 filesystems as well as NTFS.

---

### Post by mwh36 on 2011-02-23
> **BicyclerBoy said:**
> If you have PCIe slots..

Most of the new video cards still have VGA via DVI-I.
Some may be able to output component via a connector adapter or by external converter/adapter.

ASUS nvidia 9400GT 512MB has DVI VGA & component.
It works fine with VDPAU.
I would suggest the 9500GT 512MB is better choice because it can do 2x advanced de-interlacing.
You need to be very careful with which exact model you get.. 

If you can find a VGA to component converter you should get a GT220 or GT430.

You may need a custom modeline to get the best out of an old HDTV.
You will need to add an option "UseEDID" "False" to xorg.conf file.

Wonderful! Does it have to be the ASUS or will this work? [http://www.newegg.com/Product/Product.aspx?Item=N82E16814139036&cm_re=9500GT_512MB-_-14-139-036-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16814139036&cm_re=9500GT_512MB-_-14-139-036-_-Product)

Better description: [http://www.jaton.com/vga/graphics_card_detail.php?pid=74](http://www.jaton.com/vga/graphics_card_detail.php?pid=74)

I know it does have pci-e, but the power supply lacks the PCI-E graphics power connector for high-end graphics cards. Would I need to upgrade the power supply for this card(standard ATX size)? Trying not to break the bank here....we'll see. Thanks again for the help :)

---

### Post by BicyclerBoy on 2011-02-23
That looks okay. Not cheap tho.. That was the new price 2 years ago..

Shame the GT220/430 can not be had with HDTV/component output ( I can not find one). The GT220 is superior in all respects except for component output. Also far cheaper.
The GT430 is an excellent feature/performance/efficiency/price point.

No special/extra power connector needed for these HTPC video cards.

Be aware the very old ATX PSU is not the same standard as newer models but that should not cause any problems..

---

### Post by mwh36 on 2011-03-01
Ok. I installed the 9500GT 512MB tonight. How do I change the resolution to fit the screen? I'm using component cables.

EDIT- Figured it out! All is well. Thanks for the help

---

