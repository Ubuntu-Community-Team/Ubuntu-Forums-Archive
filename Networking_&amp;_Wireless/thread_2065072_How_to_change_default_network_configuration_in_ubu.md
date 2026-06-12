---
title: "How to change default network configuration in ubuntu 12.04.1"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by arroy_0209 on 2012-10-01
One change in ubuntu 12.04.1 from 10.04 is that the OS checks for network config at the time of booting and perhaps wants to completes network connection before the log in screen is visible. However I use modem along with telephone line to connect to internet and till 10.04 I used to connect modem after logging into my account. This is no longer the default way in 12.04. The OS patiently tries to complete net-config and failing that, waits for "one more minute" to complete as last effort to complete but all this is useless and annoying for me since I know the process is not going to be completed as modem is disconnected. So I have to wait unnecessarily for logging in. How can I change this default behavior from trying to complete net-config at boot time to start the job only when I issue command (like "sudo pon dsl-provider") after logging in? The net-config options at system setting seems useless for this purpose. Please help.

(Please note, in case I try to boot with modem connected, even then somehow the system fails to complete the net-config process till log in screen appears. So I prefer to go back to my previous config.)

---

### Post by T.J. on 2012-10-01
(Sorry, it's late, and I didn't think "modem".  I doubt my first response would do you any good.)

Deleted

---

### Post by Iowan on 2012-10-01
It's been awhile since I used a modem. Stabbing wildly in the dark: Does Network Connections control the modem? If so, does it have the option to "Connect automatically"?

---

