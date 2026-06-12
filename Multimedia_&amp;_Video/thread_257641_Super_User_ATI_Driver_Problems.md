---
title: "Super User ATI Driver Problems"
date: 2006-09-14
forum: Multimedia &amp; Video
---

### Post by mitchmaster on 2006-09-14
I am logged in as what i believe is the only user on my ubuntu 6.06 LTS computer.
I am using an ATI X300SE video card.
And i am trying to use the ATI drivers that are available at the ATI website. Which is the "ATI Driver Installer" available at [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)
Anyways...
the problem i am having is that i am opening it in terminal (so i can watch what it is doing)
and it works fine, and then goes "You need to be super user to run this!" or something along those lines...

Anyways... I am confused because i am 99.9% sure that i am the super user, maybe i am just going at this problem the wrong way?
Please can someone help me out.

Mitch
Thanks in advance!

---

### Post by mitch.c on 2006-09-14
> **mitchmaster said:**
> Anyways...
the problem i am having is that i am opening it in terminal (so i can watch what it is doing)
and it works fine, and then goes "You need to be super user to run this!" or something along those lines...

Anyways... I am confused because i am 99.9% sure that i am the super user, maybe i am just going at this problem the wrong way?
Please can someone help me out.

Mitch
Thanks in advance!

First, if you are running as root, your shell prompt probably ends with a '#'.

Second, you could do:
```
echo $UID
```
If it comes back with anything other than 0, you are not root.

Third, you probably shouldn't run as root, instead you should:
```
sudo ati-installer-command
```

Try that and see if it lets you go.

---

### Post by mitchmaster on 2006-09-14
hmmm... maybe im super noobish... but what code do i enter into the terminal?   sudo and then what? its in the diretory '/home/mitch/desktop/...

maybe a more detailed explanation would help...

thanks
mitch

---

### Post by agustin.g on 2006-09-15
in that case i believe it would be
```
sudo /home/mitch/Desktop/ati-installer-command
```

or

check this page, it will probably help you:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

