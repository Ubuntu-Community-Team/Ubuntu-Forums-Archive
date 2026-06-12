---
title: "switching wifi usb cause issues?"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by jesse c on 2011-06-15
I discovered that the wifi usb dongle i used for years went bad so i got an asus dongle that i cant get working.Might it be because my system is looking for my old one and the new one isnt being recognized? (e.g.wlan setting?) Yes i have no clue as to what im doing and need really really novice friendly advice

---

### Post by DanneStrat on 2011-06-15
Hi!

> **jesse c said:**
> Might it be because my system is looking for my old one and the new one isnt being recognized?

No, that shouln't be a problem.

What version of ubuntu are you using?

Post the output from the following terminal commands:

```
lsusb
```

and

```
ifconfig
```

---

### Post by jesse c on 2011-06-15
danestrat thanks for reply but since i dont have internet service on my Ubuntu 11.04 desktop to paste the results for you im stuck till i hook up an ethernet cable.but i can mention that lsusb sees a asus device but the ifconfig doesnt show anything at all to do with any hardware.Let me also point out that the clicking on the wifi icon indicates thepresence of the usb but the 'device not ready -firmware missing'.

---

### Post by DanneStrat on 2011-06-16
> **jesse c said:**
> since i dont have internet service on my Ubuntu 11.04 desktop to paste the results for you im stuck till i hook up an ethernet cable.but i can mention that lsusb sees a asus device

After running "lsusb", you will see the device name and on the left hand side of it, you will have something called an "usb id" which looks something like this "XXXX:XXXX", containing both numbers and letters. If you could write that part down for your wifi card and post it here, it would be great since we can identify which chipset it uses and load the right firmware.

> Let me also point out that the clicking on the wifi icon indicates thepresence of the usb but the 'device not ready -firmware missing'.

That looks promising. An ethernet cable would be great if you need to download a driver.

---

### Post by dFlyer on 2011-06-16
> **jesse c said:**
> I discovered that the wifi usb dongle i used for years went bad so i got an asus dongle that i cant get working.Might it be because my system is looking for my old one and the new one isnt being recognized? (e.g.wlan setting?) Yes i have no clue as to what im doing and need really really novice friendly advice

Your going to need to hardwire your computer to the modem/router so you can get the correct software needed for it to work.

---

