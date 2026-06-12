---
title: "Ubuntu 15.04 not supports Musilano  Monitor MINI0 usb sound card"
date: 2015-08-30
forum: Multimedia Software
---

### Post by KOSKERS on 2015-08-30
My friend gives me a usb sound card.
When i connect it into my computer, i find Ubuntu 15.04 not supports Musilano  Monitor MINI0 usb sound card.

lsusb : 


Bus 001 Device 006: ID 04b3:4137 IBM Corp.

---

### Post by Rob Sayer on 2015-08-30
To see if it's recognized I'd use:

```
sudo aplay -l
```

Unfortunately if it doesn't work it's not a matter of ubuntu supporting the card.  it's a question of the manufacturer of the card not supporting linux.

---

### Post by KOSKERS on 2015-08-31
hi  thx for replying indeed!!!
aplay -l

card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: VT1802 Analog [VT1802 Analog]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: VT1802 Digital [VT1802 Digital]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 2: VT1802 Alt Analog [VT1802 Alt Analog]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0

---

