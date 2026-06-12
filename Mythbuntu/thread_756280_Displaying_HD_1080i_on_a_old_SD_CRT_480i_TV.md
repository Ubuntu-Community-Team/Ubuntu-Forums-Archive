---
title: "Displaying HD 1080i on a old SD CRT 480i TV"
date: 2008-04-15
forum: Mythbuntu
---

### Post by Caps18 on 2008-04-15
I know it seems backwards, but I am looking for a way to get from HDMI to coax cable.

:lolflag:

Ok, stop laughing. :)

I am trying to come up with a way to use adapters and such, but I think the input resolution would need to be downconverted at some stage.  You could convert it using HDMI -> DVI adapters, DVI -> VGA, VGA -> RCA, RCA -> coax (RF modulator).  I have all of those right now except for the VGA -> RCA one.  But, I am wondering what I need to make it 640x480?  And I would rather not change the HDMI signal in, and probably would prefer a hardware based solution than a software one if possible, even though it might cost a little money.

Does anybody have any ideas?

Thanks.

---

### Post by agamotto on 2008-04-15
Go ahead and call me stupid, but wouldn't one of the DTV converter/tuner boxes do what you are asking?  The one that I have for my kitchen takes the DTV signal and makes it NTSC, which I run into the back of the telly using the composite inputs.

I hope this helps!

---

### Post by aseriesoftubes on 2008-04-15
I don't think that's possible using only adapters.

At a minimum, you will need an HDMI to DVI adapter, a DVI to VGA convertor (such as [this]("http://www.ramelectronics.net/audio-video/video-converters/dvi-to-vga-rgb-hv/ext-dvi-2-vga/prodGEF00119.html")), a VGA to Composite converter (such as [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16882196045")), and an RF modulator (which you say you already have). 

Unfortunately, a device that turns your digital DVI signal into an analog VGA signal is going to be quite pricey. The one I linked to above is $350, but you may be able to find something less expensive.

The VGA to Composite converter is the piece that handles the resolution issue. Most (including the one I linked to above) should be able to handle an input resolution up to 1024x768, and it will then automagically output the proper resolution for composite.

Needless to say, the final result of all these steps will be light-years away from reference quality. :)

---

### Post by Caps18 on 2008-04-15
> **agamotto said:**
> Go ahead and call me stupid, but wouldn't one of the DTV converter/tuner boxes do what you are asking?  The one that I have for my kitchen takes the DTV signal and makes it NTSC, which I run into the back of the telly using the composite inputs.


Does your converter box that accept inputs from anything besides an antenna?  I'm not sure the FCC would like me broadcasting my mythbuntu box throughout the neighborhood.  ;)

I've used these VGA to TV converter boxes before, and I think something like that might work if I can find one that supports 1920x1080. Along with something like this, [http://www.monoprice.com/products/product.asp?c_id=101&cp_id=10114&cs_id=1011402&p_id=4559&seq=1&format=2](http://www.monoprice.com/products/product.asp?c_id=101&cp_id=10114&cs_id=1011402&p_id=4559&seq=1&format=2) .

---

### Post by Caps18 on 2008-04-15
I'm not sure how these work, but I have one of them. [http://www.newegg.com/Product/Product.aspx?Item=N82E16812150010](http://www.newegg.com/Product/Product.aspx?Item=N82E16812150010)

It looks like I am trying to figure out how to do this for less than $400
[http://www.gefen.com/kvm/product.jsp?prod_id=1209](http://www.gefen.com/kvm/product.jsp?prod_id=1209)

---

### Post by Caps18 on 2008-04-15
I guess the maximum I could spend is $500 for a 32" LCD and just use HDMI...

---

### Post by agamotto on 2008-05-01
Hmmm, nope.  The converter box I have only does antenna/coax input.  Darn, so much for my smart idea :P

---

