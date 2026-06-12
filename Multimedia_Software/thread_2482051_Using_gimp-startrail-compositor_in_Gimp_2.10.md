---
title: "Using gimp-startrail-compositor in Gimp 2.10"
date: 2022-12-17
forum: Multimedia Software
---

### Post by Joe_Linux on 2022-12-17
Has anyone been able to install and use the gimp plugin gimp-startrail-compositor in gimp 2.10 ?

If you have I need assistance in doing so. A how to if you will.

---

### Post by Joe_Linux on 2022-12-18
Bump

---

### Post by Joe_Linux on 2022-12-18
I am following the instructions from this link [https://www.facebook.com/astronomylinux/posts/who-needs-startrail-plugin-for-gimpopen-the-terminal-and-runsudo-apt-install-gim/2272501992854642/]("https://www.facebook.com/astronomylinux/posts/who-needs-startrail-plugin-for-gimpopen-the-terminal-and-runsudo-apt-install-gim/2272501992854642/") 
Here are the instructions 
Open the terminal and run:
sudo apt install gimp-python
wget [https://raw.githubusercontent.com/.../master/startrail.py](https://raw.githubusercontent.com/.../master/startrail.py) | tee startrail.py
mv startrail.py.1 startrail.py
sudo cp startrail.py /usr/lib/gimp/2.0/plug-ins/
sudo chmod +x /usr/lib/gimp/2.0/plug-ins/startrail.py
rm startrail.py 
I get this to start with ```
 joe@joe-X555LAB:~$ sudo apt install gimp-python
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gimp-python
joe@joe-X555LAB:~$
```
Yes I posted before

---

### Post by Joe_Linux on 2022-12-18
Is there a way to have an older version of Gimp just to use this plugin ? So I could use 2.10 for some purposes and the older version for the startrail-compositor ?

---

### Post by mIk3_08 on 2022-12-20
> **Joe_Linux said:**
> Is there a way to have an older version of Gimp just to use this plugin ? So I could use 2.10 for some purposes and the older version for the startrail-compositor ?
I don't really use this kind of plugin but here is the ink maybe it can help. Regards and cheers.
[Click here]("https://github.com/themaninthesuitcase/gimp-startrail-compositor#default-plugin-folders")

---

### Post by Joe_Linux on 2022-12-20
Thank you

---

