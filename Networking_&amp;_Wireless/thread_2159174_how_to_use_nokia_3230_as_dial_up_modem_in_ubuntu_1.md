---
title: "how to use nokia 3230 as dial up modem in ubuntu 12.04 lts 64bit"
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by push159 on 2013-07-02
hello.! I just installed ubuntu 12.04 lts 64 bit version to pc. I want to use internet in ubuntu by using my nokia 3230 as dial up modem via usb (dku-2). How can i do this. Please help. I want it as soon as possible. Please

---

### Post by Irihapeti on 2013-07-02
*Thread moved to **Networking & Wireless**.*

---

### Post by Irihapeti on 2013-07-02
I've used the 6120c successfully as a modem. It uses a later version of Symbian, which may or may not make a difference. I've only used 12.04 32-bit, which I don't think should affect things.

Assuming it behaves the same as the 6120c, you would plug the USB cable into the phone, and then the other end into the PC. When the phone asks how you want to connect it, select PC Suite. (If it doesn't use PC Suite, then unfortunately I'm unable to help.)


Then you can use Network Manager to define a new mobile broadband connection. There's a wizard which should make it fairly straightforward. Once you have everything setup and saved, you can use Network Manager to connect and disconnect. The broadband connection only becomes accessible when you have the phone plugged in to the computer.

---

### Post by varunendra on 2013-07-03
Like Irihapeti mentioned above, you will have to enable the modem mode from inside the phone when the connection to PC is detected. Once that is done, Ubuntu will have no problem in configuring it with the wizard.

Alternatively, you can get a cheap bluetooth dongle (if the pc doesn't already have it) and connect the phone as a bluetooth modem (using the same wizard). Make sure though that your phone supports "modem" or "dun (dial up network)" mode over bluetooth. Even the cheapest kind of bluetooth dongle can easily handle the speed that a gprs connection can possibly deliver.

---

### Post by push159 on 2013-07-11
thanks Irihapati, i got it. really much faster internet in ubuntu than windows.

---

