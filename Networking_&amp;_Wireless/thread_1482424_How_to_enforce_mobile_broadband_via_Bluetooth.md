---
title: "How to enforce mobile broadband via Bluetooth ?"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by skatebiker on 2010-05-13
Hi,

I have Ubuntu gnome 10.04 'lucid' and I can connect with Mobile Broadband internet by using my Nokia 5800 as an USB dongle by just setting the right "Mobile Broadband" settings parameters. It connects flawlessly.

Then I set the /etc/rfcomm0 file with the proper parameters with the Bluetooth MAC address and the proper channel and paired the phone with my PC of course.

But how can I enforce the network manager that it selects Bluetooth instead of USB ?

---

### Post by AlanR8 on 2010-05-13
I connect my Nokia Navigator via blue tooth all the time and it just works.

I had to install blueman because the default blue tooth program does not seem to have the functionality required.

With blueman installed, open it pair, your phone and then right click the phone, select "Serial Ports" then "Dial up Networking" The phone should connect and you'll see a green dot on the blue tooth icon in the upper pane. 

Give it a moment or two, left click on your network icon and you should see an entry in the menu to create a new mobile connection, or it might offer you the option to connect straight away to your phone depending if you've already set up the connection.

Let us know how you get on.

---

### Post by chiefwiggum2k on 2010-05-13
thanks for the info. i am on a 20 yr old 'netbook' with USB 1.0... worked a treat. interestingly tho, did speed check with phone on USB cable(BBC website) and it was 2 - 2.2 Mbps. managed to connect via bluetooth after following your easy instructions and did speed check again and it is now 0.9 Mbps. I realise USB port is restrictive but i am surprised that bluetooth has slowed it down that much. Gonna do same test on desktop to see if any different

---

### Post by skatebiker on 2010-05-14
I installed these tools as well and I ran blueman-assistant and selected 'Connect DUN on device' and it conncted but still the network manager does not show the 'Mobile broadband'.
How can I enforce the NM that it shows the mobile broadband when the BT DUN is connected ?

---

