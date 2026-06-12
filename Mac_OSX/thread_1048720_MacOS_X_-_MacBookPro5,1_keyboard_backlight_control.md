---
title: "MacOS X - MacBookPro5,1 keyboard backlight controls are not intuitive"
date: 2009-01-23
forum: Mac OSX
---

### Post by iva2k on 2009-01-23
Here's what I sent to Apple feedback in regards to MacBookPro5,1.

I think others might find it useful, though it does not apply to Ubuntu. Ubuntu is keeping the brand high - works like a charm.

[B]"MacBookPro Keyboard backlight controls are not intuitive."
[/B]

I thought it was broken for 2 weeks. I tried all remedies I could think of. I finally called technical support. And I learned that it is so "by design". Bad design that is.

Ok, here's the deal. When I press keyboard buttons that are supposed to control keyboard backlight, I get the keyboard light popup (onscreen display) with single-crossed circle which I understand as "not working", and the light does not change. However the change in ambient light does adjust the keyboard backlight. If I uncheck "Illuminate keyboard in low light conditions", the buttons still do not work unless it is dark enough in the room.

1. It is a usability issue. I want to have control over keyboard backlight in well-lit room, but I don't have it

2. When I disable automatic control, I want full manual control, but I don't get it.

3. The indication on display is not intuitive and misleading. There is no explanation in help files what it means. The sign may mean many things including "your hardware is broken".

4. The function is not consistent with display backlight control. I can always adjust the display backlight, even if it is dimmed or brightened by automatic control. But the keyboard backlight follows different concept. And the concept is alien to Apple.

Issue applies to:
[LIST]
[*]Mac OS X version is 10.5.6.
[*]Same in Windows XP + bootCamp drivers
[/LIST]

Works great in Ubuntu Intrepid

---

### Post by Joeb454 on 2009-01-23
Moved to OS X Sub-Forum :)

---

### Post by bfc on 2009-01-23
> **iva2k said:**
> Here's what I sent to Apple feedback in regards to MacBookPro5,1.

I think others might find it useful, though it does not apply to Ubuntu. Ubuntu is keeping the brand high - works like a charm.

[B]"MacBookPro Keyboard backlight controls are not intuitive."
[/B]

I thought it was broken for 2 weeks. I tried all remedies I could think of. I finally called technical support. And I learned that it is so "by design". Bad design that is.

Ok, here's the deal. When I press keyboard buttons that are supposed to control keyboard backlight, I get the keyboard light popup (onscreen display) with single-crossed circle which I understand as "not working", and the light does not change. However the change in ambient light does adjust the keyboard backlight. If I uncheck "Illuminate keyboard in low light conditions", the buttons still do not work unless it is dark enough in the room.

1. It is a usability issue. I want to have control over keyboard backlight in well-lit room, but I don't have it

2. When I disable automatic control, I want full manual control, but I don't get it.

3. The indication on display is not intuitive and misleading. There is no explanation in help files what it means. The sign may mean many things including "your hardware is broken".

4. The function is not consistent with display backlight control. I can always adjust the display backlight, even if it is dimmed or brightened by automatic control. But the keyboard backlight follows different concept. And the concept is alien to Apple.

Issue applies to:
[LIST]
[*]Mac OS X version is 10.5.6.
[*]Same in Windows XP + bootCamp drivers
[/LIST]

Works great in Ubuntu Intrepid

Works perfectly fine on the Macbook Pro 4.1

I wonder what they changed on the newer version?

---

### Post by iva2k on 2009-01-26
> **bfc said:**
> Works perfectly fine on the Macbook Pro 4.1

I wonder what they changed on the newer version?

I think it is software/driver that they changed. Note that Windows XP with bootcamp drivers behaves EXACTLY the same as MacOSX, while Ubuntu Intrepid + MactelSupportTeam/PPA packages works fine.

I should say that Intrepid lacks autodimming of the keyboard, while display autodimming does not work out of the box. I had to tweak Configuration Editor > apps > gnome-power-manager > ambient settings (set correction_scale to 10000). For the keyboard - I hope MactelSupportTeam/PPA will get it into the Intrepid drivers.

---

