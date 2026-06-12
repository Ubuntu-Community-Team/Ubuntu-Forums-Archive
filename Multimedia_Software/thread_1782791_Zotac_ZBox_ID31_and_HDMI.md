---
title: "Zotac ZBox ID31 and HDMI"
date: 2011-06-15
forum: Multimedia Software
---

### Post by molgow on 2011-06-15
Hello,

I've a [Zotac ZBox ID31]("http://pden.zotac.com/index.php?page=shop.product_details&flypage=flypage_images.tpl&product_id=296&category_id=127&option=com_virtuemart&Itemid=1"). I installed Ubuntu 11.04 sucessfully. The computer is connected via HDMI to my TV (Sony of 5 years old).
I also installed the special drivers for NVidia using the special manager application of Ubuntu.
My problem is : I can't see the whole screen on my TV. About 20-30 pixels are cut all around the screen (for instance, I can't see the top menu on my TV).
If I connect the computer with VGA, everything is OK.

Have you any idea how to solve the problem ?

Thank you for your help.

---

### Post by BicyclerBoy on 2011-06-15
When you use VGA the TV uses PC mode (direct pixel mapping), no overscan.
When you connect by HDMI the TV applies default overscan.

You need to navigate the TV set-up menu for the HDMI input & set the TV to: "no overscan", "overscan off", "just scan", "direct pixel mapping", or maybe "PC input mode".
"blah"==consumer electronic BS.

You might not be able to adjust the overscan setting as a per input basis..

Failing all of the above (& only then ) as a last resort you could try to adjust the overscan in the driver.

---

### Post by molgow on 2011-06-16
Thank you for your response. I searched my TV settings for an overscan configuration but there is not (maybe my TV is too old and the HDMI was not made to connect a PC). So I found an "overscan adjusting" property in the NVidia driver which solves my problem.

Again, thank you much. I would have removed Ubuntu and installed a Windows ](*,)if I haven't been able to solve the problem.

---

### Post by BicyclerBoy on 2011-06-16
I'm pretty sure your TV will have the just-scan  direct-pixel mapping setting somewhere..

The results (PQ) will be better because there will not need to be any scaling ..

You try could searching the avforums for your TV model..

---

### Post by molgow on 2011-06-17
Well. I'm pretty sure. I searched all configuration for about 15 minutes. I also checked the [manual of my TV]("http://www.retrevo.com/support/Sony-KDL-32V2500-TVs-manual/id/22973dj487/t/2/") (Sony KDL-32V2500) and there is not this configuration property. In the manual, they also recommands not using the HDMI port for connecting a PC :

> The HDMI sockets only support the following video inputs: 480i, 480p, 576i, 576p, 720p, 1080i. To connect a PC, please use the PC socket.

As I said, I bought my TV in 2006. At this time, this was not common to connect a PC to a TV with HDMI.

---

### Post by BicyclerBoy on 2011-06-17
You might be right about the just-scan..

I notice that your TV is not HD
Its native resolution is 1366x768, and native is the best resolution to use from a PC video card (IMO).

Your TV has a pre-scaler (like all DFPs) that accepts up to 1080i etc & scales back to native. 

It seems from your experience that your TVs HDMI input always uses overscan or at least it displays overscan with the video mode used.

What video mode have you used ?

This old post suggests this TV can work okay over HDMI
[http://www.123macmini.com/forums/viewtopic.php?t=10076&highlight=displayconfigx](http://www.123macmini.com/forums/viewtopic.php?t=10076&highlight=displayconfigx)

but that this TV will not allow native over HDMI only std video TV modes 480, 576, 720 1080

---

