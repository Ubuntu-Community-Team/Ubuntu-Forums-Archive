---
title: "Ubuntu 9.04 and Nvidia Drivers"
date: 2009-06-22
forum: Multimedia Software
---

### Post by greg3305 on 2009-06-22
I'm having a hell of a time getting the Nvidia drivers installed. I've tried the 185 and 180 drivers without success, and have tried installing through the package manager and by using Nvidia's installer (following these directions: [http://forums.nvidia.com/index.php?showtopic=99513](http://forums.nvidia.com/index.php?showtopic=99513))
 
Either way, I'm left with only being able to access the console. Ctrl+alt+f7 gives me nothing but a blinking cursor.
 
I'll admit to being new to Linux, so any help you'd be willing to give a possible M$ convert would be fantastic. TIA.

---

### Post by Findarato on 2009-06-22
You should not install any drivers directly from nvidia. 
Ubuntu recognises your nvidia hardware on it's own. You can then activate it through "System->Administration->Harware drivers".

You probably want to got for a "dpkg-reconfigure xserver-xorg" in the terminal in order to clean up some of your current mess, but please someone correct me if I am wrong here (I am not that terminal-friendly yet :P).

---

### Post by AoSteve on 2009-06-22
He's definitely correct about not getting the nVidia drivers from nVidia.  I had that SAME issue before on 7.10 with my old GF4.   Once I used the Ubuntu repositories and installed the restricted drivers, everything worked perfectly.  

I'm pretty sure he's got the right command, not absolutely sure, it's been a while since I had to do that.

---

### Post by platosearwax on 2009-06-22
I guess I am wondering why, other than for philosophical reasons, one would not want to install the Nvidia drivers direct from them. In my case, I could not get a GUI of any sort no matter how I booted (usually I got the whited out screen where you could not see anything, but sometimes I got test patterns or boot direct to command).
 
What I did was make sure I had the driver downloaded to my Home area (I used OpenSUSE to download the drivers and copy to Ubuntu's Home). Then boot into Ubuntu and get to a command prompt (which it looks like you already do by default).
 
Then I run this:
 
```
sudo /etc/init.d/gdm stop
```
 
to make sure that you stop the x server and your graphics are off.
 
Then I get rid of the driver that is installed currently:
 
```
sudo apt-get remove nvidia* –purge
```
 
Then navigate to the directory where your driver has been downloaded and run this command:
 
```
sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run
```
 
Go through the prompts.
 
When that is done I just turn the x server on again:
 
```
 
sudo /etc/init.d/gdm start

```
And usually that is it. I have had the problem where I need to change the run level, which I do after killing the x server and running this:
 
```
 
sudo telinit 3

```
This is what works for me. It is a pain to have to do this every time you update the kernel but I was used to that with OpenSUSE and in my case there doesn't seem to be another way to get a graphical system running at all.

---

### Post by kpkeerthi on 2009-06-22
> **platosearwax said:**
> 
This is what works for me. It is a pain to have to do this every time you update the kernel but I was used to that with OpenSUSE and in my case there doesn't seem to be another way to get a graphical system running at all.

You don't have to do this everytime after a kernel update if you have configured dkms with nvidia. There is a howto in the tutorials section.

---

### Post by platosearwax on 2009-06-22
> **kpkeerthi said:**
> You don't have to do this everytime after a kernel update if you have configured dkms with nvidia. There is a howto in the tutorials section.
 
Fantastic!  I'll check that out.  
 
Thanks!

---

