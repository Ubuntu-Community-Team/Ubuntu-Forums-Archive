---
title: "Connect to specific channel"
date: 2012-07-28
forum: Networking &amp; Wireless
---

### Post by garebearcarson on 2012-07-28
The question I think I should be asking is: how do I setup ubuntu (preferably the gnome network manager) to connect to an ssid but only on a specific channel?

Here is the specific context:
~poc 2wire modem/router
~dmz'd my wireless server's ports
~needed to extend the range so I set up a dlink dap-1522 (bridge/wap mode) and cisco linksys e1200 (with the same ssid and security, different channel)
~as my server is halfway between the two, it will sometimes connect to the linksys and lose port forwards

Second question: Is there a better way to extend (without new hardware)?

---

### Post by OM55 on 2012-07-29
Hello garebearcarson,

You can achieve the same result by putting in the Server's wireless definitions the BSSID of the router (MAC addres). When you do that the Ubuntu box will connected wirelessly ONLY to the device with that MAC address, in your case the dlink dap-1522 (I assume that this is what you want, right?)

The BSSID is the Mac address of the network device. This is a unique number embaded in the hardware of each network device, and looks like inthe following format: 
00:13:49:A8:77:4F                      

So here are the steps:

1. Locate and copy the Mac address of the access point you want your Ubuntu box to connect to exclusively (I assume that would be the dlink dap-1522).

2. In the Ubuntu box, open the Network Connections dialog box (you can do that in many ways, simple way would a click on the wireless tray icon).

3. Select the 'Wireless' tab and select your specific wireless connection profile and click the 'Edit' button.

4. Paste into the BSSID editbox (in the middle) the Mac address of the access point to lock your Ubuntu box to.

5. Save, close - and you are done.

From now on your Ubuntu box will ignore any other access point and will connect ONLY to the one with the Mac address you entered in the BSSID field.

Hope that helps!

---

### Post by garebearcarson on 2012-07-31
Worked like a charm. I didn't realize it would take additional arguments that easily.

Thank you.

---

### Post by OM55 on 2012-07-31
You are very welcome!

(Now you can mark this thread as 'solved').

---

