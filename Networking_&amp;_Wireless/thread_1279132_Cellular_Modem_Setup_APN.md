---
title: "Cellular Modem Setup: APN?"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by pgn674 on 2009-09-30
I'm trying to use my cellphone as a modem over bluetooth. I have an LG VX8350 with Verizon Wireless. I have set up a custom proxy that I manage myself, and I know it works as I can get general internet access from the WAP browser on the phone. I can also get regular web browser internet from my Nokia 770 using the cell phone as a modem over bluetooth.

I found the instructions at [BluetoothDialup - Community Ubuntu Documentation]("https://help.ubuntu.com/community/BluetoothDialup"). I tried following them, but I've gotten stuck at Configuring PPP, as I don't know what my APN is. Would that be my proxy server? I tried that, and it's not working. Nor do I know what the data profile number is on my phone, or how to find that out. Maybe these instructions are for GSM only, and I have CDMA? If so, does anyone have some equally good CDMA instructions?

I am also curious: On my Nokia 770, I did not have to look up things like APN. It was almost just connect-and-go. And the 770's OS is Maemo, based on Debian Linux. So, what do they have that Ubuntu doesn't, that allows the device to connect without needing a lot of custom details?

---

### Post by GeorgeVita on 2009-10-01
Hi **pgn674**,
Access Point Name ([APN]("http://en.wikipedia.org/wiki/Access_Point_Name")) is defined by the provider so a search using 'country', 'provider name', 'APN' and possibly 'ubuntu' hits some answers.

As I remember (but cannot check), Verison Wireless works with any APN but they need your 10 digit phone number plus '@vzw3g.com' as **username** (1234567890@vzw3g.com) and vzw as **password**.

Warning: you mentioned WAP, do you know that 'real internet' connection may cost you a lot more? Check by asking your provider before trying. Also ask them about settings.

Regards,
George

---

### Post by pgn674 on 2009-10-14
Sorry for the delay. I took a look at what you said, but I don't see where in the instructions I linked it even asks for a username or password. I should note that I tried this in Windows Vista on the same machine too, and that wouldn't work, so the USB Bluetooth dongle I got may be bad or cheap. I won't have time to troubleshoot for a while, so it'll be a while before I get back to this thread.

---

