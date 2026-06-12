---
title: "How do I get dvd's to play on mythbuntu"
date: 2012-10-27
forum: Mythbuntu
---

### Post by Mick8882003 on 2012-10-27
I have tried just about everything, googled the pants off this one. Tried installing all the restricted drivers, everything.

It would be great if i could.

Mick

---

### Post by JRV on 2012-10-27
This script will install everything you need to play DVDs.
Copy this script into your home directory.
Name it "installDVD.sh".
Make it executable.```

chmod +x installDVD.sh

```
Read the comments to learn how to use the command.

```

#!/bin/bash
#
# Script to install libdvdcss2 and w32/64/codecs to  
# allow for the playback of DVDs.
#

# Syntax: sudo ./installDVD.sh VERSION 32/64
#
# VERSION is the version name, all lower case (lucid, natty, etc.)
# 32/64 is 32 for a 32 bit system or 64 for a 64 bit system.
# If 32/64 is blank it defaults to 32 bit.

# This script must be run only once.

echo "deb http://archive.ubuntu.com/ubuntu "$1" universe multiverse" >>/etc/apt/sources.list
echo "deb-src http://archive.ubuntu.com/ubuntu "$1" universe multiverse" >>/etc/apt/sources.list

apt-get update

wget http://www.medibuntu.org/sources.list.d/$1.list --output-document=/etc/apt/sources.list.d/medibuntu.list

apt-get update
apt-get install medibuntu-keyring

apt-get update

if [ "$2" = "64" ]; then
    sudo apt-get install w64codecs libdvdcss2
else
    sudo apt-get install w32codecs libdvdcss2
fi


```

---

### Post by Mick8882003 on 2012-10-27
It will play them fine through the dvd player, sorry.

---

### Post by nickrout on 2012-10-27
> **Mick8882003 said:**
> It will play them fine through the dvd player, sorry.so what are you asking?

---

### Post by Mick8882003 on 2012-10-27
Sorry again, when I try to copy a dvd on to the hard drive and then play it, no go.

Thanks Mick

---

### Post by nickrout on 2012-10-27
> **Mick8882003 said:**
> Sorry again, when I try to copy a dvd on to the hard drive and then play it, no go.

Thanks Mick
so how are you copying it?

is it being decrypted in the process?

---

