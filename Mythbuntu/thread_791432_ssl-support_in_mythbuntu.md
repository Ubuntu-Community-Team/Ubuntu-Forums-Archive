---
title: "ssl-support in mythbuntu?"
date: 2008-05-12
forum: Mythbuntu
---

### Post by malaTG on 2008-05-12
Hi

I am thinking of using my mythweb interface externally but I want as "full" security as possible. I have installed mythbuntu 8.04 on my computer and have activated the password part. 

What other security issues should I think about? 

I would like a ssl connection to protect my password, is there a good guide for implmenting this into mythbuntu?

I would prefer not using ssh if possible since it´s a bit more complex and could be a problem reaching my mythweb from different computer.

/Marcus

---

### Post by malaTG on 2008-05-15
I am bumping this issue one time......

---

### Post by caminham on 2008-05-26
I'm very keen to do the same.  I had a play with Apache using a guide online last night and broke mythweb :(  Had to reconfigure it all again.

Does anyone have a howto or at least some pointers on setting up SSL for MythWeb??

---

### Post by malaTG on 2008-06-05
bump...

---

### Post by caminham on 2008-06-05
Whoops... I meant to put a post here a while back.  I managed to work mine out.

Here's what I did:
1. I used this guide [https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL) to setup a cert.

2. Make sure apache is configured to listen on port 443.  To this you need to edit ports.conf (mines in /etc/apache/ but that could vary).  This is how mine is setup:
```
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>
```

3. I then updated the site to use SSL.  To do this i edited the file sites-available/default.  First I set the site to use port 443 by changing the lines
```
NameVirtualHost *
<VirtualHost *>
```
to
```
NameVirtualHost *:443
<VirtualHost *:443>
```

4. Then I added these lines to configure SSL, update the paths to your certs:
```

        SSLEngine On
        SSLCertificateFile /home/username/myCA/cacert.pem
        SSLCertificateKeyFile /home/username/myCA/private/cakey.pem
```

5. Restart Apache with ```
sudo /etc/init.d/apache2 restart 
```

Ta da, mythweb over HTTPS :-)

I hope this information helps.

Cameron

---

