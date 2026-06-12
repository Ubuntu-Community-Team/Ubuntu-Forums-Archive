---
title: "Need help connecting to Wireless in Kubuntu Lucid"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by Losgann Mor on 2010-05-14
Greetings,

I'm having trouble connecting to our home wireless network in Kubuntu Lucid. I was hoping someone here might be able to help. I can connect with no problem in Ubuntu and Xubuntu; I'm having difficulty in Kubuntu only. It might just be me being unfamiliar with the KDE network management app, I don't know.

Anyway, here is what happens:
1. I click on the network icon in the system tray, and choose "manage connections". I click on the "wireless" tab, and click "add".
2. I enter the name of our network in the SSID field (our router doesn't broadcast its SSID; however, if I click "scan" the neighbors' wireless networks do appear in the list) under the "wireless" tab, then I go the "wireless security" tab, and choose "WPA/WPA2 - personal" and enter the password. I click OK.
3. Now when I right-click on the network icon and choose "create network connection", the new connection for our network that I just made shows up in the list, but it has an icon showing a pen on paper instead of the broadcasting signal icon that appears next to the neighboring networks. It also says my connection is "insecure", even though I chose WPA and put in the password. (Neighbors' networks do say WPA, WEP,etc.)
4. I select my network connection that I created above, and click connect, and nothing happens. No connection is created.

Like I said, the problem may well be that I'm not figuring out how the KDE network app works; I've used mostly XFCE and GNOME in the past, but I've heard good things about Kubuntu Lucid and really would like to take it for a spin. However, this computer has only a wireless connection, so I really need to get it working. Any help would be greatly appreciated.

Thanks!

---

### Post by Nick_Jinn on 2010-05-14
I ALWAYS have wireless problems with every clean install of linux....there are proprietary drivers that for some dumb reason are excluded for philosophical reasons....they should really just download automatically if you have a direct connection, along with updates, because 99 out of 100 users dont give a **** about proprietary restrictions as long as the program works.



It should be as easy as enabling those drivers. Maybe start with a direct connection and then go wireless after you get the drivers you need.....anyone else want to walk him through this?

---

### Post by Losgann Mor on 2010-05-14
Hi, thanks for the reply.

I could be wrong, but I don't think drivers are the issue &#8212; it it was a driver problem then I wouldn't be seeing any wireless connections are all, right? And Kubuntu sees my wireless adapter, and picks up the broadcasts SSIDs of the networks of the folks next door, across the street, etc.; it just won't connect me to my own network, for some reason that I can't figure out. I'm assuming I must have done something incorrectly when trying to set it up, but I can't figure out what. 

Also, as I mentioned, I can connect to my network out of the box in Ubuntu Lucid and Xubuntu Lucid simply by typing in the SSID and WPA password of the network, which makes me think the issue must be something in KDE or Kubuntu, but I have no idea what it could be or why it should be so.

---

### Post by Losgann Mor on 2010-05-14
Well, I've been coming back to this off and on during the day, and doing a lot of googling and such, and it seems that it is in fact a KDE issue. KDE's network manager app won't connect to wireless access points with a hidden SSID. If I set the router to broadcast the SSID, then when I click on the network manager icon, I just select my network from the list that pops up, it prompts me to enter the WPA password, and then I'm connected and good to go. 

I'm not really happy with the solution of having to broadcast my SSID to the world in order to be able to get on the internet, though hopefully having WPA makes it a bit safer.

---

### Post by a_flj_ on 2011-01-22
You don't have to keep your router broadcasting the SSID. For some reason, k network manager only has to connect once to a wireless network when it's visible, and will connect problemless afterwards, if you have it hide its SSID again. I know this because I have to shoo/hide the SSID whenever I introduce a new device to my home network.

---

