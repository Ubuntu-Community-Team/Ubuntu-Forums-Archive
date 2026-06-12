---
title: "Citrix gives error SSL Provider Code:20, SSL Error 86"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by ebeyer on 2009-06-08
I'm hoping this problem has an easy answer. 

I have installed Citrix Receiver on a System76 netbook running Ubuntu 9.04 (netbook remix). I'm attempting&#8203; to connect to our remote server via the Opera 10 browser. I should point out that this combinatio&#8203;n of browser and citrix clients works fine on my OS X setup.

I downloaded&#8203; the security certificat&#8203;e from my system administra&#8203;tor (hosp.cer for our purposes) and put it in my /keystore/&#8203;cacerts folder. At the suggestion&#8203; of another forum, I added a copy of that certificat&#8203;e named hosp.crt.

When I try to connect to the remote server, the citrix receiver client pops up and immediatel&#8203;y gives me the error:
The security certificat&#8203;e "hosp.org"&#8203; could not be validated.&#8203; (SSL provider code: 20, SSL error 86).

Any insight you can give me to solve my problem would be much appreciated.

---

### Post by Marc van der Wijst on 2009-08-10
Just solved this problem. Besides the certificate for the site, you need to download the certificate for the CA and AAA. Here's how. In Firefox open the Secure Gateway site and click on the blue lock icon, "More Information...", "View Certificate" and the tab "Details". In my case there were three entries under "Certificate Hierarchy": CA, AAA and the site name. Select CA and click "Export...", select AAA and click "Export..." and finaly select the site name and click "Export...". Copy all three certificates to ~/ICAClient/linuxx86/keystore/cacerts.

---

### Post by iver2435 on 2009-08-11
OMG!!  you have just solved one of my most nagging problems with my laptop!!!  thank you so much for this info!!

---

### Post by themtx on 2009-09-09
Nice!  Was able to get our Comodo secured internal Citrix server certs added to my client store, now all is well.  Tried it w/just the host cert, failed w/the error posted, then added CA and Intermeditate Comodo certs, voila.

thanks again.

---

### Post by AtlasAmericana on 2010-04-21
Thank you, thank you, thank you. As the others have said, this has solved my SSL 61 and 86 errors. I tried 20 other different "solutions"; this is the only one that worked. And simple to boot!

---

### Post by skywalker_7421 on 2011-04-10
Thanks

---

