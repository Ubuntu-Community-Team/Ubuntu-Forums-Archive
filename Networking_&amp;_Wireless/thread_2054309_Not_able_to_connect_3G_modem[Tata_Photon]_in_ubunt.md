---
title: "Not able to connect 3G modem[Tata Photon] in ubuntu 12.04LTS"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by himanshupradhan on 2012-09-07
Hi, i am following the method given in ubuntu documentation but not able to connect properly.
is there any other way.
It gets connected for a second and that disconnect
 
**Mobile Broadband**
 
 
 
 
*Mobile Broadband* means any kind of high speed Internet connection which is provided by an external device such as a 3G USB stick or mobile phone with built-in HSPA/UMTS/GPRS data connection. Some laptops have recently been produced with mobile broadband devices already inside them. 

Most mobile broadband devices should be recognised automatically when you connect them to your computer. Ubuntu will prompt you to configure the device. [LIST=1]
[*]The *New Mobile Broadband Connection* wizard will open automatically when you connect the device.
[*]Click **Forward** and insert your details, including the country where your Mobile Broadband device was issued, the network provider and type of connection (for example, *Contract* or *pre-pay*).
[*]Give your connection a name (it is up to you what name you choose) and click **Apply**.
[*]Your connection is now ready to use. To connect, click the Network Manager icon in the top right of the panel and select your new connection.
[*]To disconnect, left click the Network Manager icon in the top right of the panel and click **Disconnect**.
[/LIST]If you are not prompted to configure the device when you connect it, it may still be recognised by Ubuntu. In such cases you can add the connection manually. [LIST=1]
[*]Right-click the Network Manager icon in the system notification area and click *Edit Connections*
[*]Select the *Mobile Broadband* tab.
[*]Click **Add**.
[*]This should open the *New Mobile Broadband Connection* wizard. Enter your details as described above.
[/LIST]Thanks

---

### Post by p1977p on 2012-10-14
In the Edit Connections, have you changed the APN setting?  I think it is tata.docomo.internet for GPRS/EDGE and tatadocomo3g for 3G.

---

