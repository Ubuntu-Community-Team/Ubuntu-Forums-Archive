---
title: "Connecting to windows wirless network"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by scrutineer on 2009-05-21
I have Ubuntu 8.04 loaded on my Acer Aspire 3623WXCi laptop. How do I manually connect to a wireless network that is available? Isnt there a way that Ubuntu can automatically detect the network settings and just connect ?

I tried entering the details given from the windows server in the wlanO Properties dialog box. With no success yet.

I want to access the internet via this network.

Your input will be appreciated. :p

---

### Post by dandnsmith on 2009-05-21
Are you trying to connect to the server, or to a (wireless) router which provides the internet connection to the network ?

Either way you need to have the interface up and running - what does the network manager icon in the 'task bar' show?

---

### Post by superprash2003 on 2009-05-21
there is a network icon in the top bar in ubuntu , usually once you click on that , you would get a dropdown of available wifi networks , choose the appropriate one and enter the securtiy key and you should be done , if you dont see the dropdown of wifi networks , it could be because your wifi isnt detected yet , if so post output of **lshw -C network** from the ubuntu terminal

---

### Post by scrutineer on 2009-06-01
@dandnsmith - im trying to connect to the modem which acts as a wireless router, if im not mistaken, to access the internet. I heard about Feisty Network manager, will this help to solve the problem ?

@superprash2003 - no available wireless network are detected. If I click on the network Icon, it gives shows 2 options in is wireless networks, which is dimmed out and not available, the other is manual configuration.

If i type the command in the terminal it says "command not found"

I doubt that im typing incorrectly, but I used the syntax you gave.:(

---

### Post by superprash2003 on 2009-06-01
did you use a captial C its not lshw -c network , it is **lshw -C network**

---

### Post by scrutineer on 2009-06-02
Geez, windows seems stupid. I cant open a simple linux text file in windows.

How can I copy the terminals output to a text document that will open in windows ?

---

### Post by superprash2003 on 2009-06-03
to copy output of ifconfig to output.txt you have to type ifconfig > output.txt

---

### Post by scrutineer on 2009-06-26
> **superprash2003 said:**
> to copy output of ifconfig to output.txt you have to type ifconfig > output.txt

You said I must get the output **lshw -C network**

If I type ifconfig > output.txt it does not do anything.:confused:

---

