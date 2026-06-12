---
title: "Invalid format ATI Radeon 3470 HDMI to tv"
date: 2010-08-19
forum: Multimedia Software
---

### Post by redmilitante on 2010-08-19
I have a Dell Optiplex GX280 with an ATI Radeon 3470 HDMI card.  I'd like to install Ubuntu on this computer, and I'd like to use my Olevia HDTV as a monitor and use it as a media computer.

I attach the tv to the computer via HDMI, and boot to the Ubuntu install disk - I'm presented with an 'Invalid Format' error message, and no video on the tv.  

Is there any way around this error so I can continue the install?  Thanks.

---

### Post by sydbat on 2010-08-19
> **redmilitante said:**
> I have a Dell Optiplex GX280 with an ATI Radeon 3470 HDMI card.  I'd like to install Ubuntu on this computer, and I'd like to use my Olevia HDTV as a monitor and use it as a media computer.

I attach the tv to the computer via HDMI, and boot to the Ubuntu install disk - I'm presented with an 'Invalid Format' error message, and no video on the tv.  

Is there any way around this error so I can continue the install?  Thanks.Can you connect to the TV via the VGA connectors? I think that you would have to have the ATI proprietary driver enabled before the HDMI would work (after install).

I have one of my boxes connected to my HDTV with an nVidea card, and had to do the full install with VGA connected first.

---

### Post by redmilitante on 2010-08-19
The way the Dell BIOS works, I'd have to open the computer up, pull the ATI card, then boot to onboard VGA.  I guess I could do it this way - I was hoping there was a more convenient way to do it, also I was worried by that 'Invalid Format' error and was wondering if anyone knew of any issues with that ATI Radeon card.

---

### Post by sydbat on 2010-08-19
> **redmilitante said:**
> The way the Dell BIOS works, I'd have to open the computer up, pull the ATI card, then boot to onboard VGA.  I guess I could do it this way - I was hoping there was a more convenient way to do it, also I was worried by that 'Invalid Format' error and was wondering if anyone knew of any issues with that ATI Radeon card.Doesn't the ATI card have VGA? Regardless, you shouldn't have to pull the ATI card out, just connect to the VGA output. The BIOS *should* recognize the difference.

And there are issues with ATI cards and Linux. However, it looks like that card is only a couple of years old, so ATI/AMD ought to have drivers for it.

---

