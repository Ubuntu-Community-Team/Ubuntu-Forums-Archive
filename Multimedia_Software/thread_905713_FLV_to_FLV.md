---
title: "FLV to FLV?"
date: 2008-08-30
forum: Multimedia Software
---

### Post by slickuser on 2008-08-30
Hi,

I can't find AvideMux through Add/Remove program.

I download .gz but can't run installation either.

Trying to convert FLV to FLV format.

---

### Post by tamoneya on 2008-08-30
the package is in the repos.  Open terminal and run:```
sudo apt-get update
sudo apt-get install avidemux
```

If that doesnt work please post the output of:```
cat /etc/apt/sources.lst
```

That is a lowercase "L" in "lst" not a number "1".

---

### Post by slickuser on 2008-08-30
That is so much simple and it works. Thanks.. 

Compare to [http://www.avidemux.org/admWiki/index.php?title=Compiling_Avidemux#Mandatory_packages](http://www.avidemux.org/admWiki/index.php?title=Compiling_Avidemux#Mandatory_packages)

So many steps and will not work.

---

### Post by SuperSonic4 on 2008-08-30
You may need to add the medibuntu sources, type the following in a terminal: ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

source:[http://ubuntuforums.org/showpost.php?p=4790346&postcount=1](http://ubuntuforums.org/showpost.php?p=4790346&postcount=1)

---

