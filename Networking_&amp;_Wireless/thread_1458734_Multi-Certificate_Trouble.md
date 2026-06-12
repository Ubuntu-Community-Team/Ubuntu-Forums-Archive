---
title: "Multi-Certificate Trouble"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by Psycho Game on 2010-04-20
Hello everybody,
I have a problem with our campus network.
They've recently changed their GTE Global Root Certificate with two new certificates.
Those new certificates are: AddTrust External CA Root & UTN-USERFirst-Hardware.
Now is the problem that with the connection settings TTLS you can only give one certificate.
I read somewhere that there is a possibility to create a new file with multiple certificates, but now is the big question: How do I do such a thing?
I sought with google.com, where I could find some info on how to do it in Windows, but not how this is done in Ubuntu.
I hope somebody can give me an answer.

Greetz, Psycho Game

---

### Post by Psycho Game on 2010-04-20
I already found something, but I don't know if this is the appropriate approach.
I copied the the certificate files from /usr/share/ca-certificates/mozilla to my desktop, and used the command: cat file_one.crt file_two.crt > combined.crt.
Can somebody tell me if this was the correct way to do this?

---

### Post by terazen on 2010-04-20
What is the certificate used for?  Is it apache, freeradius, ftp...?

---

### Post by Psycho Game on 2010-04-20
The certificate is used for connecting with the network of our school.
In windows you would have to set these certificates up in securew2, where you  can select multiple certificates.
In ubuntu when making a connection with network manager, when using WPA2/TTLS, you can only give in one certificate file.
The problem is that our network makes use of two seperate certificate files.

---

