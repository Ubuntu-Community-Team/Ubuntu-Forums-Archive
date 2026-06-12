---
title: "beginner here. please help with this mulimedia question"
date: 2011-01-23
forum: Multimedia Software
---

### Post by prsn4life on 2011-01-23
Hi, I am working on a web page which will have  links to my HD movies (in my ubuntu home server)  so i could click it and stream movies from any where out my house.
this is what i have learn i must do from the tutorials that i have seen online.
1. install my ubuntu home server.
2. install  LAMP(linux, Apache, My syquel, PHP).
3. configure so i can manage my headless machine from any where in the world.
4.install programs i need for the web interface. (which the can only be used in local machine)
5. sign up to webmin so i can log into domain.
6. create a static ip address.
7. install ftp
8. use [SIZE=1]BroadCam Video Streaming Server Software so i can stream movies from my site.

i have done 1,2,3,6
the problem i have is:
i can not install [/SIZE]
sudo aptitude install perl libnet-ssleay-perl openssl libauthen-pam-perl&#65279; libpam-runtime libio-pty-perl libmd5-perl 
which are the programs needed for the web interface. basically i can not install them
this is the error i get:
 couldn't find any package whose name or description matched "libmd5-perrl"

[IMG]file:///tmp/moz-screenshot.png[/IMG]Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/maverick/universe](http://us.archive.ubuntu.com/ubuntu/maverick/universe) libauthen-pam-perl am d64 0.16-2

Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/maverick/main](http://us.archive.ubuntu.com/ubuntu/maverick/main) libio-pty-perl amd64 1:1.08-1

Temporary failure resolving 'us.archive.ubuntu.com'
 Err [http://us.archive.ubuntu.com/ubuntu/maverick/universe](http://us.archive.ubuntu.com/ubuntu/maverick/universe) libnet-ssleay-perl amd64 1.36-1ubuntu1

Temporary failure resolving 'us.archive.ubuntu.com'
  E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/liba/libauthen-pam-perl/libauthen-pam-per1_0.16-2_amd64.deb:](http://us.archive.ubuntu.com/ubuntu/pool/universe/liba/libauthen-pam-perl/libauthen-pam-per1_0.16-2_amd64.deb:) Temporary failure resoliving 'us.archive.ubuntu.com'



the other problem i have is that the tutorial tells me that i need to go type /boot/grub$ sudo vim menu.list to change vga to 771 and change the command line for kernel.
i check and there is no file as menu.list in grub and also vim does not work. so i can not go to the next step which is changing the vga to 771 and add noreplace-paravert to the kernel command line.
also is it a good idea for me to use [SIZE=1]BroadCam Video Streaming Server Software for this project so  i can stream movies from my site.[/SIZE]
also just let you know i am using putty to access my ubuntu home server.
pleeeease help

---

