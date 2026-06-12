---
title: "Adding the Repository"
date: 2010-11-30
forum: Multimedia Software
---

### Post by BCMerlin on 2010-11-30
I am freaking new to Ubuntu and exploring how things work (or how they not).

I'm using Ubuntu 10.10 (i guess 64 bits), not the Maverick version but the new 10.10.
My laptop is Acer Aspire 5715Z.

Now I was on [this website]("https://help.ubuntu.com/community/Medibuntu") and tried to add the repository to get the Medibuntu packages with the following code:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```Now I get this:

```


barbara@barbara-Aspire-5715Z:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for barbara: 
--2010-11-30 14:05:33--  http://www.medibuntu.org/sources.list.d/maverick.list
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 286 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 286         --.-K/s   in 0s      

2010-11-30 14:05:33 (9,32 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [286/286]

Geraakt http://nl.archive.ubuntu.com maverick Release.gpg
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/main Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-nl
Geraakt http://archive.canonical.com maverick Release.gpg
Genegeerd http://archive.canonical.com/ubuntu/ maverick/partner Translation-en
Genegeerd http://archive.canonical.com/ubuntu/ maverick/partner Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/universe Translation-nl
Geraakt http://nl.archive.ubuntu.com maverick-updates Release.gpg
Ophalen:1 http://packages.medibuntu.org maverick Release.gpg [197B]
Geraakt http://archive.ubuntu.com maverick Release.gpg
Ophalen:2 http://extras.ubuntu.com maverick Release.gpg [316B]
Genegeerd http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Genegeerd http://extras.ubuntu.com/ubuntu/ maverick/main Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-nl
Geraakt http://archive.canonical.com maverick Release
Ophalen:3 http://extras.ubuntu.com maverick Release [57,3kB]
Geraakt http://archive.ubuntu.com maverick Release
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-nl
Fout http://extras.ubuntu.com maverick Release
  
Geraakt http://nl.archive.ubuntu.com maverick-security Release.gpg
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Geraakt http://archive.canonical.com maverick/partner i386 Packages
Genegeerd http://packages.medibuntu.org/ maverick/free Translation-en
Geraakt http://archive.ubuntu.com maverick/main Sources
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-nl
Geraakt http://nl.archive.ubuntu.com maverick Release
Geraakt http://nl.archive.ubuntu.com maverick-updates Release
Geraakt http://nl.archive.ubuntu.com maverick-security Release
Geraakt http://archive.ubuntu.com maverick/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick/main Sources
Geraakt http://nl.archive.ubuntu.com maverick/multiverse Sources
Geraakt http://nl.archive.ubuntu.com maverick/universe Sources
Geraakt http://nl.archive.ubuntu.com maverick/main i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick/restricted i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick/universe i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick/multiverse i386 Packages
Genegeerd http://packages.medibuntu.org/ maverick/free Translation-nl
Geraakt http://nl.archive.ubuntu.com maverick-updates/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/main Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/multiverse Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/universe Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/main i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-updates/restricted i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-updates/universe i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/main Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/multiverse Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/universe Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/main i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/restricted i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/universe i386 Packages
Genegeerd http://packages.medibuntu.org/ maverick/non-free Translation-en
Geraakt http://nl.archive.ubuntu.com maverick-security/multiverse i386 Packages
Genegeerd http://packages.medibuntu.org/ maverick/non-free Translation-nl
Ophalen:4 http://packages.medibuntu.org maverick Release [6857B]
Genegeerd http://packages.medibuntu.org maverick Release
Ophalen:5 http://packages.medibuntu.org maverick/free i386 Packages [3260B]
Ophalen:6 http://packages.medibuntu.org maverick/non-free i386 Packages [7100B]
17,7kB opgehaald in 0s (22,4kB/s)
Pakketlijsten worden ingelezen...
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: De volgende ondertekeningen konden niet geverifieerd worden omdat de publieke sleutel niet beschikbaar is: NO_PUBKEY DB141E2302FDF932

W: GPG error: http://packages.medibuntu.org maverick Release: De volgende ondertekeningen konden niet geverifieerd worden omdat de publieke sleutel niet beschikbaar is: NO_PUBKEY 2EBC26B60C5A2783
W: Ophalen van http://extras.ubuntu.com/ubuntu/dists/maverick/Release is mislukt  

W: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.
Pakketlijsten worden ingelezen...
Boom van vereisten wordt opgebouwd...
De status informatie wordt gelezen...
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  medibuntu-keyring
0 pakketten opgewaardeerd, 1 pakketten nieuw geïnstalleerd, 0 te verwijderen en 2 niet opgewaardeerd.
Er moeten 3448B aan archieven opgehaald worden.
Door deze operatie zal er 49,2kB extra schijfruimte gebruikt worden.
WAARSCHUWING: De volgende pakketten kunnen niet geauthentificeerd worden:
  medibuntu-keyring
Authentificatiewaarschuwing is genegeerd.
Ophalen:1 http://packages.medibuntu.org/ maverick/free medibuntu-keyring all 2008.04.20 [3448B]
3448B opgehaald in 0s (8174B/s)
Selecteren van voorheen niet geselecteerd pakket medibuntu-keyring.
(Database inlezen ... 152407 bestanden en mappen geïnstalleerd.)
Uitpakken van medibuntu-keyring (uit .../medibuntu-keyring_2008.04.20_all.deb) ...
Instellen van medibuntu-keyring (2008.04.20) ...
OK
Geraakt http://nl.archive.ubuntu.com maverick Release.gpg
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/main Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/universe Translation-nl
Geraakt http://nl.archive.ubuntu.com maverick-updates Release.gpg
Ophalen:1 http://extras.ubuntu.com maverick Release.gpg [316B]
Genegeerd http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Genegeerd http://extras.ubuntu.com/ubuntu/ maverick/main Translation-nl
Geraakt http://archive.ubuntu.com maverick Release.gpg
Geraakt http://archive.canonical.com maverick Release.gpg
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Genegeerd http://archive.canonical.com/ubuntu/ maverick/partner Translation-en
Genegeerd http://archive.canonical.com/ubuntu/ maverick/partner Translation-nl
Ophalen:2 http://packages.medibuntu.org maverick Release.gpg [197B]
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ophalen:3 http://extras.ubuntu.com maverick Release [57,3kB]
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-nl
Geraakt http://archive.ubuntu.com maverick Release
Geraakt http://nl.archive.ubuntu.com maverick-security Release.gpg
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Geraakt http://archive.canonical.com maverick Release
Fout http://extras.ubuntu.com maverick Release
  
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-nl
Geraakt http://archive.ubuntu.com maverick/main Sources
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-nl
Geraakt http://nl.archive.ubuntu.com maverick Release
Geraakt http://nl.archive.ubuntu.com maverick-updates Release
Genegeerd http://packages.medibuntu.org/ maverick/free Translation-en
Geraakt http://archive.canonical.com maverick/partner i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security Release
Geraakt http://archive.ubuntu.com maverick/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick/main Sources
Geraakt http://nl.archive.ubuntu.com maverick/multiverse Sources
Geraakt http://nl.archive.ubuntu.com maverick/universe Sources
Geraakt http://nl.archive.ubuntu.com maverick/main i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick/restricted i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick/universe i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick/multiverse i386 Packages
Genegeerd http://packages.medibuntu.org/ maverick/free Translation-nl
Geraakt http://nl.archive.ubuntu.com maverick-updates/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/main Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/multiverse Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/universe Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/main i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-updates/restricted i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-updates/universe i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/main Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/multiverse Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/universe Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/main i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/restricted i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/universe i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/multiverse i386 Packages
Genegeerd http://packages.medibuntu.org/ maverick/non-free Translation-en
Genegeerd http://packages.medibuntu.org/ maverick/non-free Translation-nl
Ophalen:4 http://packages.medibuntu.org maverick Release [6857B]
Geraakt http://packages.medibuntu.org maverick/free i386 Packages
Geraakt http://packages.medibuntu.org maverick/non-free i386 Packages
515B opgehaald in 0s (723B/s)
Pakketlijsten worden ingelezen...
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: De volgende ondertekeningen konden niet geverifieerd worden omdat de publieke sleutel niet beschikbaar is: NO_PUBKEY DB141E2302FDF932

W: Ophalen van http://extras.ubuntu.com/ubuntu/dists/maverick/Release is mislukt  

W: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.


```I know some parts are in the Dutch language, but maybe you can see without translation what's going on, cause I guess it failed.

Did I do something wrong?

---

### Post by cottfcfan on 2010-11-30
Nothings gone wrong its just a "signature verification" error, caused by missing GPG Keys.
This has started happening to me to.
Try the tip from here:

[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

---

### Post by BCMerlin on 2010-11-30
Ok thanx.

Can you tell me about the missing GPG keys? I mean, what's the function of those? And why do I want them to be added?

---

### Post by BCMerlin on 2010-11-30
Another thing, I checked[ the link you gave me]("http://www.webupd8.org/2010/05/automatically-import-all-missing.html") and I have some questions about the instructions too.

On one point it's saying:

> For this reason I've created an **Ubuntu .deb package** for the script I was talking about which you can install via the [WebUpd8 PPA]("https://launchpad.net/%7Enilarimogard/+archive/webupd8"). If you have the PPA added to your sources, simply paste this in a terminal:

sudo apt-get install launchpad-getkeys

If you don't want to add the WebUpd8 PPA, simply **download launchpad-getkeys .deb manually.**

I'm so blanco and all the jargon is new to me... :-k

How do I check "the PPA is already been added to my sources"?

---

### Post by cottfcfan on 2010-11-30
OK. Go to the webupd8 page you were on and click
(launchpad-getkeys_0.1~webupd8~maverick_all.deb (1.5 KiB)
Then open up a terminal, (Applications/Accessories/Terminal
and paste:
sudo launchpad-getkeys

That should solve your error problem.

To check the PPA has been added to yours sources, check in system/administration/sofware sources/other software.

---

### Post by runeh76 on 2010-11-30
> **BCMerlin said:**
> I am freaking new to Ubuntu and exploring how things work (or how they not).

I'm using Ubuntu 10.10 (i guess 64 bits), not the Maverick version but the new 10.10.
My laptop is Acer Aspire 5715Z.

Now I was on [this website]("https://help.ubuntu.com/community/Medibuntu") and tried to add the repository to get the Medibuntu packages with the following code:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```Now I get this:

```


barbara@barbara-Aspire-5715Z:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for barbara: 
--2010-11-30 14:05:33--  http://www.medibuntu.org/sources.list.d/maverick.list
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 286 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 286         --.-K/s   in 0s      

2010-11-30 14:05:33 (9,32 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [286/286]

Geraakt http://nl.archive.ubuntu.com maverick Release.gpg
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/main Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-nl
Geraakt http://archive.canonical.com maverick Release.gpg
Genegeerd http://archive.canonical.com/ubuntu/ maverick/partner Translation-en
Genegeerd http://archive.canonical.com/ubuntu/ maverick/partner Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/universe Translation-nl
Geraakt http://nl.archive.ubuntu.com maverick-updates Release.gpg
Ophalen:1 http://packages.medibuntu.org maverick Release.gpg [197B]
Geraakt http://archive.ubuntu.com maverick Release.gpg
Ophalen:2 http://extras.ubuntu.com maverick Release.gpg [316B]
Genegeerd http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Genegeerd http://extras.ubuntu.com/ubuntu/ maverick/main Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-nl
Geraakt http://archive.canonical.com maverick Release
Ophalen:3 http://extras.ubuntu.com maverick Release [57,3kB]
Geraakt http://archive.ubuntu.com maverick Release
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-nl
Fout http://extras.ubuntu.com maverick Release
  
Geraakt http://nl.archive.ubuntu.com maverick-security Release.gpg
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Geraakt http://archive.canonical.com maverick/partner i386 Packages
Genegeerd http://packages.medibuntu.org/ maverick/free Translation-en
Geraakt http://archive.ubuntu.com maverick/main Sources
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-nl
Geraakt http://nl.archive.ubuntu.com maverick Release
Geraakt http://nl.archive.ubuntu.com maverick-updates Release
Geraakt http://nl.archive.ubuntu.com maverick-security Release
Geraakt http://archive.ubuntu.com maverick/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick/main Sources
Geraakt http://nl.archive.ubuntu.com maverick/multiverse Sources
Geraakt http://nl.archive.ubuntu.com maverick/universe Sources
Geraakt http://nl.archive.ubuntu.com maverick/main i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick/restricted i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick/universe i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick/multiverse i386 Packages
Genegeerd http://packages.medibuntu.org/ maverick/free Translation-nl
Geraakt http://nl.archive.ubuntu.com maverick-updates/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/main Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/multiverse Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/universe Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/main i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-updates/restricted i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-updates/universe i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/main Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/multiverse Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/universe Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/main i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/restricted i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/universe i386 Packages
Genegeerd http://packages.medibuntu.org/ maverick/non-free Translation-en
Geraakt http://nl.archive.ubuntu.com maverick-security/multiverse i386 Packages
Genegeerd http://packages.medibuntu.org/ maverick/non-free Translation-nl
Ophalen:4 http://packages.medibuntu.org maverick Release [6857B]
Genegeerd http://packages.medibuntu.org maverick Release
Ophalen:5 http://packages.medibuntu.org maverick/free i386 Packages [3260B]
Ophalen:6 http://packages.medibuntu.org maverick/non-free i386 Packages [7100B]
17,7kB opgehaald in 0s (22,4kB/s)
Pakketlijsten worden ingelezen...
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: De volgende ondertekeningen konden niet geverifieerd worden omdat de publieke sleutel niet beschikbaar is: NO_PUBKEY DB141E2302FDF932

W: GPG error: http://packages.medibuntu.org maverick Release: De volgende ondertekeningen konden niet geverifieerd worden omdat de publieke sleutel niet beschikbaar is: NO_PUBKEY 2EBC26B60C5A2783
W: Ophalen van http://extras.ubuntu.com/ubuntu/dists/maverick/Release is mislukt  

W: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.
Pakketlijsten worden ingelezen...
Boom van vereisten wordt opgebouwd...
De status informatie wordt gelezen...
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  medibuntu-keyring
0 pakketten opgewaardeerd, 1 pakketten nieuw geïnstalleerd, 0 te verwijderen en 2 niet opgewaardeerd.
Er moeten 3448B aan archieven opgehaald worden.
Door deze operatie zal er 49,2kB extra schijfruimte gebruikt worden.
WAARSCHUWING: De volgende pakketten kunnen niet geauthentificeerd worden:
  medibuntu-keyring
Authentificatiewaarschuwing is genegeerd.
Ophalen:1 http://packages.medibuntu.org/ maverick/free medibuntu-keyring all 2008.04.20 [3448B]
3448B opgehaald in 0s (8174B/s)
Selecteren van voorheen niet geselecteerd pakket medibuntu-keyring.
(Database inlezen ... 152407 bestanden en mappen geïnstalleerd.)
Uitpakken van medibuntu-keyring (uit .../medibuntu-keyring_2008.04.20_all.deb) ...
Instellen van medibuntu-keyring (2008.04.20) ...
OK
Geraakt http://nl.archive.ubuntu.com maverick Release.gpg
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/main Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Geraakt http://nl.archive.ubuntu.com/ubuntu/ maverick/universe Translation-nl
Geraakt http://nl.archive.ubuntu.com maverick-updates Release.gpg
Ophalen:1 http://extras.ubuntu.com maverick Release.gpg [316B]
Genegeerd http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Genegeerd http://extras.ubuntu.com/ubuntu/ maverick/main Translation-nl
Geraakt http://archive.ubuntu.com maverick Release.gpg
Geraakt http://archive.canonical.com maverick Release.gpg
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Genegeerd http://archive.canonical.com/ubuntu/ maverick/partner Translation-en
Genegeerd http://archive.canonical.com/ubuntu/ maverick/partner Translation-nl
Ophalen:2 http://packages.medibuntu.org maverick Release.gpg [197B]
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ophalen:3 http://extras.ubuntu.com maverick Release [57,3kB]
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-nl
Geraakt http://archive.ubuntu.com maverick Release
Geraakt http://nl.archive.ubuntu.com maverick-security Release.gpg
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Geraakt http://archive.canonical.com maverick Release
Fout http://extras.ubuntu.com maverick Release
  
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-nl
Geraakt http://archive.ubuntu.com maverick/main Sources
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-nl
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Genegeerd http://nl.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-nl
Geraakt http://nl.archive.ubuntu.com maverick Release
Geraakt http://nl.archive.ubuntu.com maverick-updates Release
Genegeerd http://packages.medibuntu.org/ maverick/free Translation-en
Geraakt http://archive.canonical.com maverick/partner i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security Release
Geraakt http://archive.ubuntu.com maverick/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick/main Sources
Geraakt http://nl.archive.ubuntu.com maverick/multiverse Sources
Geraakt http://nl.archive.ubuntu.com maverick/universe Sources
Geraakt http://nl.archive.ubuntu.com maverick/main i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick/restricted i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick/universe i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick/multiverse i386 Packages
Genegeerd http://packages.medibuntu.org/ maverick/free Translation-nl
Geraakt http://nl.archive.ubuntu.com maverick-updates/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/main Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/multiverse Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/universe Sources
Geraakt http://nl.archive.ubuntu.com maverick-updates/main i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-updates/restricted i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-updates/universe i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/restricted Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/main Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/multiverse Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/universe Sources
Geraakt http://nl.archive.ubuntu.com maverick-security/main i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/restricted i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/universe i386 Packages
Geraakt http://nl.archive.ubuntu.com maverick-security/multiverse i386 Packages
Genegeerd http://packages.medibuntu.org/ maverick/non-free Translation-en
Genegeerd http://packages.medibuntu.org/ maverick/non-free Translation-nl
Ophalen:4 http://packages.medibuntu.org maverick Release [6857B]
Geraakt http://packages.medibuntu.org maverick/free i386 Packages
Geraakt http://packages.medibuntu.org maverick/non-free i386 Packages
515B opgehaald in 0s (723B/s)
Pakketlijsten worden ingelezen...
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: De volgende ondertekeningen konden niet geverifieerd worden omdat de publieke sleutel niet beschikbaar is: NO_PUBKEY DB141E2302FDF932

W: Ophalen van http://extras.ubuntu.com/ubuntu/dists/maverick/Release is mislukt  

W: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.


```I know some parts are in the Dutch language, but maybe you can see without translation what's going on, cause I guess it failed.

Did I do something wrong?


Sry i have to ask what u mean  (I'm using Ubuntu 10.10 (i guess 64 bits), not the Maverick version but the new 10.10)?
I have 10.10 and its Maverick...:?:

---

### Post by BCMerlin on 2010-11-30
> **runeh76 said:**
> Sry i have to ask what u mean  (I'm using Ubuntu 10.10 (i guess 64 bits), not the Maverick version but the new 10.10)?
I have 10.10 and its Maverick...:?:
Hmmm well... I downloaded [the new 10.10]("http://www.ubuntu.com"). Maverick is the old beta version, isn't that right? That's what I understood about it. But tell me what you know.

---

### Post by BCMerlin on 2010-11-30
> **cottfcfan said:**
> OK. Go to the webupd8 page you were on and click
(launchpad-getkeys_0.1~webupd8~maverick_all.deb (1.5 KiB)
Then open up a terminal, (Applications/Accessories/Terminal
and paste:
sudo launchpad-getkeys

That should solve your error problem.

To check the PPA has been added to yours sources, check in system/administration/sofware sources/other software.
First I saved the .deb file, than opened package manager, installed it. Then I copied the code in terminal, where I got this:

```
barbara@barbara-Aspire-5715Z:~$ sudo launchpad-getkeys
Release: maverick
Please Wait...
cat: keyss: No such file or directory
rm: cannot remove `keyss': No such file or directory
```

---

### Post by cottfcfan on 2010-11-30
Ok tried it myself and it works fine.
Could be that your repo is down.
Go to system/administration/software sources, and where it says "download from" change the repo.
Click "other" then "choose best server".
It will run through some tests and give you the best server.
When done try again it should be fine.

---

### Post by runeh76 on 2010-11-30
> **BCMerlin said:**
> Hmmm well... I downloaded [the new 10.10]("http://www.ubuntu.com"). Maverick is the old beta version, isn't that right? That's what I understood about it. But tell me what you know.


Okey okey ;) 
What it says when u click from up-- System/About Ubuntu? Is there some name ur ubuntu?
Just curious nothing else  :)

---

### Post by BCMerlin on 2010-11-30
> **runeh76 said:**
> Okey okey ;) 
What it says when u click from up-- System/About Ubuntu? Is there some name ur ubuntu?
Just curious nothing else  :)
Lol. You're right. ;)

---

### Post by BCMerlin on 2010-11-30
> **cottfcfan said:**
> Ok tried it myself and it works fine.
Could be that your repo is down.
Go to system/administration/software sources, and where it says "download from" change the repo.
Click "other" then "choose best server".
It will run through some tests and give you the best server.
When done try again it should be fine.
Where do I find software sources, cause when I'm going to where you are telling me, there is no software sources in my administration options. Is there another way to come there? Or another name or something?

---

### Post by runeh76 on 2010-11-30
> **BCMerlin said:**
> Lol. You're right. ;)

just becouse anyone getting wrong information ;)

---

### Post by runeh76 on 2010-11-30
> **BCMerlin said:**
> Where do I find software sources, cause when I'm going to where you are telling me, there is no software sources in my administration options. Is there another way to come there? Or another name or something?


U find software sources--->  updates control /settings

---

### Post by cottfcfan on 2010-11-30
BCmerlin,,
Try system/administration/synaptic package manager/settings/repositories, and go from there.

---

### Post by BCMerlin on 2010-11-30
> **cottfcfan said:**
> BCmerlin,,
Try system/administration/synaptic package manager/settings/repositories, and go from there.
Okay, that's what I did. I changed my settings in this way, see image: "repositories.png"
After reloading package manager I got this error, see image: "error.png"
(how do I load pictures in this message btw)

---

### Post by cottfcfan on 2010-11-30
Click the paperclip at the top of the mesage box and insert the file.
you haven`t installed a firewall by any chance that's blocking the repos from downloading?

---

### Post by BCMerlin on 2010-11-30
> **cottfcfan said:**
> you haven`t installed a firewall by any chance that's blocking the repos from downloading?
I wouldn't know. Nothing in purpose. How can I check?

---

### Post by cottfcfan on 2010-11-30
Can see the problem its the independant repos i think.
Its nothing to worry about, I have the same thing, it is a GPGKey.
Just ignore it.

If you untick the independant repos the error will probably go away.
Medibuntu is installed fine though.

---

### Post by runeh76 on 2010-11-30
Follow this:
[http://www.liberiangeek.net/2010/11/add-medibuntu-repository-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/11/add-medibuntu-repository-ubuntu-10-0410-10-maverick-meerkat/)

---

### Post by BCMerlin on 2010-11-30
> **runeh76 said:**
> Follow this:
[http://www.liberiangeek.net/2010/11/add-medibuntu-repository-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/11/add-medibuntu-repository-ubuntu-10-0410-10-maverick-meerkat/)
Now it's done. Thanx for this link.

---

### Post by runeh76 on 2010-11-30
Ur welcome ;)
Put thread as solved.

---

