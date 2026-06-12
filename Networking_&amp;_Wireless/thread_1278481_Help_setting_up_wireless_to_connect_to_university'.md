---
title: "Help setting up wireless to connect to university's network"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by allspiritseve on 2009-09-29
I would like to connect to my university's wireless network. However, they don't offer support for linux clients, only Win/Mac. Basically, I need to be able to connect to a "WPA/WPA2-Enterprise network with EAP type TTLS/PAP". 

Can anyone point me in the right direction for how to get this set up?

Thanks,

Cory

---

### Post by dwinks on 2009-09-29
The Ohio State University has a [nice page]("http://opensource.cse.ohio-state.edu/wireless") set up with all the information needed to connect to their student wireless.  I'd wager that yours is the same.  Take a look at that page and see if that works for you.

If not, try to provide as much information as you possibly can on the connection.

---

### Post by allspiritseve on 2009-09-29
I put in everything the same, however, it didn't work. It did ask me for a CA certificate, but the only option available was to select a file from my local hard drive. 

Here's the full connection settings:

**Network Authentication:** WPA2 preferred/WPA available
**Data Encryption:** AES preferred/TKIP available
**EAP Type:** TTLS (is not native in windows OS. You need a third party client.)
**Trusted Root CA:** Entrust.Net Secure Server Certification Authority (there are two Root CA's with the same name built into many of the OS's. The correct one is valid from 5/25/1999 to 05/25/2019)
**Server Name Verification:** .umnet.umich.edu (just the domain is added as there is more than one server for failover)
**TTLS Authentication Method:** PAP
**Domain:** NO Domain information, leave blank.

---

### Post by rasungod_7 on 2009-09-29
At my university I left clicked on the network manager applet, then selected connect to a hidden wireless network.

From there I selected the WPA & WPA2 Enterprise security.

Type in the Network name,

At my school the authentication is EAP (PEAP)

Then input the username and password

Hope this works

---

### Post by allspiritseve on 2009-09-29
> **rasungod_7 said:**
> At my university I left clicked on the network manager applet, then selected connect to a hidden wireless network.

From there I selected the WPA & WPA2 Enterprise security.

Type in the Network name,

At my school the authentication is EAP (PEAP)

Then input the username and password

Hope this works

Nope, no go. It tries to connect, but fails without telling me why.

---

### Post by dwinks on 2009-09-30
> **allspiritseve said:**
> I put in everything the same, however, it didn't work. It did ask me for a CA certificate, but the only option available was to select a file from my local hard drive. 

Here's the full connection settings:

**Network Authentication:** WPA2 preferred/WPA available
**Data Encryption:** AES preferred/TKIP available
**EAP Type:** TTLS (is not native in windows OS. You need a third party client.)
**Trusted Root CA:** Entrust.Net Secure Server Certification Authority (there are two Root CA's with the same name built into many of the OS's. The correct one is valid from 5/25/1999 to 05/25/2019)
**Server Name Verification:** .umnet.umich.edu (just the domain is added as there is more than one server for failover)
**TTLS Authentication Method:** PAP
**Domain:** NO Domain information, leave blank.

Ok, what I had to do for mine was go to the website of the cert for OSU and download a copy of it.  You can google "Entrust.Net Secure Server Certification Authority", click on the first link, click on "download certificate", select personal use and download a copy of their cert.  They list a few different ones, so you may have a bit of trial and error.  I'd start with trying the root cert.

From looking at the MWireless page you pulled that info from, it looks to be set up pretty much identical to OSU.  It WILL work, it will just take a bit of fiddling.  Also, Michigan has a [Linux Users Group]("http://www.umich.edu/~umlug/contact.html"), so you could always see if someone there would be able to help.  With any luck, you'll get a hold of someone willing to simply meet you at one of the libraries or something and actually help you get set up, or at least email you a few screen-shots of the settings.

---

