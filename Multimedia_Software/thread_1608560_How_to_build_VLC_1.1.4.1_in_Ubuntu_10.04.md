---
title: "How to build VLC 1.1.4.1 in Ubuntu 10.04"
date: 2010-10-29
forum: Multimedia Software
---

### Post by aj.d on 2010-10-29
Hey folks,

I've downloaded vlc 1.1.4.1.tar.bz2 from the internet, as I have problem using the 'sudo apt-get' command which is due to the fact that my USB Internet Modem provider didnt cared to make it compatible with Linux. I presently connect to internet using Nokia PC Suite [available only in Windows, as you all may know] to browse the net. Currently I've a dual-boot with Ubuntu 10.04 and Windows 7.

I tried building it by following the instructions in the INSTALL file, but it wont just work!!! I am sure I'm missing something and it would be great if anyone could please help me out with the sequence of commands in this case!! 

Thanks,
-AJ

---

### Post by Yellow Pasque on 2010-10-29
You should find a PPA that has the latest VLC for Lucid. If you can't, at least post the output of your build attempt.

---

### Post by celldweller1591 on 2010-10-30
Simply use this guide to install VLC :- Open terminal and type :- 
> sudo add-apt-repository ppa:ferramroberto/vlc
sudo apt-get update
sudo apt-get install vlc mozilla-plugin-vlc
Details :- [http://www.webupd8.org/2010/08/install-vlc-114-in-ubuntu-via-new-ppa.html](http://www.webupd8.org/2010/08/install-vlc-114-in-ubuntu-via-new-ppa.html)

---

### Post by aj.d on 2010-10-31
> **celldweller1591 said:**
> Simply use this guide to install VLC :- Open terminal and type :- 

Details :- [http://www.webupd8.org/2010/08/install-vlc-114-in-ubuntu-via-new-ppa.html](http://www.webupd8.org/2010/08/install-vlc-114-in-ubuntu-via-new-ppa.html)


Hey,

I told in my post that I can't use that '*sudo apt-get*' command as I cant connect to internet from Ubuntu since my USB Modem doesnt supports Linux based OS :mad:

That's why I dwnldd vlc 1.1.4.1 source package from internet and need to build it. I tried the commands given in the instructions, but it isnt of much help, and hence I need the commands to build it!!

Cheers.

---

### Post by Yellow Pasque on 2010-10-31
Chances are that you need a lot of -dev packages, so if you don't have internet and can't use apt-get build-dep, it's not going to happen.

---

### Post by mc4man on 2010-10-31
You may want to take a look here - can't personally vouch for or say how capable it is -  though did try the vlc 1.1.4 and seemed ok, 
(the binary needs to be made executable before running 

[http://portablelinuxapps.org/](http://portablelinuxapps.org/)

---

### Post by aj.d on 2010-11-01
> **Temüjin said:**
> Chances are that you need a lot of -dev packages, so if you don't have internet and can't use apt-get build-dep, it's not going to happen.

there's a text file called INSTALL in the archived vlc that I downloaded that contains instructions for building the source. I tried the commands but the first one *./configure --prefix=/usr* didnt worked as it couldn't find one package. 

Do you now think that apt-get is necessary here....probably firing the commands properly would do but ya I may be wrong!!

---

### Post by aj.d on 2010-11-01
> **mc4man said:**
> You may want to take a look here - can't personally vouch for or say how capable it is -  though did try the vlc 1.1.4 and seemed ok, 
(the binary needs to be made executable before running 

[http://portablelinuxapps.org/](http://portablelinuxapps.org/)

ok i'll try that and let you know. Thanks anywz.

---

### Post by aj.d on 2010-11-01
guys I've a question though I feel tht it may be absurd...actually I'm not so experienced.:)

The first command to start the build process is *./configure --prefix=/usr*. On firing this command, it starts checking for dependencies [probably] and at the end it asks for a prompt about one particular package...when I typed in 'yes' n hit enter it seemed that the terminal hanged!!! :confused:

Now my question is that is a /usr partition necessary for this command to succeed?? Cause I dont have one....I got only a /root and swap!!

---

