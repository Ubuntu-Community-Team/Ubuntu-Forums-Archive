---
title: "OpenVPN install - string too long error"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by LAD29 on 2010-07-27
Hi,

I'm running Kubuntu 10.04 and am trying to install OpenVPN as per the instructions here:-

[https://help.ubuntu.com/10.04/serverguide/C/openvpn.html](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html)

However, when I try enter the following I just get a continuous "string is too long, it needs to be less than 40 bytes long" message.

./pkitool --initca

I've had a look around in the forum and in google and can find a reference to this problem with 9.x but from what I can see this has supposedly been fixed for v10.04.

Is there some sort of workaround I can apply to get this to work?

Cheers.

---

### Post by LAD29 on 2010-07-27
Update:-

Possibly solved. Tried another OpenVPN server install on a different server.  This step worked fine, main difference being I used a different shorter email address in the vars file.

Tried a shorter email in the vars file on the problem install and this time the "string is too long...." error didn't occur.

?

---

### Post by LAD29 on 2010-07-27
OK, have my openvpn server set up with certificates etc.

Now I get stuck -  Basically, I have a kubuntu server sat on a LAN behind a router.  I want to be able to tunnel through the router to OpenVPN on the kubuntu server so I can access the LAN.

Where I'm getting unsure is with all the refences to bridging.... I'm stuck here. Can someone just tell me if bridging is what I need to set up for this scenario or is it routing?

Cheers.

---

