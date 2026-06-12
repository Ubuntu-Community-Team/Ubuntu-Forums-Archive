---
title: "HDMI Audio"
date: 2012-07-02
forum: Mythbuntu
---

### Post by jlp_engineer on 2012-07-02
Sorry if this has been already posted, but I could not find anything that directly related to what I have experienced.

I just started moving my MythTV Master/Slave, with multiple FrontEnds, into their final positions.  Had to do some last minute cabling, etc.,  but when I began connecting my TV's to the HDMI outputs of my FE's, I had no audio coming through the HDMI port into the TV.  OK, no problem...  Did a little research and the issues were resolved, but then I noticed the volume control in MythTV no longer worked.  I played around a little, but the only setting that would work was using software for the mixer, and not the actual mixer itself.

I am just looking for a confirmation that this is normal, or that I still have some work to do and a setting or two to change.

---

### Post by larsolav on 2012-07-02
That is the way it is supposed to be! The audio is passed through and you control the volume with the TV or amplifier.
(if your tv or amplifier is HDMI-CEC compliant may be able program Myth (starting with 0.25) to control the volume of the TV or amplifier...)

---

### Post by jlp_engineer on 2012-07-02
> **larsolav said:**
> That is the way it is supposed to be! The audio is passed through and you control the volume with the TV or amplifier.
(if your tv or amplifier is HDMI-CEC compliant may be able program Myth (starting with 0.25) to control the volume of the TV or amplifier...)

OK, thank you.  

To be able to control the amplifier volume would be way too cool.  I am getting "geek" goosebumps. :-)

---

### Post by nickrout on 2012-07-02
You can use the "software" mixer in mythfrontend and you will be able to control the volume as usual with mythtv BUT you lose clean digital passthrough - the digital stream will be decoded, the volume changed, and then re-encoded to digital.

However if you are just connecting to a TV as opposed to a nice surround amp then you may not care too much, most TVs have crap speakers and only stereo anyway.

---

### Post by anonymousdog on 2012-07-02
> **jlp_engineer said:**
> OK, thank you.  

To be able to control the amplifier volume would be way too cool.  I am getting "geek" goosebumps. :-)

> **larsolav said:**
> That is the way it is supposed to be! The audio is passed through and you control the volume with the TV or amplifier.
(if your tv or amplifier is HDMI-CEC compliant may be able program Myth (starting with 0.25) to control the volume of the TV or amplifier...)

...and, if you can't do that, an IR blaster and some creative lirc juggling can get the job done too.

---

### Post by GuiGuy on 2012-07-05
> **anonymousdog said:**
> ...and, if you can't do that, an IR blaster and some creative lirc juggling can get the job done too.

... or get one of those nifty logitech programmable remote controls. Works for me but very low on the WAF. She says too many buttons and options :D

---

### Post by anonymousdog on 2012-07-05
low WAF: the ultimate deal-breaker :)

---

### Post by Billsputters on 2012-09-04
OK two questions

How do I set up either of those two options

Use the conversion of digits to analogue to cotrol the volume and then back to digits again

Or more impressively, program MythTv to control the TV direct

---

### Post by nickrout on 2012-09-04
> **Billsputters said:**
> OK two questions

How do I set up either of those two options

Use the conversion of digits to analogue to cotrol the volume and then back to digits againread post 4> 

Or more impressively, program MythTv to control the TV direct[http://www.pulse-eight.com/store/products/104-usb-hdmi-cec-adapter.aspx](http://www.pulse-eight.com/store/products/104-usb-hdmi-cec-adapter.aspx)

---

