---
title: "Change channel sript w/o using digits"
date: 2009-04-22
forum: Mythbuntu
---

### Post by Red Bow Tie on 2009-04-22
The satellite service I subscribe to is RTN. It uses an Echostar 2700 receiver and remote, however, I cannot change channels on this receiver by pressing the digits. Instead I must press the "up" and "down" buttons and in this way go through the channels one by one (there are only 40 channels total) or I can press the "Guide" button and only then use the "page up" and "page down" to skip channels in between. I need to keep doing this until i get to the page that has the channel I want to view then use the "up" or "down" button to zero in on the particular channel I want to view.  I must then press the "select" button and the channel comes on.

Every channel change script seems to take for granted that I can use the digits on the keypad (which has no effect even with the original remote)
Is there a script that I can use to program my IR blaster to send the "up" and "down", PageUp and PageDown, Guide and Menu buttons to the STB?
Remember the Page Up and PageDown buttons only work after I press Menu and get the channel data on screen.

I have a Hauppauge PVR-150 MCE kit that comes with a MCE USB Remote and an IR transmitter (or blaster) that plugs into the back of the USB Receiver. The blaster sits directly in front of the STB receiver.

I have chosen Windows Media Center Remote new version and Windows Media Center V2 (usb) Dish Receiver as my transmitter.

I can successfully change channels directly from the command line by typing 

irsend SEND_ONCE dish up 

or any other command by substituting "up" with "down" "guide" or "page up" and "page down". but have NO IDEA how to script this. as all the scripts have the digits channel change method.

Could someone please help me with this peculiar setup?

BTW there is no channel guide either so I can't use that. All channels come up as unknown.

---

### Post by Red Bow Tie on 2009-05-14
My error. Digits can be used. They must be preceded by either one zero or two zeros depending on whether you want channels below 10 or above 10.

---

