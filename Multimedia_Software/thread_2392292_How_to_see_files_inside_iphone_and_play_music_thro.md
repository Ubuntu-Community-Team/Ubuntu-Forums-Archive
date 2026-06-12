---
title: "How to see files inside iphone and play music through VLC Mobile [Linux solution]"
date: 2018-05-19
forum: Multimedia Software
---

### Post by shantiq on 2018-05-19
Tested on iPhone 4S; no reason to believe it will be different on  later versions.
Fairly simple route:

**FIRST:**

&#10122; INSTALL:

```
 sudo apt install ideviceinstaller python-imobiledevice libimobiledevice-utils python-plist usbmuxd libimobiledevice6 libplist3 ifuse
```

you may need to do this too:

```
sudo mkdir /var/lib/lockdown
sudo chmod 777 /var/lib/lockdown
```

&#10123; in Terminal to see your iphone address:

```
  lsusb -v 2> /dev/null | grep -e "Apple Inc" -A 2
```

You will see something thus:

 iManufacturer           1 Apple Inc.
  iProduct                2 iPhone
  iSerial                 3 ca00d62380d42746b8ff8280....d1fd7b7119ca

&#10124; Open Nautilus

enter the iSerial from above with afc:// preceding:

```
 afc://ca00d62380d4274....f8280a91ed1fd7b7119ca/
```

NOW you see your files.   [SIZE=1]***Photos are in DCIM folder***[/SIZE]

[ATTACH=CONFIG]279747[/ATTACH]


========================
========================



**&#10125; THEN:**  *INSTALL VLC MOBILE on your iphone from App Store [free]* and plug into computer

There is a VLC folder under "Documents on iphone" SEE pix for clarity

[ATTACH=CONFIG]279748[/ATTACH][ATTACH=CONFIG]279749[/ATTACH]


Push a flac a wv a few mp3s and m4a into folder and remove the iphone from the computer and they all play beautifully great sound too

*NO itunes no windows no Mac all Linux and playing formats that itunes would balk at ...*

---

### Post by shantiq on 2018-07-17
Using this on a 4S ...   would love to know if anyone got this going on newer models?
Thanx for feedback

---

