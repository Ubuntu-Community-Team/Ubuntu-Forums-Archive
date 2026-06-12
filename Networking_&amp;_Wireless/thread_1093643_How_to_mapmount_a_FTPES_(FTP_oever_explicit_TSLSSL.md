---
title: "How to map/mount a FTPES (FTP oever explicit TSL/SSL) ??"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by TomyMMX on 2009-03-11
For the love of god I can't figure it out. There are solutions for doing this with FTPS(CurlFTPFS) and SFTP.. but haven't found one for FTPES. I can use FileZilla to connect to the sever and download or upload files, but since I need to run scripts and stuff that don't know what FTPES is it wold be way more convenient to have the remote folder mapped as a local folder on the file system. 

There is also the possibility that I am overlooking something.. but if the server address starts with ftpes://.. then I don't know how to map it to a local folder.

If anyone has a solution I would really appreciate it.. thanks.

---

### Post by TomyMMX on 2009-03-23
Is there no solution? I would really appreciate it, if someone finds one.

Thanks !

---

### Post by DigitaLink on 2009-12-11
I've been desperately searching for an answer to the FTPES dilemma myself.  My web host has decided to use FTPES for ftp access now, and NOTHING but FileZilla it seems will connect to the blasted thing.  I've tried Windows editors, linux editors, everything but Dreamweaver ... which I don't have and SUPPOSEDLY works if you dance through the right hoops.  Irritating as heck!!!

---

### Post by DigitaLink on 2009-12-11
Well, Dreamweaver WILL connect from Windows ... doesn't do me a lick of good in Ubuntu though!

Does anyone know if there's a way to mimic the way DW connects?  It involves setting it to use a secure connection and a firewall, then setting the firewall port to 40007 (at least for my host).

I don't want to have to ditch Ubuntu to use DW under Windows over this!!

---

### Post by DigitaLink on 2009-12-11
Well, I found another solution for WINDOWS, but nothing for linux yet.  Bitvise Tunnelier acts as an FTP to SFTP bridge.  It makes the connection to the FTPES server, and you set up your programs that support regular FTP to connect to localhost.  Then it forwards the requests over the secure connection.

Does anyone know of any sort of similar bridge for linux?

---

### Post by Holmss on 2010-09-05
Anything new about this?

---

### Post by lagus on 2010-12-17
> **Holmss said:**
> Anything new about this?

Not as far as I know... ;(
I have gotten this far but yet not news how to proceed!:

Command:
curlftpfs -v -o ssl -o ssl_control -d rxxxx:xxxx@ftp.xxxxx.xx:1xxx /mxxxxx/


Output:
```

* Couldn't find host ftp.xxxxx.xx  in the .netrc file; using defaults
* About to connect() to ftp.xxxxx.xx  port 1XXX (#0)
*   Trying 89.XXX.XXX.XXX... * connected
* Connected to ftp.xxxxx.xx (89.XXX.XXX.XXX) port 1XXX (#0)
< 220 THE XXXXX XXX (glFTPd 2.01 Linux+TLS) ready.
> AUTH SSL
< 234 AUTH SSL successful
* found 142 certificates in /etc/ssl/certs/ca-certificates.crt
* server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
* Closing connection #0
Error connecting to ftp: server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
```

What can I do to get it to work?
It works fine with Filezilla on Windows..
Please help me!

---

### Post by hiddenh on 2010-12-18
Since your command helped me find out of my issue i figured i would offer some help instead.
The end command i had to use since the hostname did not match the key in my case:
```
curlftpfs -o ssl -o ssl_control -o no_verify_hostname -d username:password@xxx.xxx.xxx.xxx:port /home/user/folder/
```


In any case what you are looking to do is get the ftp server certificate key to paste into this file 
> /etc/ssl/certs/ca-certificates.crt

Filezilla usually or can accept certificates automatically. However curlftpfs relies on them to be located in the shared library which is in the location mentioned above.

You should be able to get this key from the administration part of the ftp server since that generated the key. Filezilla should also have a copy since it accessed the site but i do not know where filezilla puts its keys.

The key looks like this:

-----BEGIN CERTIFICATE-----
MIICVjBBAb+gAwIBAgIBADANBgkqhkiG9w0BAQQFADByMRIwEAYDVQQHEwlhc2Vy
c2FkZmUxDDAKBgNVBAgTA3NlcjELMAkGA1UEBhMCYXMxDTALBgNVBAMTBHNlcnMx
EzARBgkqhkiG9w0BCQETBHNhZUXxDTALBgNVBAoTBHJzZXIxDjAMBgNVBAsTBWRm
ZXJyMB4XDTEwMDgwMzIzNTQ1OFoXDTIwMDgwMzIzNTQ1OFowcjESMBAGA1UEBxMJ
YXNlcnNhZGZlMQwwCgYDVQQIEwNzZXIxCzAJBgNVBAYTAmFzMQ0wCwYDVQQDEwRz
ZXJzMRMwEQYJKoZIhvcNAQkBEwRzYWRmMQ0wCwYDVQQKEwRyc2VyMQ4wDAYDVQQL
EwVkZmVycjCBnTANBgkqhkiG9w0BAQEFAAOBiwAwgYcCgYEAxfiAmGfVh/mlX2Za
dX4+XPLqeOqoNoerCi9bmHs9ia5X9SU+k2toMA5FR6+ZlPFi2dwSRjptlK20c29U
4B068t/PEgX4UfONq3geBQppObC3Lq6O5qbXPa7h9LtiQxjA3a64DpRidR/ULt9V
1x94SyDpAEkzFzSrzEWlxzKTrbMCAQMwDQYJKoZIhvcNAQEEBQADgYEAok1TlDoK
M6e5tuRZcacBv9Gt1m+YLuuidSyxJG3uXeCvUUdQ4/uoUAP0IIMlXqJ+r6zkKPyb
bYxUSpVuMhRiKNC8LU7hXO+KxIbpuCst4mAUHGGi84H583oFaPd0U/3BwBT3So/j
lFaDzUTCJhqjLSM1ik7xetwqOr5DmyMumIw=
-----END CERTIFICATE-----

So find it , copy it into the bottom of the .crt file and you should be good.

---

### Post by zerothink on 2011-06-16
...or if you can live with the fact that server certificate will not be vetrified you can use:

```

curlftpfs -o ssl -o ssl_control -o no_verify_hostname -o no_verify_peer -d username:password@xxx.xxx.xxx.xxx:port /home/user/folder/

```

in that case you do not need SSL certificate

---

### Post by burning-daylight on 2012-02-02
Trying to connect, but getting error:```

sudo curlftpfs -o ssl -o ssl_control -o no_verify_hostname -d user:pass@ip.ip.ip.ip /mnt/ip
Error connecting to ftp: gnutls_handshake() failed: A TLS fatal alert has been received.
```

---

### Post by karlito139 on 2012-07-19
Hi,

Juste had the same probleme, after searching on the internet I solved the probleme with this commande :


sudo curlftpfs -o tlsv1 -o ssl_control -o no_verify_hostname -o no_verify_peer -o allow_other user:mdp@host mountpoint

---

