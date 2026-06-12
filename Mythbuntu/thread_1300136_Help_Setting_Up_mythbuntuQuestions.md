---
title: "Help Setting Up mythbuntu/Questions"
date: 2009-10-24
forum: Mythbuntu
---

### Post by Jaybone203 on 2009-10-24
I am getting ready to build a mythbuntu system and I defintely need some pointers. 

I am building a backend, using my old PC, replacing motherboard, adding RAM etc. I am considering the [Hauppauge WinTV-HVR-2250]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116037") card for the setup.

But is it possible for me to set up my current [computer]("http://review.zdnet.com/product/desktops/asus-essentio-cg5270-bp003/33699688")(replaced Graphics Card with [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814102854&cm_re=4670-_-14-102-854-_-Product")) as a front end? 

Will i be able to also capture my Xbox 360 in HD. If not, can some one please lead me in the right direction.

I have full faith in the community being able to help me out. Thanks for your time.

---

### Post by Boppy3125 on 2009-10-25
ATI based video isn't considered a great option for Linux because of the drivers.  But still that thing looks like it has plenty of horsepower for a frontend.  I have no idea about the 360, are you talking about connecting the 360 into the 2250?  What is the video out on the 360?  If the 2250 can take that as an input, then you can do it?

---

### Post by Jaybone203 on 2009-10-25
> **Boppy3125 said:**
> ATI based video isn't considered a great option for Linux because of the drivers.  But still that thing looks like it has plenty of horsepower for a frontend.  I have no idea about the 360, are you talking about connecting the 360 into the 2250?  What is the video out on the 360?  If the 2250 can take that as an input, then you can do it?

The Xbox 360 can output HD via HDMI and Component Video. I basically just want to capture the video from my 360 using any method possible. I have been told I would need a good video capture card for such a purpose.

EDIT: Basically I want to make sure I can get a tuner/capture card that will not only work with capturing from my cable box/satellite(switching soon) and will also be able to capture my Xbox 360.

---

### Post by fenian on 2009-10-26
You don't need to upgrade that graphics card what you already have will work better for a frontand because NVidia supports VDPAU for offloading video processing from the CPU to the GPU and the ATI drivers for linux offer no similiar benefit.Use the money you save towards a component capture device,they are a little expensive,[this one]("http://www.hauppauge.com/site/products/data_hdpvr.html") has the best support in mythtv/linux.

---

### Post by Jaybone203 on 2009-10-26
The only thing about that capture device is that is doesn't have any composite outputs, which i would need since I don't yet have an HDTV. Is there any way I can convert the out coming Component signal into a Composite signal to output to my SDTV?

---

### Post by tgm4883 on 2009-10-26
> **Jaybone203 said:**
> The only thing about that capture device is that is doesn't have any composite outputs, which i would need since I don't yet have an HDTV. Is there any way I can convert the out coming Component signal into a Composite signal to output to my SDTV?

The component outputs there are for passthrough. You will need a video card with composite or svideo to output to an old SD TV. Newer TV's will have the ability to use other connections such as VGA, DVI, component, and HDMI

---

