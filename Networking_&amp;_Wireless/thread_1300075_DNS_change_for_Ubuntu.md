---
title: "DNS change for Ubuntu"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by portach king on 2009-10-24
Hi all,
Recently my internet provider changes it's services and that "instead of showing an error page, we have provided relevant search results which we hope improve your experience. This navigation service helps you find what you are looking for more effectively and eliminate dead-end “no such name” error pages you can encounter as you surf the web. This service is designed to make your web surfing experience more productive."

I hate it.

It completely interupts the way I use the internet and the address bar in Firefox. Previously, if I wanted to visit Ubuntu Forums, I'd just type "Ubuntu Forums" into the address bar, and bingo Firefox and Google would redirect me here. Now, it doesn't do that anymore.

Luckily, the provide opt out instructions: [http://service.upc.ie/service/?cid=123&aid=143](http://service.upc.ie/service/?cid=123&aid=143)  (See pdf link)

But the instructions only apply to Windows and mac users. Can anyone help turn this awful "service" off in Ubuntu?

ps. Running 9.10 UNR and loving it :)

---

### Post by dvlchd3 on 2009-10-24
I believe you can change your /etc/resolv.conf file to reflect the ip address for the DNS server they suggest to disable the service.

```

echo "89.101.160.8" > /etc/resolv.conf

```

---

### Post by portach king on 2009-10-24
Hi,
I entered the the code above into terminal but I got the 

```
bash: /etc/resolv.conf: Permission denied
```
reply.

I'm obviously doing something silly. 
Your help is hugely appreciated. :)

---

### Post by lswb on 2009-10-24
dvlchd3 was close, put this in the file /etc/resolv.conf. The file must be edited as root, you can use "gksudo gedit /etc/resolv.conf"

```

nameserver 89.101.160.8
nameserver 89.101.160.9

```

This may not survive a reboot. There are various ways to make it permanent. See "man dhclient.conf" and see the comments in /etc/dhclient.conf for info on one way.

---

### Post by portach king on 2009-10-24
Hi,

Thanks for the advise. I followed your guide and edited in the .conf file. 
This hasn't changed a thing unfortunately :( Still goes to the same "DNSAssist" page

---

### Post by lswb on 2009-10-24
Did you replace the original contents of /etc/resolv.conf or just add the lines at the end? If the latter, try removing any other "namserver x.x.x.x" lines from etc/resolv.conf. If you have no success include the complete file /etc/resolv.conf with your next post.

---

### Post by dmizer on 2009-10-24
Right click on the NM-applet in your notification area and select "edit connections". Select your NIC, and click "edit". Click IPv4 settings. Change from "Automatic (DHCP)" to "Automatic (DHCP) addresses only". Then add 89.101.160.8 to the DNS servers line. Click "Apply".

Right click on the NM-applet in your notification area, and uncheck "Enable networking". Wait a second or two. Right click on the NM-applet in your notification area, and check "Enable networking".

You now have your opted out DNS server.

---

### Post by portach king on 2009-10-25
I had tried both those solutions lswb, neither worked but thanks for your help.

Your solution dmizer worked perfectly! Thank you so much! What a relief!! :)

---

### Post by PorcelainMouse on 2009-11-05
FYI.  The DNS "Helper" opt-out should apply to all systems.  It was clearly based on MAC address of your cable modem at one point, but now you just go to your account web-page and disable it.  It shows your mac address right there, actually.  Now, I turned it off and it's still active, so hopefully that will take effect soon.  But, it's worth a shot since it's really easy now.

---

