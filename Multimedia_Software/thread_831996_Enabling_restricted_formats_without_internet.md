---
title: "Enabling restricted formats without internet"
date: 2008-06-17
forum: Multimedia Software
---

### Post by animesh4u on 2008-06-17
Hi, I am new to Ubuntu. I just installed it over my windows using Wubi 2 days back. I found out that I have to install restricted extras, but i dont have an internet connection, can i install them from my Ubuntu 8.04 CD. 
I tried searching for the extras in the CD,but didn't succeed. I'm not sure whether they are there on the CD or not, I read somewhere that the restrictes extras are provided with the 8.04 CD, just need to intall them.
( I also wanted to install emerald etc. )
Please help.

---

### Post by gandaran on 2008-06-17
you can download the package you need to a pen drive then install on your computer.
you can find every ubuntu package in the internet, just google the name of the application you need, and look for a ubuntu hardy .deb package, then just double click to install it.
don't download the ubuntu-restricted-extras package, as you will need a internet connection to install it, just download the various separate apps that make up this package.
here's the official ubuntu hardy 8.04 repository, has everything you'll need.[http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages)

---

### Post by Taemojitsu on 2009-02-10
Amazingly, this is on the first page of results if you search Ubuntu websites for 'Restricted formats'.

I'm trying to do the same thing, and it's a bit difficult because of all the dependencies. I did download a live DVD iso which has more commonly used packages, which hopefully means I won't get as many errors trying to install.

I go here:
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

and download every package related to my distribution. Some of these packages are available on the ubuntu repositories, but do not have certain restricted formats enabled.

I go to the repository mentioned by gandaran, and install everything related to the placeholder package mentioned on the [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") page. In my case it's here: [http://packages.ubuntu.com/hardy-updates/ubuntu-restricted-extras](http://packages.ubuntu.com/hardy-updates/ubuntu-restricted-extras)

Anything in 'universe', 'multiverse', or 'restricted' (on the package's description page) you'll probably have to download. I'm not yet sure how many of the 'main' package dependencies are already on the LiveCD.

You can also try [http://www.getdeb.net/](http://www.getdeb.net/) (donate!).

---

