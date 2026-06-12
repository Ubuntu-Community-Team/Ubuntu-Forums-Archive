---
title: "Option for Shared Key gone in Karmic Network Manager?"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by nlippincott on 2009-11-25
I have tried for several days to install Karmic on an Acer Aspire 5100 which was previously running Jaunty. I simply cannot get Network Manager to connect to my wireless network, where it was able to do so flawlessly under Jaunty.

There is one thing I had always had to do when connecting to my wireless network. When putting in the WEP key, I always had to change an option from "Open System" to "Shared Key". With the "Open System" option, the Network Manager icon would just sit there and spin, and spin, and spin, until, finally, it would ask me for the key again. Change the option to "Shared Key", and Network Manager connects just fine.

Now, with Karmic, that option is gone. The only thing it asks for is the WEP key (and an option as to whether or not the key should be displayed as it is typed). I put in the key, click "Connect", and the icon spins, and spins, and spins, and eventually asks for the key again.

It is exhibiting behavior identical to that of Jaunty with the "Open System" option. However, there is no option to switch to "Shared Key".

I have tried searching for solutions, but cannot find anything. I can't imagine I am the only one running in to this problem.

I feel as though I am missing something that should be blatantly obvious.

I have two other laptops which have been upgraded from Jaunty to Karmic. They connect just fine, however, I did not have to put in the WEP key on those systems - they were set up successfully prior to the conversion.

Although I would love to spend another week or so trying to get this system working, it is not mine, and needs to go back to its user. I have dropped back to Jaunty, and I am instruction the user, "do not upgrade". I mention this because I know someone will likely ask me to post the network configuration files. I no longer have them. However, if someone can tell me that thing I am missing that should be completely obvious, please pass it along.

This really ought to be simple, especially if Ubuntu is to be considered a viable alternative to Windows.

---

### Post by Brandon Williams on 2009-11-26
Right-click on the network manager icon in your status tray and select 'Edit connections...'. Does the ssid for your network show up on the wireless tab? If it does, select it and click edit; otherwise, click add. On the 'wireless security' tab, you'll see the option you describe.

---

