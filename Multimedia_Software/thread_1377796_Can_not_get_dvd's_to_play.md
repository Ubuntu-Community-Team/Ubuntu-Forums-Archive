---
title: "Can not get dvd's to play"
date: 2010-01-10
forum: Multimedia Software
---

### Post by Tourdog on 2010-01-10
Anyone:
I am the 8th responder on "mdquince's" message post (about 4 hours ago) . I have the same exact problem:  Ubudog responded (#6) with the following:  

> sudo apt-get install ubuntu-restricted-extrasIt seems to be a good direction but after do so I have a "locked" Sun Micro Systems Java6-Jre license aggreement menu.  The desktop is ok.   What to do?   If Ubudog is here do you have any suggestions?    If doing a uninstall is best for the above sudo could you print that please?

Anybody?         This is where I ended with Netbook Remix too!  :(
Gurus  I need some direction?  Thanks a million!

---

### Post by HappyFeet on 2010-01-10
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install libdvdcss2
```
enjoy your dvd.

---

### Post by Tourdog on 2010-01-10
HappyFeet,
Thanks for the reply!   I simply ignored the locked up Sun/Java screen and went ahead and applied the 2 sudos you provided but no joy.

> Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 198B in 1s (120B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tourdog@PJK3:~$ sudo apt-get install libdvdcss2
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
My reading the mail on this subject has surfaced the "Public Key" and the need for "libdvdcss" but I just don't know how to comply.   It would seem that Linux would take a quantum leap into being a major player if the resolution of these problems were made more sure.  I see so much prospect in Ubuntu 9.10 if only .....................
TIA !

---

### Post by HappyFeet on 2010-01-10
In the first line of code I gave you, are you sure you copy and pasted the whole thing? It scrolls far to the right. Try it again.

---

### Post by Tourdog on 2010-01-10
HappyFeet,
I'll give it a try!
Thanks for coming back!

---

### Post by Tourdog on 2010-01-10
HappyFeet,
the first sudo begins ~$ sudo ............................................very long ......................................................ends with .... update

the second sudo begins ~$ sudo .................................  ends with libdvdcss2

no go!   I am puzzled?!  What do you think?

I even did a Clear on the terminal and did it once with a fresh Terminal.

---

### Post by Tourdog on 2010-01-10
HappyFeet,
I'm doing a shutdown and restart on Karmic in hopes of clearing any loose electrons...................... maybe this will get both your Sudos to enable the Public Key and Unlock...........   hope hope hope!

---

### Post by Tourdog on 2010-01-10
HappyFeet,
I've done a reboot and used both of your sudo's and with the addition of:
 "sudo dpkg --configure -a"  (recommended)

" apt-get -f install"  I added the sudo to it.   I am now clear of the Public Key and unlock/lock problem and back to getting past the Sun Micro System:

file   edit  view  terminal  help
                                                        Package Configuration
                                               Configuring Sun-Java6 -Bin


It is the typical "license" but paging down it there is no "I agree box" anywhere on it.  It appears like anyother "agreement but no where is there a place to "agree"

What is up with this last hurtle before achieving DVDs at last!
Thanks again for all your help!

---

### Post by howefield on 2010-01-10
You probably see the <OK> button in the licence window ?

Use the TAB key to highlight it and press the Enter key.

Then on the next screen, use the left arrow key to select <Yes> and press the Enter key.

---

### Post by Tourdog on 2010-01-10
HoweField,
You.................................NAILED it  !!!  Thank You, Thank You !!!  :D

---

