---
title: "Problem with firefox"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by Alkser on 2009-09-10
Hello there,
I recently had some problems with firefox. Whenever I start it it says "Checking for updates" "Finished checking for updates" and other things. I thought it updated my firefox but it redirects me to mozzila firefox's version 3.0.11 page. Now I closed firefox and opened it again and the same things are happenin "finished checking for updates" and it opens the 3.0.11 page. I went on help.ubuntu.com and looked for firefox. When I wanted to install the firefox 3.5 package it says it's already installed.

Also I have problems when opening add-ons and downloads. When I open any of those two firefox closes without giving any messages :\

Can somebody please help me?

---

### Post by shredder12 on 2009-09-10
Actually the firefox included in the repos of jaunty is still 3.0.11/13
so if you really want to install firefox 3.5 then download that package from firefox's website and before installing it remove the existing firefox..

and please **create a backup of you firefox configurations i.e. ~/.mozilla folder**

```
sudo apt-get remove firefox
```

this will save your configuration files.
then install firefox..
if you have download a debian package
install it using

```
sudo dpkg -i firefox_package.deb
```

hope that helps..

---

### Post by Alkser on 2009-09-11
> **shredder12 said:**
> Actually the firefox included in the repos of jaunty is still 3.0.11/13
so if you really want to install firefox 3.5 then download that package from firefox's website and before installing it remove the existing firefox..

and please **create a backup of you firefox configurations i.e. ~/.mozilla folder**

```
sudo apt-get remove firefox
```this will save your configuration files.
then install firefox..
if you have download a debian package
install it using

```
sudo dpkg -i firefox_package.deb
```hope that helps..

Thanks, and where can I download debian package?

---

### Post by shredder12 on 2009-09-11
I am sorry you won't find a debian package on the website (probably, m not sure)
but instead you will have to download the tar package.

Extract it .. and read the readme file..
You will probably find an installation procedure on the website.
follow it and you will be able to install firefox 3.5...

---

### Post by Alkser on 2009-09-11
> **shredder12 said:**
> I am sorry you won't find a debian package on the website (probably, m not sure)
but instead you will have to download the tar package.

Extract it .. and read the readme file..
You will probably find an installation procedure on the website.
follow it and you will be able to install firefox 3.5...

Thanks man. I installed firefox 3.5 :)

---

