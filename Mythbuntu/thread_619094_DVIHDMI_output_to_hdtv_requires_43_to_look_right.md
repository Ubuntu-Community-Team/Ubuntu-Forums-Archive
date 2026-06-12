---
title: "DVI/HDMI output to hdtv requires 4:3 to look right?"
date: 2007-11-21
forum: Mythbuntu
---

### Post by ubnewbie2 on 2007-11-21
I am using a DVI to HDMI cable to connect my mythbuntu (7.10) to my HDTV, and it works but...

1.  There is serious overscan for the mythbuntu desktop
2. When watching TV in Myth, I need to switch to 4:3 to make the aspect ratio look right (16:9 looks squashed)


Also, what resolution should I use. It defaulted to 800x600 and I changed that to 1024x768, but neither of these are standard hdtv resolutions.

My video card is a Geforce 7200 and I am using the nvidia prop. drivers.

---

### Post by axelsvag on 2007-11-21
It seems like your tv is not pixelmapping the signal from the myth. I used the nvidiasettings to change the setting in the box Flat Panel settings. In my case under the menu DFP-0. After that the overscan problem was gone.

---

### Post by ubnewbie2 on 2007-11-21
> **axelsvag said:**
> It seems like your tv is not pixelmapping the signal from the myth. I used the nvidiasettings to change the setting in the box Flat Panel settings. In my case under the menu DFP-0. After that the overscan problem was gone.


Sounds good.  Where do I find the nvidiasettings?

---

### Post by superm1 on 2007-11-22
in the mythbuntu control centre.  There is a button for it.

---

### Post by ubnewbie2 on 2007-11-22
> **superm1 said:**
> in the mythbuntu control centre.  There is a button for it.

Found it.


Can you tell me how yours is set?  Mine does NOT have the "Force full GPU scaling" box ticked, and it is set to "stretch" on the radio buttons.

When I choose "centred"  I get a small screen in the centre of the TV - maybe because I have mythbuntu set to 800x600 right now?

I forget what the 3rd option is called, but it causes overscanning too.

I'll also add that the driver is a bit flaky - if I muck around too much with these settings, funny things happen (glitches/corruption in graphics, partial repainting) - that need to be fixed by <ctrl-alt-BS> on the X windows server.

---

### Post by superm1 on 2007-11-22
Okay so here is the thing.

When you are talking about a TV, the spec for DVI allows for overscan.  DVI on a TV isn't normally used with a computer, but instead a device that will output a picture with overscan.

You've got three options here.

1) Switch to VGA, most TVs don't overscan the VGA input.  Mine actually will only do its native 1366x768 via VGA.

2) Create a modeline to work around this.

3) Resize myth to compensate for overscan.  You can define the placement and size of the window in the settings.

1 is the most ideal route, 2 and 3 will both be time consuming to get right.

---

### Post by ubnewbie2 on 2007-11-22
> **superm1 said:**
> Okay so here is the thing.

When you are talking about a TV, the spec for DVI allows for overscan.  DVI on a TV isn't normally used with a computer, but instead a device that will output a picture with overscan.

You've got three options here.

1) Switch to VGA, most TVs don't overscan the VGA input.  Mine actually will only do its native 1366x768 via VGA.

2) Create a modeline to work around this.

3) Resize myth to compensate for overscan.  You can define the placement and size of the window in the settings.

1 is the most ideal route, 2 and 3 will both be time consuming to get right.

Alright then. I'll try it.  Will I lose much picture quality using VGA, as compared to, say, option 2 (if I managed to get it to work)?

---

### Post by superm1 on 2007-11-22
> **ubnewbie2 said:**
> Alright then. I'll try it.  Will I lose much picture quality using VGA, as compared to, say, option 2 (if I managed to get it to work)?
Nothing at all noticable.  Personally i'm happier with the VGA over the DVI/HDMI.  You can't beat native resolution in my case.

---

### Post by ubnewbie2 on 2007-11-22
> **superm1 said:**
> Nothing at all noticable.  Personally i'm happier with the VGA over the DVI/HDMI.  You can't beat native resolution in my case.

Right now, I have it working into my VGA at 1024x768, and it looks pretty good. I will experiment with modelines for the 1366x768 native res sometime though.

---

### Post by superm1 on 2007-11-22
> **ubnewbie2 said:**
> Right now, I have it working into my VGA at 1024x768, and it looks pretty good. I will experiment with modelines for the 1366x768 native res sometime though.
Well if its not already there, add "nvidia-auto-select" to the first of your list in the resolutions line.

It then tries to sort it out from EDID (and usually does a pretty good job)

---

### Post by ubnewbie2 on 2007-11-22
> **superm1 said:**
> Well if its not already there, add "nvidia-auto-select" to the first of your list in the resolutions line.

It then tries to sort it out from EDID (and usually does a pretty good job)

OK 

Many thanks for the tips.

---

