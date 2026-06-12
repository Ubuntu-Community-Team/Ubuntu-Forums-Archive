---
title: "Import VPN Connection from ovpn File Containing Certificates Using Network Manager"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by acetace on 2010-03-24
Hi All:
 
I am fairly clueless when it comes to open vpn configuration file. Though I should have some understanding to execute the fix if it is available. 
 
I have a ovpn file that is created by my organization (so theoretically there should be nothing wrong with it) containing not only the typical connection information, but also my CA key, certerficate/Public and certificate/Private key. I was able to locate these keys using the standard text editors.
 
When I follow the procedure to import (Right click on Internet Icon --> Edit Connection --> VPN Tab --> Import) none of my keys were imported (perhaps the import is not complete). I think because of the import failure I was not able to click ok and create the connection.
 
Is there a method to get around this and get it working? I have been looking for existing solution online but I was not able to find any similar cases with mine.
 
 
Thank you for your help in advance.

---

### Post by acetace on 2010-03-24
[COLOR=black][FONT=Verdana]Solved it myself.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I was looking for a way to get the certificate out from the *.ovpn file. However for the life of me I could not get it showing in Network Manager after I copy and pasted it out into a text file.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]It turned out that the certificate copying the value of the certificate is not enough, one need to include the lines that goes "---- BEGIN CERTIFICATE----" and the corresponding end, essentially everything that is included under the <ca></ca> and <cert></cert> codes in order for the certificate to show up for the Network Manager to pickup.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Once I did that and putting the certificates where they belong, and validated that all the settings in the ovpn file has been transcribed it started working miraculously thing worked great.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Regardless, I hope to post my solution here in case other novice linux users like me bump into similar problem.[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Verdana]Cheers.[/FONT][/COLOR]

---

