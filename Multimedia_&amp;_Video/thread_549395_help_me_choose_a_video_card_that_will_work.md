---
title: "help me choose a video card that will work"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by pcrussell50 on 2007-09-12
i have one of the cursed onboard video chipsets...the ati radeon xpress200.  it causes random and spurious white screens that are hard locked, requiring a hard reboot.  interstingly, i can install feisty trouble-free.  it only locks up when surfing and/or running terminal commands.  although it's been fun and educational, i'm sick of trying to "fix" it.  my mobo has a pciX slot, and i'm willing and happy to buy an nvidia-based card.  searching revealed this list:

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html")

but i have found this card, and it's not on the list:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000380048+1069609641+1305520548&name=NVIDIA]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000380048+1069609641+1305520548&name=NVIDIA")

it is a 7200gs, the third one down, and not on the list unless i missed it, but maybe because it's too new?  otherwise, the first two ARE on the list, so i suppose they will work.  they are, the  6200le, and the 7300le.

i am not necessarily holding "the list" as gospel if you all can convince me that another card will work.

system info:
athlon64 3800+
asus mobo with radeon xpress 200 integrated [grrrr!]
1Gb corsair
winXP on a sata drive
feisty on an IDE drive
what else?

-peter

---

### Post by wolfger on 2007-09-12
> **pcrussell50 said:**
> but i have found this card, and it's not on the list:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000380048+1069609641+1305520548&name=NVIDIA]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000380048+1069609641+1305520548&name=NVIDIA")

it is a 7200gs, the third one down
"third one down" is an 8600GT... Best to link directly to the product, rather than to a search results page.

Now I think (not sure) 7200GS is what I had that I couldn't make work 100% on Linux, and wound up giving it to my wife. Possibly that was 7600GS. I would recommend going higher... There are several 8400GS cards listed for under $60, for example.

---

### Post by pcrussell50 on 2007-09-12
ok, i bellied up and ordered this card:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127273]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127273")

it is on "the list" of cards specifically supported by feisty.  the list is linked to from here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

> Installation
Ubuntu 7.04 using 'Restricted Devices Manager'

Note: If you are using Kubuntu, please follow the instructions for Ubuntu 6.10

As of Ubuntu 7.04 (Feisty Fawn) the recommended way to install the binary drivers is to use System &#8594; Administration &#8594; Restricted Devices Manager. This will try and automatically choose the correct version out of:

    *

      nvidia-glx-legacy (corresponds to the 71xx driver)
    *

      nvidia-glx (which corresponds to the 96xx driver)
    *

      nvidia-glx-new (which at the time of writing corresponded to the 97xx driver)

If your card does not appear in this [http://http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html]("http://http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html")list of cards known by Ubuntu 7.04 NVIDIA binary drivers (e.g. the 8600GT) then there is no Ubuntu 7.04 supported binary driver. For unsupported workarounds try the links in See Also. 

fingers crossed that it will work.  we'll know in a few days, i suppose.

-peter

---

### Post by pcrussell50 on 2007-09-14
just follow through, i installed the card i ordered above, the  MSI NX7300LE-TD128EH GeForce 7300LE 128MB 64-bit GDDR2 PCI Express x16 Video Card

from newegg:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127273]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127273")

and it works swimmingly.

regards,
peter

---

