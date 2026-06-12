---
title: "Cisco Aironet Client 350 Set up"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by andnobodyslept on 2006-06-25
Hey everyone,
So I just switched over to Linux after my girlfreind was nice enough to give me her old Compaq laptop. I installed Xubuntu 6.06 on it and have been loving it. The only problem that I have is that I am unable to connect to my school's free wireless since it involves manually setting up useing cisco aironet series 350 clinet software. I have a Linksys Wireless-B notebook adapter (802.11b) which Xubuntu set up automatically (I tryed it out on some other networks and it worked great). The only problem is I can't figure out how to set it up manually to conect to the schools encryted network. The schools instructions are only for Macs and Win and the link below is what they say to do (I currenly think I should use NYU-Roam1 or Roam 3)
[http://www.nyu.edu/its/wireless/configure.html](http://www.nyu.edu/its/wireless/configure.html)
My school's IT service doesn't help people with Linux so I'm leaving it up to you all. As I said I'm somewhat new to linux so any help would be great.
Thanks,
Ian

---

### Post by mips on 2006-06-25
[http://www.nyu.edu/its/software/nyunetcd/wireless.html](http://www.nyu.edu/its/software/nyunetcd/wireless.html)
[http://www.nyu.edu/its/software/nyunetcd/connectNYUOffice.html](http://www.nyu.edu/its/software/nyunetcd/connectNYUOffice.html)
[http://www.nyu.edu/its/software/nyunetcd/connectOffice.html](http://www.nyu.edu/its/software/nyunetcd/connectOffice.html)

I think you need to have a look at the above links, especially the first one as they most likely contain pertinent info on the parameters used (WEP, WPA, LEAP, SSID etc) which are pretty important to setup a wireless connection.

The public does not have access to the above links for obvious reasons. I suspect their security is pretty tight as they reference 3 options for connecting, those with genuine cisco products so it its probably proprietry, roam1. You might have to look at Roam3 and 2 options. And they use VPN over wireless which tells you they are security conscious.

---

### Post by andnobodyslept on 2006-06-25
Thanks for the reply,
I took  a look around those links and I've found some good info. The only problem is that I am rather a n00b at Linux and am not too sure on how to configure a Leap in Bash. Sorry for bringing it down to such a basic level but any help would be great, if for nothing else but then to help my understanding.
Thanks again,
Ian

---

### Post by mips on 2006-06-26
[QUOTE=andnobodyslept]Thanks for the reply,
I took  a look around those links and I've found some good info. The only problem is that I am rather a n00b at Linux and am not too sure on how to configure a Leap in Bash. Sorry for bringing it down to such a basic level but any help would be great, if for nothing else but then to help my understanding.
Thanks again,
Ian[/QUOTE]

Cisco LEAP is a proprietary protocol and not a very secure one at that. Cisco has licensed the technology to some other vendors but it is not that common. There is a Linux client available of the Cisco software from Cisco.

What is the version/model of your Linksys Wireless-B adapter as we need to determine the chipset used ???

You might wan't to rather go the VPN route as described in one of those links. The airnonet 350 adapters can be had for $20 of ebay. I think they use a ralink chipset.

If you want you can mail me the info in those links, I will not distribute it or abuse it. I have helped others before where they actually gave me their username and password. Can supply a reference form this forum if you need via email/pm.

---

### Post by mips on 2006-07-01
andnobodyslept installed the Cisco VPN Client but had to use the patch below for linux kernel 2.6.15 to make things work incase anybody is wondering.

[http://www.victortrac.com/cisco_vpn_patch](http://www.victortrac.com/cisco_vpn_patch)

Thanks for the feedback andnobodyslept !

---

