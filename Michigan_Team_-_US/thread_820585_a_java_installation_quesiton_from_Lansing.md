---
title: "a java installation quesiton from Lansing"
date: 2008-06-06
forum: Michigan Team - US
---

### Post by GreenLinux@R on 2008-06-06
I am a student and just started using ubuntu last night and I love it. I need to install java 6 onto it. but I have got some problems. 
see below and hope I can please get some inputs from you.

###########
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java5-bin: Depends: sun-java5-jre (= 1.5.0-15-0ubuntu1) but it is not going to be installed
  sun-java6-jdk: Depends: sun-java6-bin (= 6-06-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

but when I run the suggested, 
`apt-get -f install"

no luck 

####
:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
:confused:

---

### Post by wolfger on 2008-06-06
You need to use sudo:
```
sudo apt-get -f install
```

Hopefully that fixes things for you?

---

### Post by GreenLinux@R on 2008-06-07
I got it. 

after running it, I selected I so, the problem fixed. Thanks.

---

