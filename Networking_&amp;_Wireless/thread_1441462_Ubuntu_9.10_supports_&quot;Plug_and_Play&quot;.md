---
title: "Ubuntu 9.10 supports &quot;Plug and Play&quot; ?"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by pumber on 2010-03-28
I am now running Ubuntu 9.10 with wired network .

Now, I want to use a USB wifi adapter to connect Internet.

As the Ubuntu 9.10 is already set up,what can I do to make the USB wifi adapter work ??Will it automatically detect my device and search for driver to install ?

Thank you !

---

### Post by chili555 on 2010-03-28
It depends. Some wireless devices are well supported, some require a wrapper to use Windows drivers and a very few are difficult to impossible to trick into life. I suggest you check here before you click 'Add to Cart.'

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by pumber on 2010-03-28
> **chili555 said:**
> It depends. Some wireless devices are well supported, some require a wrapper to use Windows drivers and a very few are difficult to impossible to trick into life. I suggest you check here before you click 'Add to Cart.'

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Thank you !

In fact, I know that for the brand of my USB wifi adapter, if I insert the USB adapter [COLOR="Red"]before[/COLOR] I install Ubuntu , it will automatically load the driver. So, will it be the same if now I insert the usb wifi adapter [COLOR="Red"]after[/COLOR] I install Ubuntu ?

---

### Post by chili555 on 2010-03-28
> So, will it be the same if now I insert the usb wifi adapter after I install Ubuntu ?Yes. Drivers are built in to the kernel so that when you insert the device and it is recognized, the driver is loaded automagically.

There are no absolutes in life, but that is how it works in the great majority of cases. Certainly in the five wireless cards I have or have had.

---

### Post by pumber on 2010-03-28
> **chili555 said:**
> Yes. Drivers are built in to the kernel so that when you insert the device and it is recognized, the driver is loaded automagically.

There are no absolutes in life, but that is how it works in the great majority of cases. Certainly in the five wireless cards I have or have had.
  Thank you for your information.

Do i have to choose " Add new hardware " or Ubuntu will prompt me  a window to ask for the new hardware ?

Thank you !

---

### Post by chili555 on 2010-03-28
> In fact, I know that for the brand of my USB wifi adapter, if I insert the USB adapter before I install Ubuntu , it will automatically load the driver.Stick it in and, if it is supported as you say, click the Network Manager icon, see your network, click Connect and you will be prompted for your WEP or WPA details and enjoy. 

If you are in any doubt about your devices support, download the Ubuntu CD and run it 'live,' that is, running from your CD drive and *not* installed on your harddrive, and see if it works as expected.

Of course, you can search for the model of the device on this forum for others' experiences. Not many users, however, post to report that it "just works."

---

