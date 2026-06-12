---
title: "How can I stream video to a SmartTV"
date: 2013-06-21
forum: Networking &amp; Wireless
---

### Post by Unterseeboot_234 on 2013-06-21
Samsung TV with a built-in wifi, or can ethernet connect. Current setup is: a cable modem ethernet cable feeds a NetGear dual-band router. The router then wifi's into the SmartTV because I could select the NetGear as a network. SmartTV offers Video-on-Demand services that have front-end software for installation that will let the SmartTV have connection to their service. Flash is not an option on SmartTV. The TV comes with a Safari web browser.

Is there any way to I can configure Ubuntu to stream my video library into the TV? Samsung offers PCShare for Windows 7/8. PCShare is still a work in progress. I was hoping there is some WAN-IP I could customize.

---

### Post by restorator on 2013-06-21
+1 for Plex. Plex rocks! Totally kicked out cable TV and only use online services for the TV via a Roku box. I watch Youtube and my video collection and much more via Plex. Upped my internet speeds to 50mbs and cut cable and I am still saving $100 a month these days, even after paying for Netflix Amazon and Hulu!

---

### Post by Unterseeboot_234 on 2013-06-21
Adding Plex did activate a link icon in the SmartTV 'desktop'. The TV adds software and documentation based upon user navigation. The added software icon is called AllShare. Launching AllShare shows the PlexServer, however I cannot find my videos in the Plex folders when navigating on the TV. I would have to read the documentation for Plex to see what I'm doing wrong.

To get Plex I had to upgrade my Ubuntu. Upgrading has made my Ubuntu unusable with extra-large graphics. Nvidia cards have become a problem for Ubuntu. So, if and when I can fix my monitor resolution I will come back to networking and streaming video.

---

### Post by Unterseeboot_234 on 2013-06-22
OK. I fixed Ubuntu by deleting the nVidia proprietary driver. I don't think I currently have OpenGL with the Ubuntu GPL video driver (but that is another problem for another day).

Plex has a fuzzy feel to it. The documentation for Plex shows examples using rental movies that come in a box. My quest is to show home videos on a SmartTV. Ubuntu would take care of any file/codec issues.

I suspect:
1. Plex has one username. The SmartTV has another username. But it seems to me that visitors should be able to view my media.
2. or, I have a Samba share issue over the network. I can see my folder I created on the SmartTV. I don't see files inside that folder
3. or, I have video files with the wrong codec for my SmartTV.

I will bug the user forums over at Plex. If I get an answer I will post the fix to this thread.

---

### Post by gordintoronto on 2013-06-22
Are you using Plex as a DLNA server?

I *think* you are incorrect about Ubuntu looking after codecs -- but I don't have a smart TV to test this on.

---

### Post by Unterseeboot_234 on 2013-06-22
Thanks for the reply gordintoronto. I think I am using Plex as a DNLA server, but I'm not sure. What I mean about Ubuntu using codec is I have perl scripts that reformat media specs and make copies with ffmpeg into .mov, .mp4, .wmv, .avi, etc. into a work folder. My home video is dvRaw.

I can not get Plex to serve.

The SmartTV has apps available for download much like a SmartPhone. In one app I can see the name of the Plex server but I get empty folders. No problem attaching an USB external hard drive or MemoryStick, the video just plays. Another SmartTV app is APSoft and one can manually input the IP-config to access the TV. My knowledge is weak with Subnet access points. The Win platforms are accomplishing streaming that way, using the access point. They know firewall, and all the networking.

There appears so many different ways to stream video. Plex looked like an elegant solution. Having media accessible over a LAN offers a lot of convenience.

---

### Post by Unterseeboot_234 on 2013-06-22
Well, Doh! Ubuntu does have the Plex Media Server in the Software Center. Samsung has the Plex app in their downloads for the TV.

I configured Plex Media Server using the walk-through setup. I added a Section. I added content. The interface for Plex is a localhost in a browser. You have logged in.

After I found the Plex app and installed it I had to manually configure the IP. In the Terminal--

```
$> ifconfig
```

In the three items the command brought up information for, I was looking for something like 192.168.x.x. That was the number I entered on the TV app using the remote. I was viewing home video after selecting one of them I had posted.

Plex does indeed rock!

---

