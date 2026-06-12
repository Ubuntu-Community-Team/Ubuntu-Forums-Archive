---
title: "Febsmart Modem detected not connecting"
date: 2019-02-05
forum: MINT
---

### Post by vampiregoat69 on 2019-02-05
[COLOR=#333333][FONT=&quot]Just bought a Febsmart FS-N600HP wireless PCI-card and installed it in the hopes it would work fine with Linux Mint or any Linux distro just to find it detects it and my internet but will not connect no matter what. I am new to Linux coming from windows and I tried what little knowledge I could find online to get it going. The Windows drivers worked well in windows but the disk just sends you to some website and tries poorly to tell you sort of how to do it. I do not know how to compile anything or make a driver that works. It even said Mint has Ndiswrapper and use that, but NO distro I downloaded even has it unless you connect to the internet and install it.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]This is where my problem is I do not have a way to direct connect as my router is in the other end of my trailer. Any help would be VERY much appreciated as I want to leave Windows for good and use Linux Mint for life if possible but all this headache does not make me want to leave windows because windows is plug and play and done and walk away.[/FONT][/COLOR]

---

### Post by Autodave on 2019-02-05
According to what I am finding, there should be nothing that you have to install to get that working.  Please tell us exactly what version of Linux that you are using.

What happens when you click on the internet link?  If it is seen there, all you should have to do would be to select your wireless network and enter the passphrase for the modem.

---

### Post by vampiregoat69 on 2019-02-05
Using Linux mint 19 (I know this is Ubuntu forums I am cross posting in hopes of help) it shows my networks but when I click connect it says an error message that it can't connect. I enter passphrase and looks all good then just does nothing no connection no matter what I do.
More info from running lspci:03:00.0 Network controller: Qualcomm Atheros AR93xx Wireless Network Adapter (rev 01)


thank you Autodave for any help

---

### Post by oldos2er on 2019-02-05
Thread moved to MINT.

---

### Post by Autodave on 2019-02-06
Just a thought since I have run into this twice before.  Instead of enetering your passphrase, first make a text document and type your passphrase into that.  When prompted for your passphrase for the modem, copy and paste it into the box.

I have a Dell laptop here and that is the ONLY way that it will accept the passphrase.  It's worth the try.-

---

### Post by vampiregoat69 on 2019-02-06
I will try that now here is hoping it works.

Edit:This did nothing as well I enter password, double click on the EXT or my other Centurylink one and get this.[IMG]http://i64.tinypic.com/501c0h.png[/IMG]

---

### Post by dave157 on 2019-03-06
If this is the pcie card he purchased 

[https://www.amazon.com/gp/aw/d/B071NZ6DL9/ref=sspa_mw_detail_3?ie=UTF8&psc=1](https://www.amazon.com/gp/aw/d/B071NZ6DL9/ref=sspa_mw_detail_3?ie=UTF8&psc=1)

I own one and it works out of the box in 18.04. Check if the poxy is active. The wifi card is working cause you can see the ssid's.  Maybe the keyboard has bad or struck keys.

---

### Post by dave157 on 2019-03-07
Try to connrct to the CenturyLink that does not have the EXT see if it connects.

---

