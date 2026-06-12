---
title: "easier way to load a webcam?"
date: 2009-03-25
forum: Multimedia Software
---

### Post by seabrighter on 2009-03-25
I'm trying to find out how to use my Aiptek webcam with Intrepid.  Every documentation I come across seems to point to some lengthy outdated instructions that ask me to learn programming.  Is there an easy way to do this without entering lines and lines of code?  I'll admit that I'm new to Ubuntu, but I thought the point of this OS was to make it easy for people to move away from Windows?  Do I really have to program the operating system to use my webcam?

---

### Post by dagoth_pie on 2009-03-25
if it doesnt work as soon as its plugged in, then odds are itll take a lil work to get running, but theres plenty of us here to help, what kind of connection does it use? usb?

---

### Post by seabrighter on 2009-03-25
> **dagoth_pie said:**
> if it doesnt work as soon as its plugged in, then odds are itll take a lil work to get running, but theres plenty of us here to help, what kind of connection does it use? usb?

Yes, it is a USB webcam.  It's a digital camera, but it's one that can function as either a webcam OR a flash drive when plugged in.  After you plug it in and turn it on, the camera's display lets you choose "camera" or "disk."

I can barely follow all the jargon about working with the terminal window.  Can't you just download files and copy them into the appropriate folders?  I suppose it's not hard to copy and paste lines of code into a terminal window, but I feel uncomfortable not knowing what all these commands mean and what they are doing (in the event that it doesn't work).

---

### Post by dagoth_pie on 2009-03-25
right well, first things first, plug it in and tell it to use the camera then. After it should be working go into the terminal and run the command
```
lsusb
```
all this will do is list all the devices you have connected via usb, it won't alter your system at all, if thats the part that worries you most, then theres two things I can tell you, if the command starts with "sudo" that means its going to ask for admin privlidges, the easiest way to find out what a command does is to type man before the command eg
```
man lsusb
```
then read the description of what the command does, if it sounds dodgey you can go down and read what the specific options people are telling you to use do, but to be honest, almost everyone here is safe to take advice from, expecially if they've got a high post count, if people are caught giving malicous commands then as far as I know its an instant ban, but if you could run ```
lsusb
``` then post back the what comes up after that will let us know if Ubuntu has drivers to run it built in.

---

### Post by seabrighter on 2009-03-26
dagoth, you're being VERY helpful, so let me just say that your guidance is much appreciated.

here's my lsusb results:

Bus 002 Device 002: ID 4971:ce15  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 009: ID 08ca:2102 Aiptek International, Inc. 
Bus 001 Device 004: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 003: ID 046d:c042 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Looks like it is on there as Device 009?

---

### Post by dagoth_pie on 2009-03-26
yep that'd mean its being detected fine, what application were you trying to get to run with it?

---

### Post by seabrighter on 2009-03-26
Tried to test it using Ekiga Softphone.  I ran through the nine step setup wizard that it has, and on the last step concerning video functionality, it said there was none detected.

---

### Post by dagoth_pie on 2009-03-26
right, well I don't have a webcam, but I did spend a few hours getting a friends one to work with skype, there was one program that was working with the webcam (cheese I think) meanwhile skype and camora wouldnt, because of a permissions problem, I'll head over to check his computer and see if I can find what I changed. Try out the cheese webcam booth
```
sudo apt-get install cheese
```
essentially that command does the same thing as going into synaptic package manager, and finding and installing the package "cheese" you can do it either way, I find it a lot faster to just put in the command when you know the name of the package your installing

---

