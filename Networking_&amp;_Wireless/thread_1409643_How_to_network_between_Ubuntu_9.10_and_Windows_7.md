---
title: "How to network between Ubuntu 9.10 and Windows 7?"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by riahc3 on 2010-02-17
Hey

I have a Windows 7 machine setup and I installed Ubuntu 9.10 on another machine and I want to now network them up to share files, share printers, etc. How can I do this? I havent seen a uptodate tutorial.

---

### Post by adam814 on 2010-02-17
You want to use Samba.  Ubuntu should have "client" applications for it by default, if you need to share files that are on the Ubuntu machine to your Windows machine you'll need to install and configure a Samba server on Ubuntu.

It hasn't changed drastically in the last few years, so most of the older tutorials should still be valid.  I believe you should be able to right-click things in the desktop and go to the share tab under properties more-or-less like in Windows if you just need to share a few files.  You configure printing (and a lot of other things) in /etc/samba/smb.conf

---

### Post by riahc3 on 2010-02-18
> **adam814 said:**
> You want to use Samba.  Ubuntu should have "client" applications for it by default, if you need to share files that are on the Ubuntu machine to your Windows machine you'll need to install and configure a Samba server on Ubuntu.

It hasn't changed drastically in the last few years, so most of the older tutorials should still be valid.  I believe you should be able to right-click things in the desktop and go to the share tab under properties more-or-less like in Windows if you just need to share a few files.  You configure printing (and a lot of other things) in /etc/samba/smb.conf
First off, thanks.

Second off, some tutorials say that Samba (which AFAIK is a protocol) isnt included in Windows anymore. Is this true?

---

### Post by adam814 on 2010-02-18
AFAIK it still is.  I haven't tried it with Windows 7, but I can access samba shares on my Ubuntu laptop from another Vista laptop without any trouble.  Sometimes it's a little tricky the other way around, but it does work once you get the permissions set right on the shares.

---

### Post by doas777 on 2010-02-18
SaMbA is the open source implementation of the MS "Server Message Block"\"Common Internetwork Filesystem". as such MS uses SMB, and we use Samba to talk to it. 

SMB is definetly still in win7 and will be in every forseeable version in the future, thought the internal components and protocols may change. for instance in the old days, NTLMv1 authentication was fine, but now they use NTLMv2 if possible. 

Samba doesn't really require an updated tutorial as not too much has changed that most would notice. I do recall hearing that windows 7 requires some new constraints that had previously been optional. 

one recomendation is that in windows you do this:
```

run -> secpol.msc
     Local Policies - Security Options 
          Network security: LAN Manager authentication level = Send LM & NTLM responses 

         Minimum session security for NTLM SSP = Disable Require 128-bit encryption 
```

personally I would not modify the authentication level on windows, but instead add this to the smb.conf on the clients.
```
client NTLMv2 auth = yes
```

---

