---
title: "Installing MakeMKV"
date: 2017-11-06
forum: Multimedia Software
---

### Post by AlyssaVS on 2017-11-06
I am installing MakeMKV in Ubuntu 16.04 from [http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224) and am stuck at the point that I need to "unpack" and enter the "./configure" code for makemkv-oss package. I have extracted both files no problem. All other steps appear to have been done successfully. I assume I am misunderstanding what I have to do to "unpack" the downloaded source packages. I get the error message "no such file or directory" because I'm only entering what I see in the directions. 

Do I need to enter something before or after "./'configure" and the other two code entries?

Any help would be appreciated. :)

---

### Post by monkeybrain20122 on 2017-11-07
You have to change directory (cd) into the folders.

so lets say  you extracted both files in Downloads, the folders are called makemkv-oss-1.10.7 and makemkv-bin-1.10.7, then the full commands are

```
cd Downloads/makemkv-oss-1.10.7
./configure
make 
make install

cd Downloads/makemkv-bin-1.10.7
./configure
make 
make install
```

change Downloads/makemkv-oss-1.10.7 to the path to makemkv-oss-1.10.7 if you extracted it elsewhere, if you extracted it to /home/yourusername then you can just type makemkv-oss-1.10.7 because the path is relative to your home (i.e, subdirectories of /home/yourusrname. so Downloads is really /home/yourusername/Downloads) **Edited:** more accurately the path is relative to your current directory, but if you just start a clean terminal your current directly would be your home, otherwise to specify path relative to your home you need to put ~/ in front, e.g ~/Downloads)

---

### Post by SeijiSensei on 2017-11-07
You might want to consider the mkvtoolnix package that is in the Ubuntu repositories.  The mkvmerge program might be all you need.

---

### Post by Yellow Pasque on 2017-11-07
Handbrake offers similar DVD ripping functionality.

---

