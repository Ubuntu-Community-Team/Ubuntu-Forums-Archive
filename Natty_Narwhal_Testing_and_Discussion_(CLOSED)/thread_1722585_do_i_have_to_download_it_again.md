---
title: "do i have to download it again?"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by utkarsh009 on 2011-04-05
ok! i had a question. say if i download and install the beta version of ubuntu 11.04 and then upgrade it to stable release. then will i have to download 700MB again or will it be just like a regular ~50MB upgrade?

---

### Post by lindsay7 on 2011-04-05
If the beta works for you and all is fine, then the upgrades and updates will do the trick, No need to do a reinstall.  you can stay ahead of the game by doing the following from time to time,

sudo apt-get upgrade 
sudo apt-get update

---

### Post by 23dornot23d on 2011-04-06
> 
sudo apt-get upgrade 
sudo apt-get update
Really want to do these the opposite way around .....

in fact I would do

[B]sudo apt-get update
sudo apt-get install aptitude
sudo apt-get aptitude safe-upgrade
[/B]

But this is just the way I like to update my system ..... it rarely lets me down doing it this way ......
but the first way works ...... update is always first though ......

---

### Post by lindsay7 on 2011-04-06
Yup! I never know which one should come fist so I run the sequence of update and upgrade until nothing new shows up. As for aptitude, I have never really understood the difference between apt and aptitude even after reading about in.

---

### Post by MacUntu on 2011-04-06
> **utkarsh009 said:**
> ok! i had a question. say if i download and install the beta version of ubuntu 11.04 and then upgrade it to stable release. then will i have to download 700MB again or will it be just like a regular ~50MB upgrade?

It depends how many packages have changed between beta and release.

---

### Post by 23dornot23d on 2011-04-06
> 
Yup! I never know which one should come fist so I run the sequence of  update and upgrade until nothing new shows up. As for aptitude, I have  never really understood the difference between apt and aptitude even  after reading about in.
@Lindsay7

The way I understand it ...... 
update - updates the package lists ....
upgrade - updates the programs using the lists that it has just updated ......

As for aptitude it seems much the same ..... except it does a safe-upgrade that seems to make sure that all the package dependencies are workable ..... if not it does not install
the packages that could have caused a problem to your system ......

I have done this for such a long time now and it is hard to break the habit or my system ,

(As using other ways - has sometimes caused me lots of grief ........
I just trust it more ....... but I guess what people use is what they are used to and what works best for them .......)

---

### Post by cor2y on 2011-04-06
You can also update the iso if you kept it via zsync from beta to final version.
Its what i do to save myself having to download a new iso everytime.
Here are some tutorials
[http://ubuntu-tutorials.com/2009/10/29/use-zsync-to-update-existing-iso-images/](http://ubuntu-tutorials.com/2009/10/29/use-zsync-to-update-existing-iso-images/)
[https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage)

---

### Post by utkarsh009 on 2011-04-06
thanks guys. your suggestions were really valueable especially zsync one.

---

