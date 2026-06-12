---
title: "Installing Brother MFC 9120"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by carloscmt on 2011-04-20
I recently purchased a brother MFC 9120 and do not know how to install the scanner driver and make it work when connected to the network. I was able to install the printer driver very easy though. I am a beginner. How do I install it over the network? brother website does offer a linux driver. But do not know how to install it and scan over network.

---

### Post by RockOut on 2011-08-13
> **carloscmt said:**
> I recently purchased a brother MFC 9120 and do not know how to install the scanner driver and make it work when connected to the network. I was able to install the printer driver very easy though. I am a beginner. How do I install it over the network? brother website does offer a linux driver. But do not know how to install it and scan over network.


I have the same problem. 

Here is what I know:

* Download the Angry IP scanner from its website and install it.

* Open the Angry IP scanner program and scan youir local network from 192.168.1.1 -m 192.168.1.254. You should now be able to determine the IP address of your network 9120 printer/scanner.

* Using Firefox, type in your Brother 9120's IP address.

* Here you will be prompted for a password. Brother's defaults are user:admin, pass:access.

* When you are logged in, there is a "Administration" link. Here you can find the network settings.

I am currently trying to figure out how to configure my network to accomodate the new settings. Once I find out, I'll post my results.

---

### Post by demonipuch on 2011-08-14
> **carloscmt said:**
> I recently purchased a brother MFC 9120 and do not know how to install the scanner driver and make it work when connected to the network. I was able to install the printer driver very easy though. I am a beginner. How do I install it over the network? brother website does offer a linux driver. But do not know how to install it and scan over network.

Hello

Look at this page on Brother's website : [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html)

---

### Post by RockOut on 2011-10-26
The tutorial from brother did not work. Not sure what I did wrong. the brconfig3 file did not contain data. Not sure where I went wrong

---

### Post by kurt18947 on 2011-10-26
What version of Ubuntu are you using?  There's an issue with Brother scanners in 11.10.  It's documented here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101). I've had quite good success installing a Brscan3 machine via network.  When adding the line "brsaneconfig3  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx" the model must be in cap letters e.g. MFC-9120 and no parentheses.

---

### Post by RockOut on 2011-10-26
I am on 10.04.

I'm not sure what's gone wrong. I am currently reinstalling 10.04 LTS Ubuntu Server (with Desktop GUI) in order to try to fix this issue.

The thing is this printer DOES include an option to Scan to FTP. However, I doubt that I set up our FTP server properly. Has anyone had luck getting Scan to FTP working on the brother printers? I think this setup may be easier to do instead of trying to scan directly to XSANE via the network or something.

---

