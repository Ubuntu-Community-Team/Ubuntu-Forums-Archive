---
title: "Wireless card"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by Chad256 on 2010-04-11
So I've decided I want to cross over to Ubuntu from Win vista but there's one thing i cant get working. My wireless card.

My wireless card is a Xterasys xn 2523g

I can't make this switch until i have the internet working please help.

---

### Post by chili555 on 2010-04-11
You will need to use ndiswrapper to get your card going.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I have thoughtfully located the Windows drivers and have attached the file. Download the file to your desktop and right-click it and select Extract Here. A folder will be created containing the .inf file you need. Post back if you get stuck.

---

### Post by Chad256 on 2010-04-11
Thanks for the drivers.:) the problem is that I don't know how to install/use ndiswrapper could you explain it in a very simple way?

---

### Post by chili555 on 2010-04-11
Do you have internet access on the computer? If so, please open a terminal and do:```
sudo apt-get install ndisgtk
```That will install ndiswrapper and it's dependencies for you. Then you will be able to go to System > Administration > Windows Wireless Drivers and ask it to install your driver. Navigate it to your desktop and the folder that was created when you extracted the file I sent. All the dirty work will be done for you.

---

### Post by Chad256 on 2010-04-11
No internet acess on that computer I've download the 3 packages and installed ndiswrapper util but I don't know how to do the other two

---

### Post by steveneddy on 2010-04-11
> **Chad256 said:**
> No internet acess on that computer I've download the 3 packages and installed ndiswrapper util but I don't know how to do the other two

No Ethernet connection?

---

### Post by chili555 on 2010-04-11
If you have all three, install the other two the same way. I assume you got .deb files. If they are on your desktop, just do:```
cd Desktop
sudo dpkg -i ndis*.deb
```Or, you could probably right-click them and select Install with package manager.

---

### Post by Chad256 on 2010-04-11
No I downloaded the packages on another computer

---

### Post by Chad256 on 2010-04-11
The other two are tar.gz

---

### Post by chili555 on 2010-04-11
> **Chad256 said:**
> No I downloaded the packages on another computerWell, that won't do us much good, will it. Can you transfer them on a USB key or burn a CD?

---

### Post by Chad256 on 2010-04-11
I did transfer it over and install it (forgot to mention the transferring part)

Edit: found those .deb files going to go try it.

Edit2: IT WORKS!! This is awesome! Thanks a Million!

---

### Post by chili555 on 2010-04-11
Good work! Have fun and welcome to the Ubuntu party.

---

