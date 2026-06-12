---
title: "packages.medibuntu.org  down again ?"
date: 2010-04-21
forum: Multimedia Software
---

### Post by scjet on 2010-04-21
Hi,

 I get the below errors when trying to connect to the below repos.
It has almost always worked in the past.
 Is the site "packages.medibuntu.org" down again !?
...
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_CA
  Unable to connect to packages.medibuntu.org http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_CA
  Unable to connect to packages.medibuntu.org http:
Reading package lists... Done  


-thx ahead.

---

### Post by drs305 on 2010-04-21
Here's the answer and a workaround:
[http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html]("http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html")

---

### Post by Morbius1 on 2010-04-21
I read in another forum somewhere that the problem is not that medibuntu.org is down - it's a DNS problem. "packages.medibuntu.org" can't be converted to an ip address. This might explain why it's been going on for so many days now. Medibuntu can't fix it because it's not their problem.

Anyway, to fix it add the following line to your **/etc/hosts** file:

```
88.191.101.8 packages.medibuntu.org
```That's the ip address of the repository so it doesn't have to use DNS to convert it.

---

### Post by nicknefarious on 2010-04-22
Cheers Morbius...

For others - I tried one of the alternate sources at [http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html]("http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html") and still could not get update to complete without errors. After adding Morbius' suggestion to the **/etc/hosts** file everything is working fine again.

Nick

---

### Post by AnneElizabeth on 2010-05-05
How do you add this code to the **/etc/hosts** file?  I'm not sure what/where this file is?

---

### Post by Morbius1 on 2010-05-06
The problem with the medibuntu repository has been fixed so this should no longer be  a problem.

---

### Post by AnneElizabeth on 2010-05-06
I thought the problem was not with medibuntu, but with DNS.  Either way, I am still getting Connection Timed Out messages when I enter the medbunty repository command into the terminal, and still cannot play DVDs.  Anyone have any suggestions?  Thank you

---

### Post by howefield on 2010-05-06
> **AnneElizabeth said:**
> Anyone have any suggestions?

Download the relevant package from [http://packages.medibuntu.org/](http://packages.medibuntu.org/) and install the downloaded .deb file.

---

### Post by AnneElizabeth on 2010-05-06
Still no luck.  I downloaded the medibuntu keyring package and installed and still nothing.  Anymore ideas as to what is going on with my computer?  Should I remove libdvdread4 and medibuntu repository and reinstall them?

---

