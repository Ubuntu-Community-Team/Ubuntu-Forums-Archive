---
title: "Asking for help with irratic internet connection."
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by jbruced on 2010-09-17
Hello all,

I am currently running Ubuntu 10.04 on a Dell 5130 laptop, I'm using the usb port to connect to a paradyne dsl modem. My dilema is that my isp is not very savy where I live, and the activity light goes crazy flashing periodically, even when I'm not accessing any websites etc. It comes and goes, and even when I disconnect the usb cable, the activity light continues to flash(so I assume it's on their end). However when I do have the usb connected, the system monitor shows a high(~97kB receiving) activity. Could be noise? What I'm hoping to do is monitor exactly what is coming into, and leaving that usb network device when this happens. I've looked through system logs but I'm not sure what it's telling me.

Is there an application that can show real time network traffic through that usb device?



I live in the US Virgin Islands, and the level of technical expertise seems to lacking here, so I need to take it upon myself to help troubleshoot this issue.

Any and all suggestions and help will be greatly appreciated!

---

### Post by grahammechanical on 2010-09-17
What does the power indicator light do? Do you have a fluctuating electrical supply? You can use a web browser to access the modem/router. You enter the router address into the web browser. There may be a label on the router to give you the information you need. Look for the router address and the router password (also called serial number). One of the menus in my router settings is Intruder Detection. There is other information that may or may not be useful. This is all I can offer. Someone else might be able to give more technical help for what you want.

regards

---

### Post by jbruced on 2010-09-18
Thanks for reply graham.

All my equipment, OS, and software is fine. I just need to prove to the isp that their line is corrupt, and if possible show the "noise" or whatever data that is incoming during these times.

---

### Post by rocknrollmouse on 2010-09-18
Do you use your usb modem with any other computers.  

When working with these in the past I found some of them sensitive, if you change connected computer.  Generally re-booting the modem for each computer helped.  (You don't say if your service is over cable or phone-line) for some cable attached usb devices, I've even had to have the device down for 20 mins per pc change (in uk 20 is about the time needed to clear the connection at the other end).

---

### Post by jbruced on 2010-09-19
Thanks rocknroll,

The modem activity light goes crazy(causing me unable to connect to web) at times **even when I have no computers connected at all.**

It is not a problem on my end, just looking for a program to capture the garbage my isp is sending to my usb port via the dsl line.

Thanks a lot for your attention.

---

### Post by rocknrollmouse on 2010-09-19
Try Wireshark, it maybe a bit techie
here's link for installing on ubuntu:
[http://www.howtoforge.com/network-analysis-with-wireshark-on-ubuntu-9.10]("http://www.howtoforge.com/network-analysis-with-wireshark-on-ubuntu-9.10")

As with many technical tools, you may need to spend sometime getting to know it, and which tools/reports you need.


A couple of simple on-line tools, that can come in useful:
[http://www.speedtest.net/]("http://www.speedtest.net/")
[https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")
[http://visualroute.visualware.com/]("http://visualroute.visualware.com/")

Unfortunately, being on-line you do need a connection to be able to use these.  Assuming you can get a connection, Visual Route maybe the best to help with your problem.

---

### Post by jbruced on 2010-09-21
RocknRoll,

You are the essence of ubuntu. Thanks very much for your attention.

FYI, I loaded wireshack and it looks EXACTLY like what I was looking for.

If I can ever repay, please don't hesitate to contact me.

Thanks!

Bruce

P.S. If you bet on american football, visit [i60200nfl.clanteam.com]("http://i60200nfl.clanteam.com"), this is the main reason I need internet access.

---

