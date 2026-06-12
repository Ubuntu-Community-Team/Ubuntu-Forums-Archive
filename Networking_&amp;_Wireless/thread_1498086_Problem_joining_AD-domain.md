---
title: "Problem joining AD-domain"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by eaglecoth on 2010-05-31
Hi,  I have a problem.

I can't join my domain.  I know I was able to join previously, but after reboot it is now impossible to login using the domain account and it is also impossible to rejoin the domain. I used the following command line to join:

sudo domainjoin-cli --loglevel verbose --log /tmp/domainjoin.log join DOMAIN.COM admin


Here is a print out of the last rows in my join-log:


20100531180317:INFO:File /tmp/likewisetmpSrVrR5/etc/krb5.conf modified
20100531180317:INFO:Finishing krb5.conf configuration
20100531180402:ERROR:Lsass Error [CENTERROR_DOMAINJOIN_LSASS_ERROR]

59 (0x3B) ERROR_UNEXP_NET_ERR - Unknown error

Stack Trace:
main.c:938
main.c:479
djmodule.c:323
djauthinfo.c:843
djauthinfo.c:1187


Any suggestions as to what might be wrong?


/Eaglecoth

---

