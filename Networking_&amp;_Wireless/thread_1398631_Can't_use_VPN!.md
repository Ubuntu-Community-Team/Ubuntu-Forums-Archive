---
title: "Can't use VPN!"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by winjeel on 2010-02-04
I've spent an hour at the IT dept of my university trying to get a wireless connection for e-mail access working... 80% of that time was trying to get the iPhone to work (despite the IT guy following the same instructions I did, and doing his bit of magic more than that), and the other 20% of the time was getting 9.10 to work. There is a connection, my computer knows there's a wifi network present, but it isn't able to connect. The IT guy tried to add a VPN but the "Add" button was greyed out. If I can get the "Add" button un-greyed, then he can do the rest. What can be done?

[Details: Dell v10 mini with fresh installed 9.10, and a cup of fresh instant coffee]

---

### Post by amauk on 2010-02-04
There's different types of VPN
command below will install the clients for the 2 most popular

```
sudo apt-get install network-manager-pptp network-manager-openvpn
```

Add button should now be enabled, and you can setup either a PPTP VPN (Microsoft's VPN protocol) or an OpenVPN

---

### Post by winjeel on 2010-02-04
thanks. I'll give it a go when I can get home. :p

---

### Post by winjeel on 2010-02-05
Got it, and it's working. Cheers. :D

---

### Post by hambidextrous on 2010-02-05
I am having this same issue.  I have a Dell Mini with Hardy.  If I try  ```
sudo apt-get install network-manager-pptp network-manager-openvpn
```
then I have to remove network-manager and network-manager-gnome.  Even if I do that the add a VPN button is still greyed out AND my wireless internet stops working.  I have to plug into the internet to uninstall the pptp and openvpn and reinstall the two I removed just to get wireless working again.  Are there any other solutions?

---

