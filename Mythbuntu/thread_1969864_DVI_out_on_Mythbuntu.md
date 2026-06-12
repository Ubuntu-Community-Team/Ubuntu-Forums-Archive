---
title: "DVI out on Mythbuntu"
date: 2012-04-30
forum: Mythbuntu
---

### Post by bleve on 2012-04-30
Hi all, 

I am using a NVIDIA card currently configured with the SVIDEO out.  I would like to connect the card to component out on my TV instead of using the SVIDEO.  The NVIDIA card has a DVI out which I connected to a DVI to component cable with red, greed and blue cables that I connected into my TV.  

I changed xorg.conf  setting the:

>  Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "TVOutFormat"    "SVIDEO"
    Option    "TVStandard"    "NTSC-M"
    Option    "DPI"    "100x100"
    Option    "ConnectedMonitor"    "TV"
    Option    "NoLogo"    "True"
EndSection

To:

>  Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "TVOutFormat"    "COMPONENT"
    Option    "TVStandard"    "HD1080i"
    Option    "DPI"    "100x100"
    Option    "ConnectedMonitor"    "TV"
    Option    "NoLogo"    "True"
EndSection

I tried different HD TVStandard settings but can't get it to output to the TV.  I am not sure if using a DVI to component cable should work or not and if so not sure about the other Options.  

Has anyone set something like this up before?  I purchased a  HD PVR (the one that connects between the cable set top box and USB). 

Thanks

---

### Post by nickrout on 2012-04-30
> **bleve said:**
> Hi all, 

I am using a NVIDIA card currently configured with the SVIDEO out.  I would like to connect the card to component out on my TV instead of using the SVIDEO.  The NVIDIA card has a DVI out which I connected to a DVI to component cable with red, greed and blue cables that I connected into my TV.  

I changed xorg.conf  setting the:



To:



I tried different HD TVStandard settings but can't get it to output to the TV.  I am not sure if using a DVI to component cable should work or not and if so not sure about the other Options.  

Has anyone set something like this up before?  I purchased a  HD PVR (the one that connects between the cable set top box and USB). 

Thanks

DVI has twoversions -D and -A for digital and analogue. For a DVI to component connection I suspect you need DVI-A. Your nvidia card likely does not do DVI-A. See [http://en.wikipedia.org/wiki/Digital_Visual_Interface](http://en.wikipedia.org/wiki/Digital_Visual_Interface)

---

### Post by bleve on 2012-04-30
Well that would make a heck of a lot of sense.  If this is the case I am looking at new cards and may just go for HDMI since my TV can do that as well.   I will look at the wiki but wondering if DVI-A can be connected with a DVI to HDMI connector.  If so another card would not be needed.

---

### Post by bleve on 2012-04-30
According to the wiki DVI-I should be able to either and this card in its spec has:

VGA or DVI-I compatible monitor

From the wiki:

> DVI was developed to create an industry standard for the transfer of  digital video content. The interface is designed to transmit [uncompressed]("http://en.wikipedia.org/wiki/Data_compression#Lossless") [digital]("http://en.wikipedia.org/wiki/Digital")  video and can be configured to support multiple modes such as DVI-D  (digital only), DVI-A (analog only), or DVI-I (digital and analog).  Featuring support for analog connections as well, the DVI specification  provides optional compatibility with the [VGA]("http://en.wikipedia.org/wiki/VGA") interface.[[1]]("http://en.wikipedia.org/wiki/Digital_Visual_Interface#cite_note-2000_Press_Release-0")So this card should be able to do either.  It is a PNY GEFORCE 6200 AGP.  So maybe there is an option to make the card do Digital.

---

### Post by nickrout on 2012-04-30
> **bleve said:**
> According to the wiki DVI-I should be able to either and this card in its spec has:

VGA or DVI-I compatible monitor

From the wiki:

So this card should be able to do either.  It is a PNY GEFORCE 6200 AGP.  So maybe there is an option to make the card do Digital.

You should be able to use a DVI to HDMI cable if your TV can do HDMI. I used such a card for ages (until it blew up due to the fan stopping working).

You probably won't get audio over HDMI but you can use an analogue audio cable.

---

### Post by bleve on 2012-05-01
One of my TVs has HDMI and the other does not, hence why I am trying to get the component working.  One thing that I need to try but did not was hooking a monitor up to the DVI to make sure it is working DVI to DVI.  I will try that when I get home later today.

---

### Post by nickrout on 2012-05-01
> **bleve said:**
> According to the wiki DVI-I should be able to either and this card in its spec has:

VGA or DVI-I compatible monitor

From the wiki:

So this card should be able to do either.  It is a PNY GEFORCE 6200 AGP.  So maybe there is an option to make the card do Digital.

Don't forget VGA is NOT component! Component for your TV is YPbPy, for VGA is RGB.

---

### Post by bleve on 2012-05-01
I am not using the VGA.  Connected to the DVI.

---

### Post by nickrout on 2012-05-02
> **bleve said:**
> I am not using the VGA.  Connected to the DVI.

For heaven's sake I'll rephrase that: DVI-A is compatible with VGA, which is RGB. But for component to your TV you need YPbPr, not RGB.

---

### Post by bleve on 2012-05-02
Yes, I agree DVI-A would not work.  DVI-D shoudl as well as DVI-I.  There may be something that needs to be done, or a different driver to get DVI-D out of the card, not sure.

---

### Post by nickrout on 2012-05-02
> **bleve said:**
> Yes, I agree DVI-A would not work.  DVI-D shoudl as well as DVI-I.  There may be something that needs to be done, or a different driver to get DVI-D out of the card, not sure.DVI-D will only work into HDMI and you simply need a DVI-HDMI cable.

---

### Post by bleve on 2012-05-02
> **nickrout said:**
> DVI-D will only work into HDMI and you simply need a DVI-HDMI cable.

Thanks, this is what I needed to know.  I have a DVI to Component cable and if that will not work I need to look at plan B which would be to run a HDMI cable to my projector which is capable of doing HDMI and then for my older TV that only has component will need to come up with some other scheme.

My thought was that since DVI does YPbPr and Component does YPbPr, this DVI to component cable would work.

---

### Post by nickrout on 2012-05-02
> **bleve said:**
> Thanks, this is what I needed to know.  I have a DVI to Component cable and if that will not work I need to look at plan B which would be to run a HDMI cable to my projector which is capable of doing HDMI and then for my older TV that only has component will need to come up with some other scheme.

My thought was that since DVI does YPbPr and Component does YPbPr, this DVI to component cable would work.

I think that is where you are wrong DVI does not seem to do YPbPr - if you look at the wikipedia page the pinouts for analogue seem to be RGB:

C1 	Analog red 	  	
C2 	Analog green 	  	
C3 	Analog blue 	  	
C4 	Analog horizontal sync 	  	
C5 	Analog ground 	Return for R, G, and B signals

it is possible to use relativel simple electronics to convert from RGB to YPbPr and i suspect your convertor cable has the electronics to do so. Why it itsn't working I do not know.

As a test try a DVI to HDMI cable to the projector and at least confirm the video card is sending something out the DVI port.

---

