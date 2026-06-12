---
title: "Modem not working"
date: 2006-01-27
forum: Networking &amp; Wireless
---

### Post by Maskednightmare on 2006-01-27
I installed Ubuntu 5.10 For Your PC from the cds i got shipped from ubuntu.Everything is working fine except the fact that I have no internet connectivity at the moment.I have an Intel 536EP 56K internal modem installed in my pc.The device manager in Ubuntu displays this modem but does not detect it in Networking.I have tried using the method mentioned in [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) but it is not working for sum inexplicable reason.I have downloaded all the packages as mentioned in the guide.But when i got to the step of Compiling the Driver, I faced a problem : 
First we need to uncompress the downloaded file. Start a terminal window and run the following command: 

 tar xzf Intel-536EP-4.71.tgz
This assumes you saved the file downloaded from Intel in your home directory; otherwise, type cd <directory-where-the-file-is> before typing the tar command above. 

This will create a directory Intel-536 with the source contained in it. Change to this directory by typing 

 cd Intel-536
Still in the terminal window, type the following: 

 make clean

(*this is where Im stuck, wenever i type in make clean, it says make : command not recognised*
Now what am I supposed to do?

---

### Post by ddtmsa on 2006-01-28
[QUOTE=Maskednightmare]This will create a directory Intel-536 with the source contained in it. Change to this directory by typing 

 cd Intel-536
Still in the terminal window, type the following: 

 make clean

(*this is where Im stuck, wenever i type in make clean, it says make : command not recognised*
Now what am I supposed to do?[/QUOTE]

I posted a (fuller) answer to this in a recent thread in the Desktop Support forum. You need to install the Build-Essential and Linux-Headers packages off of the CD. 

> 
sudo apt-get install build-essential
sudo apt-get install linux-headers2.6.12-9-386

You may also have to download some complier packages to compile the driver.

> 
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb)


and then copy over to your ubuntu files and install them

> 
dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4-base_3.4.4-6ubuntu8_i386.deb gcc-3.4_3.4.4-6ubuntu8_i386.deb


and then make an appropriate link for compiling:
> 
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc


---

