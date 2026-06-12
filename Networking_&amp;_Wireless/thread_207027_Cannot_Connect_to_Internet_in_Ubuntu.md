---
title: "Cannot Connect to Internet in Ubuntu"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by Miki01 on 2006-07-01
Hello, I just installed the latest edition of Ubuntu from an ISO I had burned a few hours ago. Everything is installed and it works. But when I try upon Firefox, I can't get to Google. It seems that I cannot connect to the internet. I'm not sure if its my equipment, or user error somewhere. I tried going to System>Administration>Networking and tried setting up an ethernet connection from that... Its still seems that I cannot connect to the internet... May be it is my machine? I don't know. If anyone can help me, it would be greatly appreciated. This is the first PC I am building, so please bare with me. 

My current setup is listed below:


CPU - AMD Sempron64 3600+ AM2 socket (1337)
Mobo - Asus M2N32-SLI Deluxe Wi-Fi Edition
Graphics Card - XFX nVidia GeForce 7300 GS
HDD - Seagate Baracuda 80GB
Optical - Sony DVD/CD ReWritable DRU-810A
RAM - Corsair Value Select 1024MB PC5400 DDR2 (2 x 512MB)

The motherboard supports dual gigabit LAN. So I just unplugged the cable from my other PC and plugged it into one of the ports... Please help me... It would be greatly appreciated!

---

### Post by jakez on 2006-07-01
Maybe you have to reset or restart your modem; after that put the following command into the terminal:
sudo /etc/init.d/networking restart

I'll hope it works.
Greetz

---

### Post by Miki01 on 2006-07-01
Yes, my connection is working now! Many thanks to you! ^_^

---

