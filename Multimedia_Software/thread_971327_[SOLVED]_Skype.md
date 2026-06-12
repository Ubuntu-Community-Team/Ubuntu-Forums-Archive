---
title: "[SOLVED] Skype?"
date: 2008-11-04
forum: Multimedia Software
---

### Post by Yezinki on 2008-11-04
Hi there every one,

Could you please guide in to download which version of Skype?

How do I install it?

Thanks,

Regards,

Yezinki.

---

### Post by crazyness003 on 2008-11-04
There's only one version of skype for Linux. Its 2.0.0.72 and its recomended to get it from the repos.

---

### Post by Yezinki on 2008-11-04
Thanks for your reply.

By repos you mean synaptic?

Sorry am new to Linux,

Regards,

Yezinki.

---

### Post by crazyness003 on 2008-11-04
> **Yezinki said:**
> Thanks for your reply.

By repos you mean synaptic?

Sorry am new to Linux,

Regards,

Yezinki.

Yes, Synaptic is the application that lets you download from the repositories. Or you can quicly install skype by issuing this command in the terminal (Applications -> Accessories -> Terminal)
```
sudo apt-get install skype
```
Insert your password and then accept the rest of the necessary dependencies by typing Y
Then have fun. Be warned tho, the version for Linux is very outdated compared to the windows one. For win , you have 4.x. Linux is at 2.0

---

### Post by Yezinki on 2008-11-04
[B]ubuntu@ubuntu-laptop:~$ sudo apt-get install skype
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ [/B]


Out put is this?

What am I doing wrong?

Regards,

Yezinki.

---

### Post by lisati on 2008-11-04
I got the copy on my machine from the [skype website]("http://www,wkype.com"), clicking on the "download" tab at the top of the screen (the download button tends to choose the Windows version) and choosing the version for Ubuntu.....

It's a "deb" file, so once the download is complete, you can open the file, and clicking on the "install package" button.

Edit: the direct link to the download page for Linux is [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

---

### Post by crazyness003 on 2008-11-04
> **Yezinki said:**
> [B]ubuntu@ubuntu-laptop:~$ sudo apt-get install skype
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ [/B]


Out put is this?

What am I doing wrong?

Regards,

Yezinki.

I forgot you need the medibuntu sources enabled. 
See this site for enabling in your distro
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then try the **sudo apt-get install skype** command again 

It should work after that.

---

### Post by crazyness003 on 2008-11-04
You might wanna take a look at this article (or blog, whatever). 
[http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html](http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html)
Its a great place to start when you first install Ubuntu. Its designed for Hardy Heron 8.04. So if you use Intrepid Ibex, just replace where it says hardy with interpid and 8.04 with 8.10.

---

### Post by redenex on 2008-11-04
[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)


Skype site do have the .deb file, so what is the difficulty now? Just download and click install.

---

### Post by Yezinki on 2008-11-04
Exactly I did the same.

Thanks.

---

### Post by Yezinki on 2008-11-04
> **lisati said:**
> I got the copy on my machine from the [skype website]("http://www,wkype.com"), clicking on the "download" tab at the top of the screen (the download button tends to choose the Windows version) and choosing the version for Ubuntu.....

It's a "deb" file, so once the download is complete, you can open the file, and clicking on the "install package" button.

Edit: the direct link to the download page for Linux is [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)


You were correct smart man.

Thanks,

Regards.

---

### Post by Yezinki on 2008-11-04
> **crazyness003 said:**
> Yes, Synaptic is the application that lets you download from the repositories. Or you can quicly install skype by issuing this command in the terminal (Applications -> Accessories -> Terminal)
```
sudo apt-get install skype
```
Insert your password and then accept the rest of the necessary dependencies by typing Y
Then have fun. Be warned tho, the version for Linux is very outdated compared to the windows one. For win , you have 4.x. Linux is at 2.0


Didn't work either way ........

Thanks any how,

Regards,

Yezinki.

---

### Post by crazyness003 on 2008-11-04
> **redenex said:**
> [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)


Skype site do have the .deb file, so what is the difficulty now? Just download and click install.

The only difficulty is the problem of choice. By adding the medibuntu repositories you increase the app pool you can install throught Synaptic (or aptitude, apt-get or Add/Remove...)

For quick install go to the link, download, install the .deb and done.
For a little longer install, do what i said. The only difference is that when there's an available update, you will be auto-notified i the Update Manager. Plus, it adds the ability to add additional apps.

See, choice.

---

### Post by Yezinki on 2008-11-05
Repos didn't add........

Thanks,

Regards,

Yezinki.

---

### Post by lisati on 2008-11-05
> **redenex said:**
> [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)


Skype site do have the .deb file, so what is the difficulty now? Just download and click install.

Exactly what I said......it does have an Ubuntu version.

---

### Post by Yezinki on 2008-11-05
You indeed are a genius....

Can a Ubuntu user exchange cam with a window one?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-05
> **lisati said:**
> Exactly what I said......it does have an Ubuntu version.

Hi there,

Could you care to answer my post:

[http://ubuntuforums.org/showthread.php?p=6108378#post6108378](http://ubuntuforums.org/showthread.php?p=6108378#post6108378)

Sorry to have bothered,

Regards!

Yezinki.

---

