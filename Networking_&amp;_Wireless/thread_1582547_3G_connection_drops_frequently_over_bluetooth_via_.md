---
title: "3G connection drops frequently over bluetooth via Blueman using Nokia 6233"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by amarendra on 2010-09-26
I am facing this problem.
I use Nokia 6233 via bluetooth to connect my Laptop (Ubuntu) to 3G Internet. The Internet connection goes down in some every 7-8 minutes. Then, I have to do this:

[LIST=1]
[*]Blueman Applet on Panel
[*]In the "Bluetooth Devices" window right-click on my Phone Name and click "Refresh Services"
[*]Then right click again and click "Dial-up networking"
[*]Then click "Setup" and select "Dial-up Networking (DUN)" radio-button and click "Forward"
[*]Then click on "Network Manager Applet" and click my 3G connection
[*]Within a few seconds the Internet connection resumes.
[/LIST]

Note: While the Internet connection goes the my 3G connection is still there in Network Manager applet list under "available" (But clicking on it doesn't connect Internet and Network Manager already shows connection as broken with no antenna "bars") and disappears only after "step 3". 

I have no idea what breaks/drops the connection. Anything to do with message bus security policy? I have disabled iptables.

---

