---
title: "Pulseaudio in  Karmic with Skype 2.1.0.47"
date: 2010-01-13
forum: Multimedia Software
---

### Post by Robbyx on 2010-01-13
I had the sound working from the Logitech webcam 9000 pro and then it stopped. I had adjust the mic volume and then found I could not get the mic to work at all. It is being seen by the pulse audio sound meter.

I have not yet worked out how to ensure that the sound from the webcam is used. It defaults to the sound card's plug in mic. I have been through the pulse audio applet and its options have not helped.


I would be most grateful for some additional help in getting the webcam's usb mic to work.

---

### Post by tube013 on 2010-01-15
I have a similar setup (Karmic with a logitech 9000...

at first skype wasn't getting the mic input.

I did 2 things, I set the webcam's mic as the default source with the pulseaudio-device-chooser applet, and then with the pulseaudio volume-control- I had to set the webcam mic under the input devices tab as the fallback (green checkmark icon).\

that seemed to work, I was able to make a test call with out any problems..

---

### Post by Robbyx on 2010-01-15
Thanks. The default fallback is not obviously switched on or off. I click on the button and the icon doesn't change. Is yours any different?

---

### Post by tube013 on 2010-01-15
> **Robbyx said:**
> Thanks. The default fallback is not obviously switched on or off. I click on the button and the icon doesn't change. Is yours any different?

Not sure, might depend on the theme... 

the button does look a little grayer than the deactivated one.

---

### Post by Robbyx on 2010-01-15
> **tube013 said:**
> Not sure, might depend on the theme... 

the button does look a little grayer than the deactivated one.

I see what you mean. It is slight but after looking for the difference in the surround of  the button,  I can see it changes. 

Thanks for your help

---

