---
title: "Telstra Next G Modem and Ubuntu 10.4"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by onetruth on 2010-10-04
[FONT=Verdana]Hi,

Can anyone give me some directions on how to run my telstra next g usb modem in ubuntu 10.4? 

Thanks.
[/FONT]

---

### Post by dineshs on 2010-10-04
Can you post the results of```
lsusb
```
```
dmesg | grep tty
```

---

### Post by onetruth on 2010-10-04
> **dineshs said:**
> Can you post the results of```
lsusb
```
```
dmesg | grep tty
```
Hi dineshs,

I apologise for my ignorance, but I'm not sure what to make of your message. Can you explain in further detail what you mean?

Thanks.

---

### Post by TopEnder on 2010-10-05
> **onetruth said:**
> Hi dineshs,

I apologise for my ignorance, but I'm not sure what to make of your message. Can you explain in further detail what you mean?

Thanks.
What dineshs would like is the output for:
lsusb ,   and
dmesg | grep tty

To do this type these codes in a terminal, to open a terminal by: Applications/Assessories/terminal  and post the output in your next post.

---

### Post by tuffs on 2010-11-19
I recently had a problem in connecting to the net with my Telstra Next G USB modem. Here are the steps which solved my problem.
. Right button clicked on the **network icon** in the top panel.
. Select the **Edit Connections** item.
. Click the **Mobile Broadband** tab, then click the **Telstra Next G** item to highlight it.
. Then click **Edit**. A dialogue box will open up.
. Make sure you have *99# in **Number**, ....@bigpond.com in **Username**, your password in **Password**.
. In **APN**, delete **telestra.internet** and replace it with **telestra.bigpond**. 
.Then click **Apply**.
Hope this fixes your problems.:)

---

