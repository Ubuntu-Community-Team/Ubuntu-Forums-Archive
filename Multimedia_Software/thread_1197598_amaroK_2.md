---
title: "amaroK 2"
date: 2009-06-26
forum: Multimedia Software
---

### Post by GSI on 2009-06-26
Hello everybody. :) From where can I download amaroK 2 package ? I'm having problems installing amarok 2 with commands :(

---

### Post by tolotos on 2009-06-26
Hello 

To get amarok2:

"Applications>Accesories>Terminal" and enter:  "sudo apt-get install amarok2".
Or alternatively System>Adminstration>Synaptic Package Manager and search for amarok2 there.
If this one succeeds, do the same with amarok-kde4 package.

If the standard repository versions fail, I would at first try:
    sudo apt-get update
    sudo apt-get upgrade


If for some reason this fails too, I would be happy if you could post the error message, with which the installation fails.

With all this failing, you could still try to compile it from source. But this really is the last course of aktion.

---

### Post by GSI on 2009-06-27
I tried all the commands you said and I get this error : 

W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) experimental Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B

---

### Post by tolotos on 2009-06-27
GPG ist used to verify that the source from where you download your packages is trust worthy. Your System seems to be missing the gpg-key of the repository your are trying to download from. To import the gpg-key (Ubuntu 8.10) type in Terminal:
       sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com CA967634
After that retry 
       sudo apt-get install amarok2
Hope that helps.

---

### Post by GSI on 2009-06-27
It didn't helped...I'm still getting the same error :(

---

