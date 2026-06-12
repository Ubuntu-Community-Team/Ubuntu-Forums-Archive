---
title: "Webcam server surveillance, setup help"
date: 2012-04-04
forum: Multimedia Software
---

### Post by Tjomissen on 2012-04-04
Hello everyone:)

My first post:D

Im trying to set up an "[MSI U160DX]("http://no.msi.com/product/nb/U160DX.html")" with "[Logitech Quickcam Messenge]("http://www.logitech.com/en-roeu/480/3378")" and Ubuntu 11.10 to make a webcam server to stream out on the internet.
I've been googlin without any luck of finding out how.

I got the webcam driver in place, I have Cheese, and it works fine.
now I just need to get the webcam server software and whatever other things that are needed.

_So I need help to get the software, install it, and set it up._:confused:

I have checked "sudo apt-get install webcam-server" but it cant find the file.

---

### Post by Paddy Landau on 2012-04-05
You would have to find suitable software to run it as a server. Logitech won't help you, as it supports only Windows (not even Mac).

I suspect that you'd have to use Ubuntu Server (or convert your current desktop to a server) before you could do achieve what you are after, unless you could find appropriate software.

Sorry I'm not much help, but it may help you in your search.

---

### Post by Tjomissen on 2012-04-05
Okey thanks, downloading Ubuntu server edit 11.10 now. What is the main diffrence between server edition and dekstop?

---

### Post by gordintoronto on 2012-04-05
I disagree with Paddy about using Ubuntu Server. You can install and run Apache on Ubuntu Desktop. This link has a step-by-step:
//www.linux.com/learn/tutorials/417799-create-a-cheap-and-effective-monitoring-system-with-ubuntu-linux-and-webcamserver

It includes a link for downloading the webcam-server program.

Ubuntu Server is all command line, so everything will take you ten times as long.

---

### Post by Tjomissen on 2012-04-06
After downloading [webcam-server_0.50-2.deb]("http://ubuntu.mirror.cambrium.nl/ubuntu//pool/universe/w/webcam-server/webcam-server_0.50-2_i386.deb")and installing the program, I try to run it from terminal:

ioctl (vidiocgcap): invalid argument
ioctl (vidiocspict): invalid argument
error setting video device parameters, using defaults
ioctl (vidiocgcap): invalid argument
ioctl (vidiocspict): invalid argument
not a valid video device? quitting.

My camera works fine in Cheese

---

