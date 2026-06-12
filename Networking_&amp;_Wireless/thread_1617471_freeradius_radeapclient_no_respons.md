---
title: "freeradius radeapclient no respons"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by StephanT on 2010-11-09
Hello,
I wanna use freeradius. After installing I build a user called bob and changed the clients.conf for my pc. After testing the following command I got Accept Message:

radtest bob hello localhost 0 testing123

than i wanna test the EAP-MD5 functionality with radeapclient, but that tool did not find the radius. I used the following command: 

( echo "User-Name = \"bob\"";   echo "Cleartext-Password = \"testing123\"";  
echo "EAP-Code = Response";   echo "EAP-Id = 210";   echo "EAP-Type-Identity
= \"bob\"";   echo "Message-Authenticator = 0x10"; ) | radeapclient -x
localhost auth testing123

While doing that freeradius -X did not output anything and Wireshark did not capture any packet on loopback interface.

My System is ubuntu 10.04 with freeradius 2.1.8. Do you have any idea?

---

### Post by Freaky#Funga on 2012-03-31
Same problem here...

---

### Post by Matteus_Blanc on 2012-06-23
> **Freaky#Funga said:**
> Same problem here...

And here...

+++> About to send encoded packet:
        User-Name = "user"
        Cleartext-Password = "mypwd"
        EAP-Code = Response
        EAP-Id = 211
        Message-Authenticator = 0x00000000000000000000000000000000
        EAP-Type-MD5 = 0x1008500d009e5090069eb7d13a0d4b7ff4
        State = 0x516a3f2651b93bf8bc7a0fdc9cf84cfc
radclient: no response from server



I should add that I have already got kerberos auth working with radtest but I am working towards the cert install following this guide: [http://www.freesoftwaremagazine.com/articles/howto_incremental_setup_freeradius_server_eap_authentications](http://www.freesoftwaremagazine.com/articles/howto_incremental_setup_freeradius_server_eap_authentications)

I found this which suggests there is an issue with the debian package: [http://freeradius.1045715.n5.nabble.com/Freeradius-with-EAP-SIM-td4997729.html](http://freeradius.1045715.n5.nabble.com/Freeradius-with-EAP-SIM-td4997729.html)

I'm stuck...

Sorry, I take it back. Comment out this line in /etc/freeradius/eap.conf

default_eap_type = md5

i.e. 

#                default_eap_type = md5


It made everything work for me. I have an ubuntu 10.04 client with these settings

Security: WPA & WPA2 Enterprise
Authentication: Tunnelled TLS
Anonymous Identity: <blank>
CA Certificate: (None)
Inner authentication: PAP
Username: <uname>
Password: <pwd>

uname and pwd are those for my krb5 realm

It all works and I am happy. If anyone can explain why it fails with the default_eap_type = md5 or peap then I would be very interested.

---

