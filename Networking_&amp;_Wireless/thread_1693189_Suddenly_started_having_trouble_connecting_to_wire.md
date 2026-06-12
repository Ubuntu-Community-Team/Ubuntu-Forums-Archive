---
title: "Suddenly started having trouble connecting to wireless"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by Jwiere03 on 2011-02-22
I have been using Ubuntu exclusively since August with no problems. Then about a month ago I came home after being gone for a couple of days and my laptop wouldn't connect to the wireless. It showed the connection as available but wouldn't connect. I was able to connect to the wifi at a restaurant fine. After 2 or 3 days it started working again. Then the exact same problem the next week after I came back after being gone a couple of days over the weekend. I reset the router (just unplugged it for a second from the power source) and the problem was solved (I assume someone else reset it the week before when it "magically" started working again).  A couple weeks later I had the same problem (this time I wasn't gone a few days) I reset the router but then the problem occurred again the same day and I left if for about a week before finally resetting it again and it is currently working.I have Googled this and it seems to be a common problem but there seems to be several reasons for this depending on the particular setup.

I have tried booting from a usb stick running the original version that I installed to see if I have added some software or update since that is causing this issue but this doesn't help. I live in a house where the rooms in the upstairs are rented out (one being mine) so the router and everything is just a home setup. When my Ubuntu won't connect everyone else seems to be able to use their Windows fine. Reseting the router seems to work but it is in the landlords living area so I can't be running down there and reseting it all the time.

Problem seems to be recent after working fine from August till mid January. Doesn't seem to be related to any updates or system changes since the original release I installed from doesn't work either. And the router seems to work fine for everyone running Windows.

The router is a Linkys Wireless -G WRT54G and my computer is Ubuntu 10.04 on a HP G60-117US with Integrated 10/100 Ethernet LAN.[ Product Specifications]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01570465&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&site=null&key=null&product=3807267")

---

### Post by uncaspi on 2011-02-23
Try to switch off power save mode and increase transmit power.

sudo iwconfig wlan0 power off txpower 20

assuming your card is wlan0

---

### Post by Jwiere03 on 2011-02-25
> Try to switch off power save mode and increase transmit power.

sudo iwconfig wlan0 power off txpower 20

assuming your card is wlan0

Thanks for the reply, it went down again and so I tried this and got nothing. I reset the router again and it connects fine. I had a ton of trouble when I had Windows on this machine (with other stuff never connecting) and Ubuntu has been awesome, till now. All the Windows in the house seem to connect fine but this is getting to be an at least once weekly sometimes more occurrence for me.

---

### Post by Paulahar on 2011-02-26
I have had the same trouble, I have had no problems logging on with the Wireless network until around the same time in August, It connects and then disconnects straight away, I have to shut down and restart around 5 times before it becomes stable., the boys in the house have no trouble, (they are using windows).  I am just wondering if there were any updates around that time which may have a bug in them.

---

### Post by Jwiere03 on 2011-02-26
> **Paulahar said:**
> I have had the same trouble, I have had no problems logging on with the Wireless network until around the same time in August, It connects and then disconnects straight away, I have to shut down and restart around 5 times before it becomes stable., the boys in the house have no trouble, (they are using windows).  I am just wondering if there were any updates around that time which may have a bug in them.

 I was thinking the same thing but I booted off a usb stick with the original version I installed from (that worked no problem for several months) and that didn't work either so that seems to rule out any updates to Ubuntu

---

### Post by Jwiere03 on 2011-02-27
Once in the past when I was having trouble I tried moving the computer closer to the router but this made no difference. I guess I am not surprised because it seems to show the connection fine when looking at avalible networks, just can't connect

---

### Post by Jwiere03 on 2011-02-28
I stated in my original post that the first time my connection wouldn't work I was still able to use the wifi at restaurants. Since I made my original post it has gone done again. I currently can't connection to the router in my own home. But there is a unprotected connection available that I have never seen before (there are several wireless connections that I pick up but the rest are all protected) I think this is a small coffee shop nearby. I can connect to this fine and am actually using this connection to post right now.

 It is weired because I seem to be able to connect to other connections fine and if I reset the router I can reestablish a connection to our router (sometimes only lasts for a few hours). So the problem seems to be between my computer and this particular router/connection but the problem isn't continuous as it works for a while after reseting the router.

---

### Post by Paulahar on 2011-02-28
> **Jwiere03 said:**
> I was thinking the same thing but I booted off a usb stick with the original version I installed from (that worked no problem for several months) and that didn't work either so that seems to rule out any updates to Ubuntu


I am using a USB Tenda 54Mbps, I am wondering if it is powerful enough as there are a quite a few new wireless connections coming up in my area, which could be causing interference, if anyone knows if this could be the case let me know, or which USB works best with Ubuntu/Linux,(through AOL)

---

### Post by Jwiere03 on 2011-03-01
> Try to switch off power save mode and increase transmit power.> there is a unprotected connection available that I have never seen  before (there are several wireless connections that I pick up but the  rest are all protected) I think this is a small coffee shop nearby. I  can connect to this fine > I am wondering if it is powerful enough as there are a quite a few new  wireless connections coming up in my area, which could be causing  interference I had never seen this particular network till after I increased the transmit power. Probably not a coincidence, I have several connections with in range but this one is a couple blocks away and now I can connect after doing this. But can't connect to the one that is one story below my room :confused:

---

### Post by Jwiere03 on 2011-03-02
Tried lowering my transmit power to see if maybe all the avaliblle networks were causing some kind of interference or something, knowing my strongest avalible was the desired one. No help, even after going back up to 20 I can't find the coffee shop one I was able to connect on. Obviously this problem is more complicated then I first thought since everyone on this board is as stumped as me. Maybe time to reconsider Ubuntu

---

### Post by Paulahar on 2011-03-13
Just wanted to let you all know that my problem was only the Tenda USB, (faulty), put in a netgear USB and all working fine now.

---

