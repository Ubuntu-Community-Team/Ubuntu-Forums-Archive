---
title: "Playing a dvd unable to get plug inns"
date: 2009-08-15
forum: Multimedia Software
---

### Post by ran1wil on 2009-08-15
DVD source Plugin reqired bu t nun found please help

---

### Post by SoftwareExplorer on 2009-08-16
If you are trying to play a commercial DVD, you'll probably need to install one of these.
If you installed amd64 (64 bit) Ubuntu -> [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb)
If you installed i386 (normal, 32 bit ) Ubuntu -> [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)

Hope that helps.

---

### Post by ran1wil on 2009-08-16
that is all good but I find that i have a problem trying to find any plug-ins how can I correct this.

---

### Post by SoftwareExplorer on 2009-08-16
Well, you could install vlc. It will play just about anything. Applications->Add/Remove. Search for vlc. Check the box next to VLC media player. Click Apply changes. When its done, you can find it at Application->Sound & Video->VLC media player. 

If that doesn't work you could try Applications->Accesories->Terminal and paste this in:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```
when it finishes, try playing a DVD and see if it can find what it needs.

PS:The exact error message pasted here would be great.

---

