---
title: "Camera Detection Issues"
date: 2010-03-20
forum: Multimedia Software
---

### Post by higashi on 2010-03-20
sorry, this is a double post. The reason i'm posting it again is because my first one has a typo in the title and i'm afraid no one will find it on time. Anyway, 

i have a kodak camera and i took pictures in its internal memory for an art project.
After taking all the pictures, i remember that , the last time i tried to put pictures onto my computer, it didn't work. The reason it didn't work last time is because the camera itself wasn't being detected; the memory card was.
So now, i REALLY need these pictures, and i have no idea how to take them from my camera's internal memory.
please please pleaase help me D:
thanks so much in advance
PS: using ubuntu 9.10

---

### Post by recycledhippy on 2010-03-20
I have had the same problem with my Kodak camera too. What I've done is dont let a program try to open anything up ie f-spot or something. I usally will end up with two Kodak folders on the desktop one for onboard memory one for memory card. I have then been able to open then from there. Dont know if this helps. good luck!

---

### Post by philip5 on 2010-03-20
Depends on which model it is but some will need an updated version of libgphoto2 to work. You can find packages of that in my repository on Launchpad for Karmic if you like. If the camera use the PTP2 protocol to transfer data then it usually doesn't show up as other mounted usb-media and you'll need an application that does that. I use Digikam for this but F-spot and others might work to. They all have in common that they use libgphoto2 for this.

Hope this helps.

[Edit. Spell correction of package name]

---

### Post by higashi on 2010-03-20
My camera is a Kodak EasyShareC763.
i dont know how to add your repository :\
can you just tell me what to add to my sources list?

---

### Post by 2hot6ft2 on 2010-03-20
> **higashi said:**
> My camera is a Kodak EasyShareC763.
i dont know how to add your repository :\
can you just tell me what to add to my sources list?
Well he sure didn't make it easy for you did he?
First off he didn't spell the package name right so it took a while to find it but here's how to install it from his ppa
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo add-apt-repository ppa:philip5/extra
```
then
```
sudo apt-get update
```
then
```
sudo apt-get install libgphoto2 
```

Hope that fixes you up.

---

### Post by higashi on 2010-03-21
after completing the last step, i get
E: Couldn't find package libgphoto2

---

### Post by philip5 on 2010-03-21
> **higashi said:**
> after completing the last step, i get
E: Couldn't find package libgphoto2
You might also need to add my key that my packages are signed with so your system can verify that you trust them.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 43C56F3F
```
Then repeat the update and install process as shown above.

---

### Post by higashi on 2010-03-21
Still can't find package libgphoto2  :\
(also, while doing this process, i got a partial distribution upgrade... what was that abuot?)

---

### Post by philip5 on 2010-03-21
> **higashi said:**
> Still can't find package libgphoto2  :\
(also, while doing this process, i got a partial distribution upgrade... what was that abuot?)
Are you sure you are using Ubuntu 9.10 Karmic Koala and not some other version of Ubuntu?

---

### Post by higashi on 2010-03-21
yes, im sure
> 
You are using Ubuntu 9.10
                - the Karmic Koala - released in October 2009 and supported until April 2011.
	

---

### Post by philip5 on 2010-03-21
Oh, not that strange as **2hot6ft2** happened to write the wrong name for the package. Make sure you use these names:

```
sudo apt-get install libgphoto2-2 libgphoto2-port0
```

I took for granted that they were right in the first place.

---

### Post by higashi on 2010-03-21
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgphoto2-2 is already the newest version.
libgphoto2-port0 is already the newest version.
The following packages were automatically installed and are no longer required:
  amarok-common libopal3.6.4 recordmydesktop libpt2.6.4-plugins libpt2.6.4
  libtag-extras1 amarok-utils
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

and it's still not detecting my camera... :\

---

### Post by malspa on 2010-03-21
Sorry if I'm missing something here, but why not simply copy the photos over from the internal memory to the memory card and then just plug the memory card into a USB card reader?

I have card readers for my XD cards and for my SD cards and I don't even bother with trying to connect the cameras to the computer anymore.

---

### Post by higashi on 2010-03-21
i don't know how to copy the photos onto a memory card...

---

### Post by malspa on 2010-03-21
> **higashi said:**
> i don't know how to copy the photos onto a memory card...

Dang, my son has the Kodak camera with him or I'd walk you through it.  I've done it with other cameras, too.  It's usually (but not always) pretty easy, especially if the memory card happens to be empty.  If you put the memory card in and find the photos that are stored in internal memory, and then play around in the menu you can find an option to copy or move the photos over to the card.

---

### Post by higashi on 2010-03-22
can't find that option

---

### Post by philip5 on 2010-03-22
Two things. Which version do you have installed of libgphoto2-2 now? Either check it with synaptic or something like that or in a terminal run:

```
apt-cache policy libgphoto2-2
```
The other thing is that I didn't find your camera model in the supported list of libgphoto2: [http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

What that mean in your case I don't know. It might work if you try to add it as some other camera that is like your camera or some generic ptp2 kind. I'm not sure. Might not be so easy as just connect and use as you have noticed.

The whole problem you have is that (what I understand) is that your camera does't show up as a usb-media (i.e a usb-memory or usb-harddisk) that you can copy from as many other cameras do.

This is my best guess without access to the camera it self to try with.

---

### Post by higashi on 2010-03-22
```

libgphoto2-2:
  Installed: 2.4.8-karmic~ppa1
  Candidate: 2.4.8-karmic~ppa1
  Version table:
 *** 2.4.8-karmic~ppa1 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
     2.4.6-1ubuntu6 0
        500 http://us.archive.ubuntu.com karmic/main Packages
        500 http://cz.archive.ubuntu.com karmic/main Packages

```

Also, im pretty sure it used to work fine before karmic. Oh well, i guess i'll just have to re-take the pictures  :\

---

