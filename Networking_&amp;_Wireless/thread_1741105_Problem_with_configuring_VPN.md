---
title: "Problem with configuring VPN"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by gripen on 2011-04-27
Hi guys I'm having problems with creatign a VPN with OpenVPN and to add to it I am a total noob at anything to do with VPNs.:confused:
I'll be glad if any of you could help.

I basically wanted to create a VPN between by Linux box and my Windows box.Pretty much I want my Linux box to be able to access the Internet(via VPN)  through my Windows box when I am working on a public Internet connections.

I'll be glad i anyone could guide a total noob though configuration.:)

---

### Post by Sven6210 on 2011-04-28
> **gripen said:**
> Hi guys I'm having problems with creatign a VPN with OpenVPN and to add to it I am a total noob at anything to do with VPNs.:confused:
I'll be glad if any of you could help.

I basically wanted to create a VPN between by Linux box and my Windows box.Pretty much I want my Linux box to be able to access the Internet(via VPN)  through my Windows box when I am working on a public Internet connections.

I'll be glad i anyone could guide a total noob though configuration.:)

I am not really sure what you intend to do. I understand you have a Windows and a Linux machine. Which one is the fixed server and which one is the mobile device you also want to use e.g. at an airport of coffee shop?

I further understand that you want to build up a secure VPN connection when surfing at a public internet access point - which is a very good idea indeed.

Then another question, what is the upload speed of your internet at home. Most internet connections are asynchronous, you can download from the internet much faster than you can upload it. In your case, if you install a openvpn server at home, your upload speed will be the bottleneck for the download speed you have with your mobile device at any public internet access point.

The next question is what you want to use your VPN for. If you want to access your whole network when travelling you should definitely have your own VPN server at home. If you only want to secure your internet traffic from other users sniffing at the WiFi hot spot you do not need your own server. You can also consider using a professional VPN service provider such as "Witopia" where you pay app. 40 USD per year and you have access to a great many of VPN servers around the globe. This is good enough to avoid internet censorship (as it exists in some countries) as well as being protected from people spying on public WiFi hot spots.

Having your own server at home run 24/24 can easily cost more electricity than using a VPN service such as Witopia.

Conclusion:
The given information is not sufficient to make a good suggestion. You need to be more specific.

---

