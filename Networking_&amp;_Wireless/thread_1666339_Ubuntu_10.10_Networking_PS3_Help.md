---
title: "Ubuntu 10.10 Networking PS3 Help"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by Scion_of_Cthulhu on 2011-01-13
Hi, not sure if this would go here or the gaming section.

I am running Ubuntu 10.10 and I have been trying to connect my PS3 to it for the last few days.

My laptop is connected wirelessly to my college network. My PS3 is NOT able to connect to it because of all the encryption methods. So instead I have it connected with an Ethernet cable to my laptop. 

I was able to connect this way when I was running windows. Can anyone help me?

---

### Post by Sylslay on 2011-01-13
1. Install "firestarer" as fierwall and share inetrent from wlan0 to etho,(they are on list when runnig Wizzard in firestarter. Most important, edit network conetction in netwokrmanager and mark "aviable for all users"


2. If You need play media files form lapotp/network, 
You need install DLNA Server. I inastalled on 10.10

Therea 3 diffrent brands.
Most easy for setup IMHO, was

[COLOR="Blue"][SIZE="3"]minidlna[/SIZE][/COLOR]

Install in fiew steps:

sudo add-apt-repository ppa:stedy6/stedy-minidna
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install minidlna

Then configure:
all settingas are at:

sudo gedit /etc/minidlna.conf

media_dir=V,/home/abc/Video
media_dir=A,/home/abc/Music
media_dir=P,/home/abc/Picture

[COLOR="Lime"]where abc is "any name"[/COLOR] of local DLNA media server.
Video, Music, Picture are  "share-folder" with autoscan-all-files 
after reboot or sudo /etc/init.d/minidlna restart 

It works perfect with Samsung TV. 7000 series.

3. Check these WEP setings for ps3, and You can stream all media form pc to ps3 by wireless network. 

Worth to tray

PS. I wasn't able to add media content to mediathomb, sorry.

---

### Post by inobe on 2011-01-13
> **Scion_of_Cthulhu said:**
> Hi, not sure if this would go here or the gaming section.

I am running Ubuntu 10.10 and I have been trying to connect my PS3 to it for the last few days.

My laptop is connected wirelessly to my college network. My PS3 is NOT able to connect to it because of all the encryption methods. So instead I have it connected with an Ethernet cable to my laptop. 

I was able to connect this way when I was running windows. Can anyone help me?

mediatomb, it's in the repos, you can get it from synaptic.

here is all the information.

[http://mediatomb.cc/](http://mediatomb.cc/)

---

### Post by Scion_of_Cthulhu on 2011-01-14
> **Sylslay said:**
> 1. Install "firestarer" as fierwall and share inetrent from wlan0 to etho,(they are on list when runnig Wizzard in firestarter. Most important, edit network conetction in netwokrmanager and mark "aviable for all users"


I have tried the Firestarter method and for some reason it says it can't detect anything connected to the other end of my ethernet cable. My laptop detects it though. Any idea why?

---

