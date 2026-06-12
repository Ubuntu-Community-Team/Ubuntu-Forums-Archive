---
title: "Citrix and SSL Error 61"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by halfhearted on 2012-05-07
I'm using Ubuntu 12.04 LTS (32bit) and the latest Linux version of Citrix Receiver. Whenever I try to connect to my work network through Citrix I get the error message below. As far as I can see it's not true, I *am* trusting the issuer of the server's security certificate. This error message, (with different issuers) is frequently mentioned on the net but I cannot get any of the many many solutions to work in my case. Any advice would be gratefully received.

SSL error : Contact your help desk with the following information: You have not chosen to trust "/C=US/ST=/L=/O=The Go Daddy Group, Inc./OU=Go Daddy Class 2 Certification Authority/CN=", the issuer of the server's security certificate (SSL error 61).

---

### Post by damage84 on 2012-05-08
> **halfhearted said:**
> I'm using Ubuntu 12.04 LTS (32bit) and the latest Linux version of Citrix Receiver. Whenever I try to connect to my work network through Citrix I get the error message below. As far as I can see it's not true, I *am* trusting the issuer of the server's security certificate. This error message, (with different issuers) is frequently mentioned on the net but I cannot get any of the many many solutions to work in my case. Any advice would be gratefully received.

SSL error : Contact your help desk with the following information: You have not chosen to trust "/C=US/ST=/L=/O=The Go Daddy Group, Inc./OU=Go Daddy Class 2 Certification Authority/CN=", the issuer of the server's security certificate (SSL error 61).

This is actually straight from Ubuntu's Citrix help page:

To prevent the following error when accessing remote sessions:

Citrix Receiver
SSL error
Contact your help desk with the following information:
You have not chosen to trust"/C=US/ST=/L=/O=Equifax/OU=Equifax Secure Certificate Authority/CN=", the issuer of the server's security certificate ((SSL error 61).


Make Firefox's certificates accessible to Citrix, e.g.,

```
sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts
```

It worked perfectly for me.

---

### Post by halfhearted on 2012-05-08
Thanks very much damage84. It worked but I don't understand why. What does "ln -s" mean? Thanks for your help.

---

### Post by damage84 on 2012-05-09
> **halfhearted said:**
> Thanks very much damage84. It worked but I don't understand why. What does "ln -s" mean? Thanks for your help.

No problem, it works because the root problem is Citrix doesn't have access to the SSL certificate required to make a secure connection. Since it has no way of guranteeing the connection it rejects / doesn't connect. What that command does is create a link to Mozilla's SSL certificates in Citrix's certificate folder. That's what ln -s does, it creates a link, like a Windows shortcut so that when Citrix looks in it's own certicate folder, it sees Mozilla's certificates so instead of seeing a folder that lacks the right certificate, it sees a folder that has the right certificate so it can verify and make the connection securely.

---

### Post by fbrites on 2012-08-18
Hi damaged84.
I've tried the solution you gave but got an error :
ln: target `/opt/Citrix/ICAClient/keystore/cacerts' is not a directory

What am I doing wrong?
Thanks!

---

### Post by halfhearted on 2012-10-13
Well fbrites (if you are still looking) it could be that Citrix hasn't installed properly and created the folder. See if the other folders in the pathname exist in /opt.

---

### Post by rigobertomanchu on 2012-10-22
ln -s of certificates from mozilla to citrix is not enough some times.

i had to install the Go Daddy root certificate and the Intermediate certificate, copy them in citrix cacerts dir and it finally works

---

### Post by gready on 2012-10-25
> **rigobertomanchu said:**
> ln -s of certificates from mozilla to citrix is not enough some times.

i had to install the Go Daddy root certificate and the Intermediate certificate, copy them in citrix cacerts dir and it finally works

How did you do this?

---

### Post by pdowty on 2012-12-18
This Error 61 has been a recurring problem for me.  On Windows it seems to come and go in association with Firefox updates.

I haven't been able to resolve the issue in Ubuntu.  I tried the ln -s command above but the problem persists.  I checked the contents of 
/opt/Citrix/ICAClient/keystore/cacerts 
and all the links are there that appear in the Mozilla certificate directory.

The specific error I get now includes that I have chosen not to trust "Entrust Certification Authority - L1C", but there are three Entrust certificates in the cacerts directory:
Entrust.net_Premium_2048_Secure_Server_CA.crt
Entrust.net_Secure_Server_CA.crt
Entrust_Root_Certification_Authority.crt

Any help would be appreciated.  Thanks.

---

### Post by pdowty on 2012-12-18
Resolved my Error 61 after finding a post that suggested finding a working Windows Citrix Receiver and exporting the problem certificate from the Windows browser and placing in the Ubuntu directory.  It worked.  Whew!  What a pain.

---

