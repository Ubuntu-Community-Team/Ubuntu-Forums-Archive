---
title: "Realtek 8192su wireless on 64bit system"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by tammerlane on 2010-07-05
I have a Realtek 8192su wireless usb receiver. I have been unable to run it on 64bit Ubuntu, or any of it's derivatives that I have tried - and I have tried a few. It works on Windows 7 64bit. On Ubuntu and the derivatives I have used the ndiswrapper. It works on some 32bit derivatives and NO 64bit derivatives. I cannot plug into the router as it is another building. I have tried many of the solutions I have read here and in other forums. NONE have worked on 64bit. I have come to two possibilities - a problem with Ubuntu 64bit or the drivers supplied by Realtek.

BTW I can use terminal input (cli) if all steps are provided, but I am more comfortable with GUI. I have the Realtek supplied Windows drivers and a zip file with a bunch of stuff, including the targz with the Linux driver, also supplied by Realtek. I don't have a clue what to do with the zip file or the targz.

 
Can anyone help? tammerlane

---

### Post by imahuph on 2010-07-05
I have used the realtek linux driver it works quite well just extract the realtek tar.gz go into terminal  cd to the directery that you extracted them to sudo make and sudo make install, wireless should work

---

### Post by tammerlane on 2010-07-05
Thank you for your reply. I have some questions, please. Did you install them on Ubuntu 64bit? I have used ndiswrapper on Ubuntu 32bit derivatives, but have been unable to get the 8192su working on 64bit. Additionally, I have a zip file full of stuff from Realtek. In it is included the rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20100625.tar.gz driver. I don't have a clue what to do with any of that. I would need step-by-step instructions, along with the exact cli coding. I am a noob.

---

### Post by tammerlane on 2010-07-07
Hello. Anyone have any ideas? Please. Thanx, tammerlane.

---

