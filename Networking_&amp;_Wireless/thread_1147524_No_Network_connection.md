---
title: "No Network connection"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by Vince_8.10 on 2009-05-03
If I hold the cursor over the network icon on my acer laptop it shows No Network Connection. It used to connect to my destop without a problem. About a week back we had a cable and phone outage and I reset my cable modem. I think that's when the problem started. I have all the connection information in the laptop but when I click on Connect "Disconnected - The Network connection has been disconnected is displayed. If I go to terminal and type in iwconfig It shows eth1 with the information: iEEE.11bg ESSID:"" Nickname:"". When I type in Sudo lshw -c network, It shows *-network description: Wireless interface; Logical Name: eth1. If I look at my network configuration it shows "Auto VAPNETWORK12 - 8 DAYS AGO, Mode: infrastructure, Connect automatically is checked and MTU: is automatic. Any suggestions? Let me know if there is any additional information you need. I'm new to all this, but learning fast. Thanks in advance for the help.

---

### Post by cariboo on 2009-05-03
Is there a router built into your cable modem? If there is, then the reset probably set all the settings back to the factory defaults.

---

### Post by Vince_8.10 on 2009-05-04
My Router is a separate device. It's a Linksys Wireless-G Broadband Router, Model WRT54G2 V1. Do I need to go into the software of the router and define parameters for it to see my laptop??

---

### Post by connor4312 on 2009-05-04
Wow, talk about conicedense.

I too just installed Ubuntu 9.04 on an Acer laptop, and have had the same problem with the same cable modem (Linksys WRK54G2 right?). Not sure why, I'll post if I figure it out.

---

### Post by Vince_8.10 on 2009-05-04
Well I just resolved my problem by going into my router software and changing my settings. So maybe I can help you out.
Go into your router software - 192.168.1.1
On the Setup tab, select the subtab: Basic Setup

From the pull down list box "Automatic Configuration -DHCP" 
should be selected.

Router Name: WRT54G2
Host Name: leave blank
Domain Name: leave blank
MTU: Select "Manual"
Size: change to 1490

Now select the "Wireless" tab
Wireless Configuration: select "Manual"
Wireless Network Name (SSID): type in: Your SSID name here.
Wireless Channel: select 9 - 2.452GHz
Wireless SSID Broadcast: select "Enabled"

Now click on the sub tab: "Wireless Security"
Security Mode: Select WPA Personal
WPA Algorithms: select: TKIP
WPA Shared Key: type a secret key: (MUST BE 8 OR MORE CHARACTERS)
Group Key Renewal: 3600 seconds

Now click on the Security tab
Click on the check mark box next to all of the filters

Your done.

---

