---
title: "Installin NETGEAR WG111T [Help]"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by splinta on 2005-12-10
Hi..

I am super noob to linux, after few months i found out how to get ubuntu & windows xp to work on both hard drives on my pc..

but now i am tryin 2 find out how to use my wireless USB adapter 2 connect 2 my router in order 2 use my internet...

Can someone show me steps of installing my adapter on Ubuntu 5.10?

Thanks,
Faris..

---

### Post by chambery on 2005-12-10
Hi,

I just installed the driver WG111 using [ndisgtk]("http://spohlenz.blogspot.com/2005/08/ndisgtk-in-universe.html") ndiswrapper tool.  It uses the Windows driver (something.inf, I think) off the CD/website to communicate with the adapter.  Once installed it should appear as an adapter in the Network Configuration tool.  Set the properties there, activate, and you should be good to go. 

Good luck,

Todd

---

### Post by chambery on 2005-12-10
I forgot to mention that ndisgtk is available through Synaptic...

---

### Post by splinta on 2005-12-10
lol.. ok i re-edited this post again cos now i have found out where everything was.... i now installed ndisgtk from Synaptic Package Manager...

how do use ndisgtk to install my netgear adapter, then how do i use my adapter to connect on a secured router to the internet? It's current secruity i set it to is WEP.

---

### Post by splinta on 2005-12-11
if found my way through this, and now i kinda got a bit further into, and i was tryin 2 install this *.inf file but problem is, ndiswrapper says these drivers are invaild and they came from ndiswrapper@sourceforge page

proof :)

[IMG]http://i8.photobucket.com/albums/a13/splinta/Untitled.gif[/IMG]

please help if u can...

thanks..

---

### Post by hamil on 2005-12-11
Go to netgears homepage, downlod the latest drivers for your card, and make sure that it is the correct card you download.
Unzip it, and put the winxp folder someplace in your homefolder. point ndiswrapper to the .inf file. It made the trick for me. (even though I can not get ndiswrapper to work...)

---

### Post by splinta on 2005-12-11
well, i have tried the latest verison of this driver wit ndiswrapper and it gave me invalid drivers... but i will keep trying....

but if any one can help any more, do please post... :)

---

### Post by ORF1000 on 2006-07-29
To get the WG111T to work you need to download and install the latest stable ndiswrapper from source.  The version in the Ubuntu repository accessible through synaptic is way out of date.  [It's not hard -- just follow these instructions.]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")  Go to section 4. You will probably need to install the Windows drivers from the command line as instructed, rather than the gtk graphical interface.  Also, you do need to install both Windows drivers, (athfmwdl.inf and netwg11t.inf) although the system will only indicate "Hardware installed" for one.

---

