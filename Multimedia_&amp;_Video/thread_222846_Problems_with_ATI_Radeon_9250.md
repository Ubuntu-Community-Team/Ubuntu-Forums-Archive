---
title: "Problems with ATI Radeon 9250"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by Matodo on 2006-07-25
Hello

I am using Ubuntu 6.06, the kernel version is 2.6.15.23-386, my Graphic Card is ATI RADEON 9250 (256 MB).

I couldn't get 3D acceleration working. I bought O'Reilly Ubuntu Hacks book, I followed 3 diffrent tutorials and I destroyed my OS in the last time. I have tried everything.

Now, I will give Ubuntu another chance, I reinstalled Ubuntu 6.06 & I didnt't install anythings else except the modem driver.

Please, I would like a step-by-step guide. I would like to see a detailed tutorial. (do this and this then go to [http://www.ati.com/](http://www.ati.com/) and download the latest  driver and you should do this to install it then ...)

Thanks for your help :)

---

### Post by Matodo on 2006-07-26
.......

---

### Post by Matodo on 2006-07-26
I read this [tutorial]("http://ubuntuforums.org/showthread.php?t=204910")and this [guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") I did what the authors said, finally I destroyed my OS again. :( Nothing works anymore
Should I reinstall Ubuntu ? Would somebody help me ?

---

### Post by matc on 2006-07-26
Got the same here with ATI Radeon 9000. I am really pissed off.

But most of the trouble goes to ATI for crappy fglrx drivers that don't support older cards anymore in 3D way. 

Unfortunately the normal "radeon" drivers with open source support don't work either (I am NOT in the mood of recompiling the world...)

I am thinking of buying an GeForce FX6200, but I don't know whether it is really faster (and my budget's limited...)

---

### Post by Darth Tux on 2006-08-26
All right, here we go. I recently got my 9250 working with ATI's latest 8.28.8 drivers. There are two ways I got this to work. The more complex way is detailed in this [guide]("http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26"). I will explain the easy way, step by step. 
[B]
First:[/B] Download driver 8.28.8 from this [link]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run"). After its done downloading, place it in your home folder.

**Second:** Open up a terminal by going to your menu bar and clicking on "Applications", then "Accessories" and then "Terminal". In the terminal type this:
```
 sudo chmod 777 ati-driver-installer-8.28.8.run 
```
```
 sudo sh ati-driver-installer-8.28.8.run 
```
The installer should pop up. I suggest following the default options until it is installed. After it is installed close the installer but leave your terminal open.

**Third:** Now type this into your terminal:
```
 sudo dpkg-reconfigure xserver-xorg 
```
Most of the defaults will be ok. Just make sure that you choose "fglrx" when your choosing the driver, and make sure, when you get to the module screen, that you enable "glx" and "dri". After it finishes your X server should now be reconfigured to use the new driver you installed.

Now restart your computer and you should have 3D acceleration. To check whether you do or not type in a terminal:
```
fglrxinfo
```
You should see something like this:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250 Generic
OpenGL version string: 2.0.5814 (8.28.8)
```

Then type:
```
glxgears -printfps
```
This will start a 3D gears rendering with a FPS printout. This is by no means a benchmark, just so you know. 

That should just about cover it. If this did not work for you then I suggest following the link provided earlier to the other guide.

**Troubleshooting:** If you experience random freezing in regular use or in games, then you need to add a line to your xorg.conf. If this is happening, in a terminal, type:
```
sudo gedit /etc/X11/xorg.conf
```
Then scroll down to the "Device" section. At the end of the "Device" section add this:
```
Option "AGPv3Mask" "0x00000002"
```
Save the file and close it. This should stop the freezing. 

Feel free to post about any other problems with it. I'll help however I can.

---

### Post by Johnathon on 2006-08-26
Thats worked for me... Thanks!

Now all I have to do is repair windoze, and then I can play Halo & Legends :D

---

### Post by Darth Tux on 2006-08-27
Good to hear. Mine was broken for some reason this morning, but I fixed by using the 8.28.8 drivers with the other guide. Thought you should know, just incase yours stops working.

---

### Post by Johnathon on 2006-08-27
Ok... Its got me basic graphics working.. but not my 3D. :'(

Could you point me at the other guide, and I'll try again.. Thanks!

---

### Post by Darth Tux on 2006-08-27
[http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26]("http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26")

There's the link. I suggest using the 8.24.8 drivers first. Then, if it works. Use the guide with the 8.28.8 drivers. Just make sure you remember to replace what it says in the guide with your driver version.

Also, post what it says when you type this into a terminal:

```
fglrxinfo
```

---

### Post by Johnathon on 2006-08-28
me@asus:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Edit:
I'm getting this error:

make: *** [configure] Error 127

---

### Post by Darth Tux on 2006-08-28
at what point on that guide are you getting that error?

---

### Post by Johnathon on 2006-08-28
./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/dapper

---

### Post by Darth Tux on 2006-08-29
did you follow the step for installing the neccessary software that allows you to build the package?

---

### Post by Johnathon on 2006-08-29
yep

---

### Post by Darth Tux on 2006-08-29
only thing I can suggest is for you to make sure you got the file name right, are you installing 8.24.8, or 8.28.8?

---

### Post by Johnathon on 2006-08-30
Hello... I was. I went back and tried again, reinstalling everything. It worked! Till I rebooted that was... and then Nothing. Black screen.](*,)  Tried using Ubuntus recovery thingy... But I'm not that hot on using a command line interface to repair the kernel. :(

So I've had to reinstall Linux. (a bit hard to access forums without a GUI, and I am NOT mucking about with lynx. I just dont have the time!)

Still debating whether to try again. After all, I've already had the worst that could happen happen - I've lost all my files and settings. Rubbish. Ah well, such is life.

Thanks for your help tho! :)

---

### Post by Kengee on 2006-08-30
8.28.8 is the only one to start with.  I had no luck installing 8.24.8 as there was no --buildpkg option for Ubuntu/6.06, which has worked for me.
Running 6.06 LTS 64-bit and ATI x1300 512mb. I was ready to give up on ATI until I used 8.28.8.

---

### Post by Darth Tux on 2006-08-30
Yea, it seems now that ATI is releasing a driver every month, that they are also increasing the quality of their drivers. Its about time.

---

### Post by Darth Tux on 2006-08-30
> **Johnathon said:**
> Hello... I was. I went back and tried again, reinstalling everything. It worked! Till I rebooted that was... and then Nothing. Black screen.](*,)  Tried using Ubuntus recovery thingy... But I'm not that hot on using a command line interface to repair the kernel. :(

So I've had to reinstall Linux. (a bit hard to access forums without a GUI, and I am NOT mucking about with lynx. I just dont have the time!)

Still debating whether to try again. After all, I've already had the worst that could happen happen - I've lost all my files and settings. Rubbish. Ah well, such is life.

Thanks for your help tho! :)

No problem. I always suggest trying again. I can't even begin to count how many times I have had to "try again" with ATI's drivers.

---

### Post by Johnathon on 2006-08-31
I installed it on my nice fresh new install, and it worked :D

Thanks for your help.

---

### Post by Darth Tux on 2006-09-04
well just so you know, shadow-c told me your problems could have probably been fixed by this:
```
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```

thanks shadow-c

---

### Post by Johnathon on 2006-09-15
Thanks :)

---

### Post by sinek on 2007-04-05
./ati-installer.sh: 165: Syntax error: Bad substitution
some one help pls,... i dont know what to do,.. 
i'm nooby

---

