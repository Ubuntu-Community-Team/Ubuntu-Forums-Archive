---
title: "[How to] Logitech Quickcam IM/Connect webcam on Kubuntu 6.10 (Edgy Eft)"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by binselam on 2006-11-20
I have been trying to install Logitech Quickcam IM/Connect webcam on Kubuntu 6.10 (Edgy Eft). So, I have searched the ubuntuforms and how-to's. Although, what I have found in both sites was very helpful, but it was not specific to my webcam and step by step approach. I wanted to contribute to community by posting this.

I followed the ubuntu-community`s Spca5xx documentations and Yoriko post with little modifications. 

It worked for me. I hope this helps you.



**STEP 1: **First, I have used ***lsusb*** to find out: 
          1) Vendor Id and Product ID 
          2) to see do I have usb support, and check the driver files for device support.  The supportted device list is available at the  Michael Xhaard's homepage ("http://mxhaard.free.fr/ ").
 
This list shows the lsusb result.
Bus 001 Device 005:*** ID 046d:08d9 Logitech, Inc.***
Bus 001 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical


**STEP 2:** Download latest Spca5xx source code to your home directory from Michael Xhaard's homepage. At the time of writing this installation guide, the latest source code version was  spca5xx-20060501.
            NOTE: There might be  a newer version of the driver by the time you install. Please check the web page :" [http://mxhaard.free.fr/](http://mxhaard.free.fr/) ". 
                       Latest driver is:gspcav1-20070508.tar.gz (swejuggalo indicated that works fine on Ubuntu 7.04). Make sure you substitue correct driver name in the following steps, if you use a different driver.
                       (You can see the instructions for the new driver in following post:   [http://ubuntuforums.org/showthread.p...09418#poststop]("http://ubuntuforums.org/showthread.p...09418#poststop")).

[I][B]cd ~ 
wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.orig.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.orig.tar.gz)[/B][/I]


**STEP 3: **Become root. To do that, you need to open a terminal window and enter following command(Please enter user password when it is prompted. In each terminal window, you just need to enter sudo 
            command and password once (for the first time).

***sudo -s***
Password:***######## ***

Note: Prompt should change to: root@yourmachine:


**STEP 4: **Download the necessary packages. The following packages are needed from the Ubuntu repositories for compiling. 
    [I]1. linux-headers-`uname -r`
    2. linux-restricted-modules-`uname -r`
    3. build-essential[/I]

*uname -r*
Identifies the version of running kernel. Exp: 2.6.17-10-generic

***apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential***


**STEP 5:** Compile the spca5xx source code. The linux stuff (drivers/programs) is installed under /usr/src. The downloaded driver files need to be placed to proper directory under linux. So, please type following commands to change directory,  move downloaded source files, unpack the source files and change into directory. (NOTE: This step assumes you downloaded the driver file to your home directory.)

[I][B]cd /usr/src
mv ~/spca5xx-220060501.orig.tar.gz . 
tar xfvz spca5xx-20060501.orig.tar.gz  
cd spca5xx- 20060501 [/B][/I]


STEP 6: Set the environment variable CC for spac5xx Makefile. In my case, Ubuntu  Edgy Eft uses gcc 4.1 as kernel compiler. (NOTE: your system might use gcc-4.0. if you use version gcc4.0, you need to modify the command as "***export CC=gcc-4.0***" So, please make sure of your compiler version.)

***export CC=gcc-4.1***


STEP 7: Set a link back to source code(headers).

***ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build ***

STEP 8: Now, we need to compile spca5xx source code, remove the old driver(from memory and hard drive), install the new driver and load the new driver. Please enter the following commands in the order given.

[I][B]make 
modprobe -r spca5xx 
rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx* 
make install 
modprobe spca5xx [/B][/I]

If everything went accordingly, there should be no error messages. When you type ***dmesg***, you should get something like shown above.

[17191980.272000] usbcore: deregistering driver spca5xx
[I][17191980.276000] drivers/media/video/spca5xx/spca5xx-main.c: driver spca5xx deregistered
[/I][17192035.756000] Linux video capture interface: v1.00
*[17192035.768000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: USB SPCA5XX camera found. Logitech QC IM/Connect*
[17192035.768000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_probe:5480] Camera type JPEG
[17192036.860000] /usr/src/spca5xx-20060501/drivers/usb/zc3xx.h: [zc3xx_config:558] Find Sensor HV7131R(c)
[17192036.872000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_getcapability:1765] maxw 640 maxh 480 minw 176 minh 144
[17192036.872000] usbcore: registered new driver spca5xx
[17192036.872000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
root@eagel:/usr/src/spca5xx-20060501#  


GOOD LUCK!

---

### Post by StratosL on 2006-11-27
Fantastic! Thanks! I was just about to give up!!! Works great...

---

### Post by binselam on 2006-11-30
I am glad to here that.

---

### Post by ickleangel on 2006-12-14
Thank you so much, i have finally got my camera working under ubuntu 6.10 edgy eft.

you are a hero!


ike,

---

### Post by cjbrooker on 2006-12-20
This also worked for me in Dapper Drake (6.06 LTS).

All I changed was the 'export CC=gcc-4.1' to 'export CC=gcc'. Other than that I followed your instructions exactly, including the dmesg command.

Thank you very much!

---

### Post by jstad on 2006-12-22
I dont see where to set export gcc-4.1 in the MakeFile. Im an idiot, any help!?

---

### Post by StratosL on 2006-12-23
Just in case you have not figured it out yet, you write that as a command in the terminal, you don't write it in any file

---

### Post by StratosL on 2006-12-23
Having compiled kernel 2.6.19.1, I found myself without a camera again. 

Looking around, I found this fantastic site, which provides a new kernel module. Check it out:

[http://mxhaard.free.fr/index.html](http://mxhaard.free.fr/index.html)

StratosJL

---

### Post by gu014 on 2007-01-03
Hello,

Can someone please provide the model number for this Logitech Quickcam IM/Connect as i would like to purchase the exact model.  Any help would be appreciated.  Thank you.

---

### Post by dvarsam on 2007-01-03
> **gu014 said:**
> Can someone please provide the model number for this Logitech Quickcam IM/Connect as I would like to purchase the exact model.

And please provide a snapshot of it too!
Cause other people might be interested - including me!
Thanks.

---

### Post by cblanquer on 2007-01-03
I could just make work a Logitech Quickcam Chat, installing the latest version from December 2006. The name of the driver changes, the quality of the image is not so good as in W but definitly working ! Thanks a lot.
Please notice the driver name changes to GSPCA with new linux kernels (see link [http://mxhaard.free.fr/index.html](http://mxhaard.free.fr/index.html) ), so follow the instructions changing the names accordingly.
Thanks also to the GSPCA/SPCA5xx developpers !
Let us hope soon a new Skype release will work with video unde rLinux (one less point for W).

---

### Post by dpm on 2007-01-05
> **dvarsam said:**
> And please provide a snapshot of it too!
Cause other people might be interested - including me!
Thanks.

> **gu014 said:**
> Hello,

Can someone please provide the model number for this Logitech Quickcam IM/Connect as i would like to purchase the exact model.  Any help would be appreciated.  Thank you.

[http://www.logitech.com/index.cfm/products/details/ES/EN,CRID=2204,CONTENTID=11525](http://www.logitech.com/index.cfm/products/details/ES/EN,CRID=2204,CONTENTID=11525)
         P/N: 961459-0412

(note that I couldn't find this product on the US Logitech site)

And its ID:

```
$ lsusb
Bus 001 Device 002: ID 046d:08d9 Logitech, Inc.
```Just a couple of things: 
The **spca5xx** driver version included in Edgy is **0.57.xx**. This version did still not support this particular webcam. Support for this webcam was first added in version **0.60.00** of the driver. See the changelog of the driver at [http://mxhaard.free.fr/news.html](http://mxhaard.free.fr/news.html) for more information.

Luckily, the **0.60.00** driver sources are available from the ubuntu repositories in the **spca5xx-source** package. Once the package is installed, the sources can be unpacked and compiled and installed as per the instructions on the original post.

Notice also what cblanquer said: the newer versions of the driver are no longer called **spca5xx** but **gspcav1** (v 1.00.11 is the latest at the time of writing, again, see the changelog). In any case, if your webcam is supported by the **spca5xx v0.60.00** driver, there is no need to install the latest driver.

I hope this bit of background information helps.

Cheers.

---

### Post by GarBhaD on 2007-01-05
I just bought a Logitech Quickcam Communicate STX Plus.

BTW, the webcam ID is
```

Bus 002 Device 002: ID 046d:08ad Logitech, Inc.

```
I followed all the steps in this thread and I could install it successfully.
Thanks a lot for creating this post!!

Still, there's a little issue: the colors look weird and the picture is mirrored. How can I configure my webcam?

[QUOTE=cblanquer]Please notice the driver name changes to GSPCA with new linux kernels (see link [http://mxhaard.free.fr/index.html](http://mxhaard.free.fr/index.html) ), so follow the instructions changing the names accordingly. [/QUOTE]

Whops! I used the old driver. Could this be the reason why I don't see the video correctly?

Edit:

I tried the new driver and colors look much better now. Image is still mirrored though. Guess this is normal operation for webcams?
Again, thanks a lot for this thread!

---

### Post by Cushie on 2007-01-05
ref:  >>STEP 1: First, I have used [SIZE="4"][COLOR="Black"]Isusb [/COLOR][/SIZE]to find out: <<

Just a novice trying to set up my webcam

I have searched the computer help, the forum help and even Google can't find "Isusb"  Where do I find this command/programme and how do you use it?

If I get passed this hurdle the rest might be easier?  

Help appreciated.

---

### Post by GarBhaD on 2007-01-06
> **Cushie said:**
> ref:  >>STEP 1: First, I have used [SIZE="4"][COLOR="Black"]Isusb [/COLOR][/SIZE]to find out: <<

Just a novice trying to set up my webcam

I have searched the computer help, the forum help and even Google can't find "Isusb"  Where do I find this command/programme and how do you use it?

If I get passed this hurdle the rest might be easier?  

Help appreciated.

Try with **L**SUSB instead of ISUSB (in lowercase, of course).

---

### Post by Andrew1234 on 2007-01-08
Problem sorted

---

### Post by Cushie on 2007-01-10
Thanks Andrew, I got the command ok, managed the first part of the procedure, a few more challenges ahead!  Many Thanks

---

### Post by jjcmmgb on 2007-01-10
Hi there,

Will this procedure work also for my old Logitech Quickcam Pro
The ID I found is ID 046d:0810 Logitech, Inc. QuickCam Pro

Many Thanks

---

### Post by seabee on 2007-01-11
Ive been trying to follow the instructions but no luck. so i tried again using the **gspcav1** driver instead. Im using Dapper Drake, and so I changed the code as was suggested in this thread. I keep getting stuck on the final stage,

[B]make
modprobe -r spca5xx
rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
make install
modprobe spca5xx[/B]

when i do the **modpobe -r gspcav1** line (changed from spca5xx) i get a file not found error.. what am i doing wrong?

---

### Post by Andrew1234 on 2007-01-11
Same mistake I made, you are trying to update a driver(spca5xx) here not the file you have downloaded(gspcav1) just type in as below

> 
make
modprobe -r spca5xx
rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
make install
modprobe spca5xx


I still have some issues thro as it does not show full screen only half of the image.

---

### Post by seabee on 2007-01-11
I tried again, this time without changing **spca5xx**. So I entered,

[B]make
modprobe -r spca5xx
rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
make install
modprobe spca5xx[/B]

It says, **Module spca5xx not found**

When I try and modify the code for the **gspca** driver, something is out of place.

When I followed the instructions for the older **spca5xx**, everything went smoothly. I had no errors. However the driver didnt seem to get my webcam into action. 

Any chance someone could post the code for the **gspca** driver 'as is' so dummies like me can cut and paste?

---

### Post by cblanquer on 2007-01-13
Hi,

As I am fully reinstalling my system ](*,) , it is the webcam turn so I shall try to document whatever I do in order to help.
But I am basically cloning the instructions quite well detailed on the first post.
I hope this helps. :) 
======

**STEP 1**
Not necessary for me, as I knew already I would need it (ekiga/gnomemeeting does not find it as a device). 

**STEP 2**
I downloaded the new driver from the site [http://mxhaard.free.fr/](http://mxhaard.free.fr/). The file name used that time is: gspcav1-20070110.tar.gz
New versions will have different names. 
I copied it to a directory in my home folder that I called ~/lib/webcam.driver.

**STEP 3**
Skipped it, I preferred to use "sudo".
I opened a terminal (by the way I reduce the size and set it to "always on top").

**STEP 4**
Similar to former instructions - please follow them:
> sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential

> sudo apt-get install gcc-4.1
or > sudo apt-get install gcc-4.0
Depending on which is available. Remember this for a later instruction.
As my system was fresh installed, I did get only the compile tools.

**STEP 5**
Here comes the fun! Instead of moving I just copy to avoid a reload next time...
> cd /usr/src
sudo cp ~/lib/webcam.driver/gspcav1-20070110.tar.gz .

Please do not forget the space-dot at the end in order to properly copy your file.

Now next actions:
> sudo tar xfvz gspcav1-20070110.tar.gz
cd gspcav1-20070110

**STEP 6**
> export CC=gcc-4.1
If gcc-4.1 was not available :
> export CC=gcc-4.0
**STEP 7**
> sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build 

**STEP 8**
First prepare and eliminate the former driver:
> sudo make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
Then set and load the new one:
> sudo make install
sudo modprobe gspca

**THE END**
Type
> dmesg
And see results at the bottom (specs will depend on your H/W)
> [17188664.212000] /usr/src/gspcav1-20070110/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
[17188664.212000] /usr/src/gspcav1-20070110/gspca_core.c: [spca5xx_probe:3983] Camera type S561 
[17188664.220000] /usr/src/gspcav1-20070110/gspca_core.c: [spca5xx_getcapability:1189] maxw 352 maxh 288 minw 160 minh 120
[17188664.220000] usbcore: registered new driver gspca
[17188664.220000] /usr/src/gspcav1-20070110/gspca_core.c: gspca driver 01.00.12 registered


Now it seems ready. 
Actually I had to review and redo as I made first a mistake building and then calling the new module (gspcav1 instead of gspca ].

Test with ekiga is SUCCESSFUL ! :)  Now waiting for a linux new Skype version (my contacts use all Skype). Good luck !

See 3 screenshots...

=============================================
Updates since I installed Ubuntu 7.04.
My TV card DVB-T features were not enabled by default so that I reinstalled the TV drivers for DVB.
Since then the card works ok (by means of Kaffeine I have access to the TV digital terrestial channels) but the webcam is driver is BROKEN.
I have tried the reinstall for several of the new versions of the webcam drivers, unsuccessful. There is a conflict somewhere that does not allow the webcam device to be created (I would expect a "video2" device).

Here is the end of dmesg after the last compilation:
[11861.956000] gspca: disagrees about version of symbol video_devdata
[11861.956000] gspca: Unknown symbol video_devdata
[11861.956000] gspca: disagrees about version of symbol video_unregister_device
[11861.956000] gspca: Unknown symbol video_unregister_device
[11861.956000] gspca: disagrees about version of symbol video_device_alloc
[11861.956000] gspca: Unknown symbol video_device_alloc
[11861.956000] gspca: disagrees about version of symbol video_register_device
[11861.956000] gspca: Unknown symbol video_register_device
[11861.956000] gspca: disagrees about version of symbol video_device_release
[11861.956000] gspca: Unknown symbol video_device_release

---

### Post by dabl on 2007-01-14
Yay!  It wasn't quick or pretty, and it took 3 tries, but this Linux nooB pulled it off, with the new gspca file. THANK YOU, FOLKS!

:mrgreen:

---

### Post by L34NN3 on 2007-01-14
Hi all

I followed everything above to the letter (and dot space lol) and all i got was "no such file or directory" to 
sudo mv ~/lib/webcam.driver/gspcav1-20070110.tar.gz .
Couldn't get any futher than that...

I am still at a complete loss. This nOOb mite be beaten...

---

### Post by dabl on 2007-01-15
Probably you downloaded the file somewhere different than your home directory.  Like maybe the desktop?  I like to use Krusader for such file-moving activities.  It has a "root mode" that you can use if you need to be root, such as this project requires.  Krusader looks a lot like the original Windows File Manager (Win 3.1), you've a left pane and a right pane, and some cool command buttons along the bottom to make new directories and so on.  I got Krusader from Automatix, but I think you can also get it from the repositories, using your package manager.

HTH  :)

---

### Post by L34NN3 on 2007-01-15
I have gspcav-1 saved to desktop and to home...It is a zip file an I am not sure exactly what to do with it. If I unzip it, as soon as I close the window it unzips into, the whole unzipped file vanishes...

I am at a loss as most of the comand listed in the posts are either not recognised or it says file/directory not recognised...

---

### Post by L34NN3 on 2007-01-15
Oh a P.S. When I follow step 4 I get this:

leanne@leanne-laptop:~$ sudo apt-get install linux-headers-leanne-r linux-restricted-modules-leanne-r build-essential
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-headers-leanne-r


Can't get any further...

---

### Post by L34NN3 on 2007-01-15
PPS I'm using Edgy if that matters...

---

### Post by L34NN3 on 2007-01-15
Erm I have tried to make a directory with Krusaer called SPCAV-1. I have moved the file into this. It is still zipped tho hmmm

---

### Post by cblanquer on 2007-01-15
Please restart reading and understanding carefully the steps, eventually checking the initial post. Applying instructions with success requires some skills and understanding of each step. And not to be  shy of making small errors.

You must first know how to download a file, I do it myself form my browser (Firefox) and set where I want it to be stored, in my case in the "~/lib/webcam"

Regarding the location:
~ means your home directory
lib was created by me, then I "cded" (moved into using cd command in a terminal or from the file browser just clicking the directory to enter) it and created the other directory webcam the same way.

Good luck.

---

### Post by seabee on 2007-01-17
oh well, no luck for me. The driver seems to be installed correctly, but nothing comes up in either Ekiga or Kopete. My webcam does have a Pixart chip, but maybe because I bought it in Japan it doesn't like the driver..

---

### Post by Nim on 2007-01-17
[QUOTE=binselam;1782440]
cd ~ 
wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.orig.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.orig.tar.gz)


When I do this it says:

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.


any ideas??

---

### Post by seabee on 2007-01-19
I've only just noticed that the heading of this thread says "... for Kubuntu ..." as opposed to *Ubuntu*. I'm actually running Ubuntu ( Edgy Eft ). Will that make any difference to the instructions?

---

### Post by dpm on 2007-01-21
> **seabee said:**
> I've only just noticed that the heading of this thread says "... for Kubuntu ..." as opposed to *Ubuntu*. I'm actually running Ubuntu ( Edgy Eft ). Will that make any difference to the instructions?

No, it does not make any difference. 

The instructions apply to Ubuntu as well as Kubuntu, since you'll be compiling and installing a Linux driver, which is independent of the desktop manager (KDE for Kubuntu, GNOME for Ubuntu) you are using.

Cheers.

---

### Post by ramjet_1953 on 2007-01-25
Sorry to say, it didn't work for me.

I have a Logitech QuickCam for Notebooks Pro.
The camera LED comes on, but all I get is a grey screen.

It worked OK in Dapper and works in Feisty, but I just can't seem to crack it in Edgy.

Regards,
Roger 8-)

---

### Post by Doug11 on 2007-01-26
I keep getting this error when I run the >sudo modprobe -r spca5xx< command



doug@home:/usr/src/gspcav1-20070110$ sudo modprobe -r spca5xx
FATAL: Module spca5xx not found.


Any ideas??

---

### Post by cblanquer on 2007-01-27
Hi Doug11

Check one of my former posts in the thread, it might be you are not using the very last driver.
Good luck.

---

### Post by Doug11 on 2007-01-27
> **cblanquer said:**
> Hi Doug11

Check one of my former posts in the thread, it might be you are not using the very last driver.
Good luck.

As far as I know,,this is the latest one,,,I'm using the>gspcav1-20070110.tar.gz<  I've lookked around,,if there is a more recent one than this, plz let me know. Thx

I also should say I'm using Edgy amd64 with the 2.6.19 kernel.

---

### Post by irv on 2007-01-29
I just bought a Quickcam Communicate STX this past weekend, and this how-to did the trick for me. The first time around I had problem because I was using the older driver. The second time around, on step 4 I did the (sudo apt-get install gcc4.0) and got a error loading mod, the third time on step 4 I did the (gcc4.1) and everything worked. I get a great video and sound in Ekiga.

I only have one question, is there any software for Linux that is anywhere close to the software that come with QuickCam for Windows? I would like to capture videos and still pictures to send via email.
Thanks for the great post in this How-To.
Irv:D

---

### Post by JayJones on 2007-01-29
I've had this creative live! videoIM cam for a bit, and I can't get this working:

lsusb: ID 041e:4055 Creative Technology, Ltd

(this is supposedly supported on the big list at [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html))

os: Dapper
kernel: 2.6.15
gcc: gcc-4.0

I initially tried spca5xx, and now I'm trying gspcav1-20070110.  In both cases, I can make the project, make install, modprobe, and the drivers are loaded properly:

dmesg>
usbcore: registered new driver gspca
/usr/src/gspcav1-20070110/gspca_core.c: gspca driver 01.00.12 registered

what is happening is; no device node is being created at /dev/video or /dev/video0, which is needed by the camorama and gqcam tools.  furthermore, nothing (visually) happens with the webcam when I a. plug it in or b. press the button on the top.  So, anybody have an idea about who's supposed to be creating /dev/video or /dev/video0?  I presume it would be the gspca module who should be creating it, but nothing seems to be detecting/turning on the webcam, even though it's detected on usb.

Any help would be useful, I'm almost fed up with this issue.

---

### Post by mrojas73 on 2007-02-06
> **cblanquer said:**
> Hi,

As I am fully reinstalling my system ](*,) , it is the webcam turn so I shall try to document whatever I do in order to help.
But I am basically cloning the instructions quite well detailed on the first post.
I hope this helps. :) 
======

**STEP 1**
Not necessary for me, as I knew already I would need it (ekiga/gnomemeeting does not find it as a device). 

**STEP 2**
I downloaded the new driver from the site [http://mxhaard.free.fr/](http://mxhaard.free.fr/). The file name used that time is: gspcav1-20070110.tar.gz
New versions will have different names. 
I copied it to a directory in my home folder that I called ~/lib/webcam.driver.

**STEP 3**
Skipped it, I preferred to use "sudo".
I opened a terminal (by the way I reduce the size and set it to "always on top").

**STEP 4**
Similar to former instructions - please follow them:



or 
Depending on which is available. Remember this for a later instruction.
As my system was fresh installed, I did get only the compile tools.

**STEP 5**
Here comes the fun! Instead of moving I just copy to avoid a reload next time...


Please do not forget the space-dot at the end in order to properly copy your file.

Now next actions:


**STEP 6**

If gcc-4.1 was not available :

**STEP 7**


**STEP 8**
First prepare and eliminate the former driver:

Then set and load the new one:


**THE END**
Type

And see results at the bottom (specs will depend on your H/W)


Now it seems ready. 
Actually I had to review and redo as I made first a mistake building and then calling the new module (gspcav1 instead of gspca ].

Test with ekiga is SUCCESSFUL ! :)  Now waiting for a linux new Skype version (my contacts use all Skype). Good luck !

See 3 screenshots...
Aswome, your guide worked great for me on my aspire laptop running edgy!

Thank you.

---

### Post by OakRand on 2007-02-08
> **JayJones said:**
> 
what is happening is; no device node is being created at /dev/video or /dev/video0, which is needed by the camorama and gqcam tools.  furthermore, nothing (visually) happens with the webcam when I a. plug it in or b. press the button on the top.  So, anybody have an idea about who's supposed to be creating /dev/video or /dev/video0?  I presume it would be the gspca module who should be creating it, but nothing seems to be detecting/turning on the webcam, even though it's detected on usb.

Any help would be useful, I'm almost fed up with this issue.

I had the same problem. Check out the following page:[http://www.myl.ro/forum/index.php?showtopic=2185](http://www.myl.ro/forum/index.php?showtopic=2185)

Here are the necessary instructions. Following the guide in the first post of this thread, then:

1. Install Video4Linux if you haven't done so already
> sudo apt-get install libpt-plugins-v4l

2. Open xorg.conf 
> sudo gedit /etc/X11/xorg.conf

3. Add the following to 'Section "Module'
Load "v4l"

4. Make an init script that loads the webcam:
> sudo touch /etc/init.d/webcam
> sudo chmod +x /etc/init.d/webcam
> sudo gedit /etc/init.d/webcam

and add the following two lines:

!#/bin/sh
for i in 0 1 ;do if [ ! -f /dev/video$i ]; then echo "Creating /dev/video$i" && mknod /dev/video$i c 81 $i && chown :adm /dev/video$i && chmod 660 /dev/video$i; else echo "/dev/video$i already exists";fi;done

5. Update
> sudo update-rc.d webcam defaults

6. Reboot

---

### Post by Celil Rifat on 2007-02-10
Worked for my 

Bus 002 Device 006: ID 046d:08d9 Logitech, Inc.

Excellent guide. Thanks!

---

### Post by cblanquer on 2007-02-11
Try what I wrote here:
[http://ubuntuforums.org/showthread.php?p=2009418#poststop](http://ubuntuforums.org/showthread.php?p=2009418#poststop)
 
Do not download from the link but rather go to the host site and find the appropriate driver.

---

### Post by browneyedgirl65 on 2007-02-23
> **binselam said:**
> I have been trying to install Logitech Quickcam IM/Connect webcam on Kubuntu 6.10 (Edgy Eft). So, I have searched the ubuntuforms and how-to's. Although, what I have found in both sites was very helpful, but it was not specific to my webcam and step by step approach. I wanted to contribute to community by posting this.

GOOD LUCK!

<strike>I am very convused by this because the folks over at the site say to use gspcav1 for linux kernels greater than 2.6.11, and edgy's at 2.6.17.  So I was using the gspca stuff, but I cannot find the correct module to modprobe...agh??</strike>

In the immortal words of RoseannaDanna: NEVUH MIND.  And, thanks!  The instructions worked beautifully.

---

### Post by cblanquer on 2007-02-24
See my instructions completing the initial ones, there I state the module to load, haven't you read this ? That worked to me in 3 PCs.
[http://ubuntuforums.org/showthread.php?p=2009418#poststop](http://ubuntuforums.org/showthread.php?p=2009418#poststop)

---

### Post by dabl on 2007-02-25
I just ran through the process on Feisty, with a Logitech Quickcam, and found a couple of deviations were required. While it is fresh in mind, I'll paste in binselam's original instruction, and note the deviations as of today.  Thanks, binselam, for the original great job!

QUOTE:

STEP 1: First, I have used lsusb to find out:
1) Vendor Id and Product ID
2) to see do I have usb support

This list shows the lsusb results.
Bus 001 Device 005: ID 046d:08d9 Logitech, Inc.
Bus 001 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
[B]
EDIT:  Not needed -- I knew it was Logitech Quickcam[/B]

STEP 2: Download latest Spca5xx source code to your home directory from Michael Xhaard's homepage. At the time of this installation, the latest source code version is spca5xx-20060501.

cd ~
wget [http://mxhaard.free.fr/spca50x/Downl...01.orig.tar.gz](http://mxhaard.free.fr/spca50x/Downl...01.orig.tar.gz)

**EDIT: The new one is named gspcav1-20070110.tar.gz and is found here: [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)**


STEP 3: Become root. To do that, you need to open a terminal window and enter following command(Please enter user password when it is prompted.

sudo -s
Password:########

Note: Prompt should change to: root@yourmachine:

**EDIT: In (K)Ubuntu you use the "sudo" command in front of the commands give below, EXCEPT for a couple of them noted below.**

STEP 4: Download the necessary packages. The following packages are needed from the Ubuntu repositories for compiling.
1. linux-headers-`uname -r`
2. linux-restricted-modules-`uname -r`
3. build-essential

uname -r
Identifies the version of running kernel. Exp: 2.6.17-10-generic

apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential


STEP 5: Compile the spca5xx source code. The linix stuff is installed under /usr/src. So, please type following commands to change directory, move downloaded source files, unpack the source files and change into directory.

cd /usr/src
mv ~/spca5xx-220060501.orig.tar.gz .
tar xfvz spca5xx-20060501.orig.tar.gz
cd spca5xx- 20060501
[B]
EDIT: For the command-line impaired like me, it is easier to open the GUI file manager of your choice (I use Krusader), and copy the file that you downloaded to the /usr/src folder, and paste it in there. That will eliminate the first two commands in Step 5.[/B]


STEP 6: Set the environment variable CC for spac5xx Makefile. In this case, Ubuntu Edgy Eft uses gcc 4.1 as kernel compiler.

export CC=gcc-4.1

**EDIT:  This was a cause of grief and lost time, because if you use "sudo export CC=gcc-4.1" you will get an error: export command not found. For this command, do NOT use "sudo", just type in your non-super user mode.**

STEP 7: Set a link back to source code(headers).

ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build

**EDIT: Again, no need to be "sudo" to do this one.**

STEP 8: Now, we need to compile spca5xx source code, remove the old driver(from memory and hard drive), install the new driver and load the new driver. Please enter the following commands in the order given.

make
modprobe -r spca5xx
rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
make install
modprobe spca5xx

**EDIT: "sudo modprobe -r gspca" or "sudo modprobe -r gspcav1" were ineffective, resulting in an error.  Tried it in non-super mode, and still got nada.  Just skip it -- it didn't seem to be essential.**

If everything went accordingly, there should be no error messages. When you type dmesg, you should get something like shown above.

[17191980.272000] usbcore: deregistering driver spca5xx
[17191980.276000] drivers/media/video/spca5xx/spca5xx-main.c: driver spca5xx deregistered
[17192035.756000] Linux video capture interface: v1.00
[17192035.768000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: USB SPCA5XX camera found. Logitech QC IM/Connect
[17192035.768000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_probe:5480] Camera type JPEG
[17192036.860000] /usr/src/spca5xx-20060501/drivers/usb/zc3xx.h: [zc3xx_config:558] Find Sensor HV7131R(c)
[17192036.872000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_getcapability:1765] maxw 640 maxh 480 minw 176 minh 144
[17192036.872000] usbcore: registered new driver spca5xx
[17192036.872000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
root@eagel:/usr/src/spca5xx-20060501#


GOOD LUCK!

ENDQUOTE

---

### Post by bomanizer on 2007-02-27
```

root@mato:/usr/src/gspcav1-20070110# export CC=gcc-4.1
root@mato:/usr/src/gspcav1-20070110# ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build 
root@mato:/usr/src/gspcav1-20070110# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20070110 CC=gcc-4.1 modules
make: *** /lib/modules/2.6.17-11-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

```

?:( ?

---

### Post by binselam on 2007-02-28
> **bomanizer said:**
> ```

root@mato:/usr/src/gspcav1-20070110# export CC=gcc-4.1
root@mato:/usr/src/gspcav1-20070110# ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build 
root@mato:/usr/src/gspcav1-20070110# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20070110 CC=gcc-4.1 modules
make: *** /lib/modules/2.6.17-11-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

```

?:( ?
Hi, I assumed that you are asking" What is the problem?"
It is possible that you missed something in step 5, or you do not have sudo rights. 
First, please make sure you have sudo rights. 
If it is not the case, you do not have correct directories or links (ln) created to those directories. If you are using newer libraries, you should substitute the correct directory/library names in the below steps. 

STEP 5: Compile the spca5xx source code. The linux stuff is installed under /usr/src. So, please type following commands to change directory, move downloaded source files, unpack the source files and change into directory.

cd /usr/src
mv ~/spca5xx-220060501.orig.tar.gz .
tar xfvz spca5xx-20060501.orig.tar.gz
cd spca5xx- 20060501


STEP 6: Set the environment variable CC for spac5xx Makefile. In this case, Ubuntu Edgy Eft uses gcc 4.1 as kernel compiler.

export CC=gcc-4.1


STEP 7: Set a link back to source code(headers).

ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build

STEP 8: Now, we need to compile spca5xx source code, remove the old driver(from memory and hard drive), install the new driver and load the new driver. Please enter the following commands in the order given.

make
modprobe -r spca5xx
rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
make install
modprobe spca5xx

---

### Post by cblanquer on 2007-03-01
doug@home:/usr/src/gspcav1-20070110$ sudo modprobe -r spca5xx
FATAL: Module spca5xx not found.

This means you have not the old "spca5xx" module loaded, this is not an issue, you have to worry if the new module does load properly and you get your functionality.
Review accurately the instructions, I think you should quickly fix it.
Good luck.

---

### Post by cblanquer on 2007-03-01
Hi Biselam,

Please check your notes, there is a different driver than spca5xx for recent linux kernel versions: gspca
I have added this update in a former entry of the thread, based on your great initial instructions, but I guess the new one must be preferred to spca5xx.

So loading the new driver is made with "modprobe gspca", if of course this driver has been previously installed.
Greetings.

---

### Post by cblanquer on 2007-03-01
bomanizer,

Try to repeat steps form the beginning, see what I wrote in [http://ubuntuforums.org/showthread.php?p=2009418#poststop](http://ubuntuforums.org/showthread.php?p=2009418#poststop) , that worked at least 3 times without any error.
Kippis.

---

### Post by maltinho on 2007-03-02
Thanks alot! The tutorial is great. My Logitec Communicate STX rocks on LINUX now!:guitar:

---

### Post by binselam on 2007-03-07
Hi cdlanquer, 
Thanks. It is a nice update(revision).
binselam

---

### Post by noah_parkcity on 2007-03-25
Thank you for the in-depth guide

I am such a n00b i cant get through set 5

STEP 5: Compile the spca5xx source code. The linux stuff (drivers/programs) is installed under /usr/src. The downloaded driver files need to be placed to proper directory under linux. So, please type following commands to change directory, move downloaded source files, unpack the source files and change into directory. (NOTE: This step assumes you downloaded the driver file to your home directory.)

cd /usr/src
mv ~/spca5xx-220060501.orig.tar.gz .
tar xfvz spca5xx-20060501.orig.tar.gz
cd spca5xx- 20060501

i try to move the file, which is in /home/jon directory and it gives me:

root@jon-desktop:/usr/src# mv ~/gspcav1-20070110.tar.gz.
mv: missing destination file operand after `/home/jon/gspcav1-20070110.tar.gz.'
Try `mv --help' for more information.
 

help

---

### Post by sdgreen on 2007-03-25
Is there some sort of automated script for all this?

---

### Post by noah_parkcity on 2007-03-25
Thank you cblanquer !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I've spent many hours this weekend trying to get a 

Logictech QuickCam Chat working (29 bucks at chumpusa)

I've read and tried so many methods AND YOURS WORKS!!!!!!!!!!!

Thank you again. Due to my lack of knowledge, it is people like YOU that are helping me 

stay away from winblows (I hear its like a 12-step program)

I can't believe it freakin' works!  If this n00b can do it, then so can

almost ANYBODY that wants to get a webcam up and running in Ubuntu 6.10

Good Luck!

---

### Post by cblanquer on 2007-03-27
type a SPACE between the fikename and the last dot.
The dot "." means "here", you write you want to move your file onto the directory you are located "usr/src".

---

### Post by cblanquer on 2007-03-27
Not from my side.
I have tried Automatix2 but it did install the old driver and my webcam did not work.
Maybe you want to propose one ?   :-)

---

### Post by binselam on 2007-04-09
Hi,
I have been away. Sorry for replying late.  Just in case, if you have not found a solution yet:
**`/home/jon/gspcav1-20070110.tar.gz.'**

there must be a space between the letter z and last period.
**mv  ~/gspcav1-20070110.tar.gz .**

---

### Post by swejuggalo on 2007-04-26
Anyone tried gspcav1-20070426 ? Got the gspcav1-20070110 working...

/usr/src/gspcav1-20070426/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/gspcav1-20070426/gspca_core.c:2630: error: void value not ignored as it ought to be
/usr/src/gspcav1-20070426/gspca_core.c:2632: error: void value not ignored as it ought to be
/usr/src/gspcav1-20070426/gspca_core.c:2634: error: void value not ignored as it ought to be
make[2]: *** [/usr/src/gspcav1-20070426/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/gspcav1-20070426] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [default] Error 2

---

### Post by binselam on 2007-04-27
Yes, I have tried and got it working.


First prepare and eliminate the former driver( if you have installed):

Quote:
sudo make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*  

Then set and load the new one:

Quote:
sudo make install
sudo modprobe gspca

---

### Post by hazelkid on 2007-04-28
I am trying to compile the latest gspcav1 driver without any success...
>   export CC=gcc-4.1; sudo make

make -C /lib/modules/`uname -r`/build SUBDIRS=/home/hazelkid/Desktop/gspcav1-20070426 CC=gcc-4.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/hazelkid/Desktop/gspcav1-20070426/gspca_core.o
/home/hazelkid/Desktop/gspcav1-20070426/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/hazelkid/Desktop/gspcav1-20070426/gspca_core.c:2630: error: void value not ignored as it ought to be
/home/hazelkid/Desktop/gspcav1-20070426/gspca_core.c:2632: error: void value not ignored as it ought to be
/home/hazelkid/Desktop/gspcav1-20070426/gspca_core.c:2634: error: void value not ignored as it ought to be
make[2]: *** [/home/hazelkid/Desktop/gspcav1-20070426/gspca_core.o] Error 1
make[1]: *** [_module_/home/hazelkid/Desktop/gspcav1-20070426] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [default] Error 2



---

### Post by nite_man on 2007-05-01
Hi,

I have the same problem when I try to build latest driver - gspcav1-20070426. any Idea why?

Thanks in advance

---
Michael

---

### Post by binselam on 2007-05-02
hi Hazelkid,
looks like you try to compile files in you Desktop folder. Please make sure you are  in locatin with super user previlages.
/usr/src/gspcav1-20070426/

I am listing the only diffrences from the my first post in compiling process ( if you installed the older version.).

First prepare and eliminate the former driver( if you have installed):

Quote:
sudo make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx* 

Then set and load the new one:

Quote:
sudo make install
sudo modprobe gspca

---

### Post by DirtDawg on 2007-05-04
> **hazelkid said:**
> I am trying to compile the latest gspcav1 driver without any success...

I get identical errors trying to compile ('make') gspcav1-20070426 on Dapper.

---

### Post by cblanquer on 2007-05-04
So after /.04 instalaltion everything went fine from the beginning: my Logitech Quickcam webcam was running without any action. I was thinking even to delete my former posts in this thread.
Then I had to install DVB drivers for my TV card Hauppauge 1300, this process got successful without any major issue.
However I then discovered that my webcam driver disappeared.
So I went back to the posts here and repeated the steps with the recent, new driver gspcav1-20070426.
My former installaitons wre gspcav1-20070111 on 6.10 and 6.10-64bits, all successful.

Now the issues:
> FATAL: Error inserting gspca (/lib/modules/2.6.20-15-generic/kernel/ubuntu/media/gspcav1/gspca.ko): Unknown symbol in module, or unknown parameter (see dmesg)


My dmesg extract is:
> [   40.478358] cx2388x v4l2 driver version 0.0.6 loaded
[   40.478409] ACPI: PCI Interrupt 0000:03:0c.0[A] -> GSI 20 (level, low) -> IRQ 21
[   40.478418] cx88[0]/0: found at 0000:03:0c.0, rev: 5, irq: 21, latency: 64, mmio: 0xfb000000
[   40.498932] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   40.501937] tuner 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   40.504914] tuner 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   40.506083] tuner 0-0063: chip found @ 0xc6 (cx88[0])
[   40.531507] wm8775 0-001b: chip found @ 0x36 (cx88[0])
[   40.539553] cx88[0]/0: registered device video0 [v4l2]
[   40.539579] cx88[0]/0: registered device vbi0
[   40.539605] cx88[0]/0: registered device radio0
[   40.618156] gspca: disagrees about version of symbol video_devdata
[   40.618160] gspca: Unknown symbol video_devdata
[   40.618314] gspca: disagrees about version of symbol video_unregister_device
[   40.618316] gspca: Unknown symbol video_unregister_device
[   40.618377] gspca: disagrees about version of symbol video_device_alloc
[   40.618379] gspca: Unknown symbol video_device_alloc
[   40.618403] gspca: disagrees about version of symbol video_register_device
[   40.618405] gspca: Unknown symbol video_register_device
[   40.618533] gspca: disagrees about version of symbol 


I would expect the webcam to become /dev/video1 as the TV card copes /dev/video0.
A 2nd compilation has driven me to the same results.

I have not found a solution yet. Does anybody have the same problem ?

---

### Post by DirtDawg on 2007-05-05
Okay, got this to work on Dapper with a Logitech Quickcam Communicate STX, by using an older driver, It was gspcav1-20060925.tar.gz (found [here]("http://mxhaard.free.fr/spca50x/Download/oldrelease/") as of this writing), then followed the HOWTO instructions normally.

Try using this driver if you are experiencing the errors described above.

---

### Post by swejuggalo on 2007-05-10
New driver, gspcav1-20070508 , works fine (on Ubuntu 7.04) unlike the previous driver gspcav1-20070426.

cd "the folder the tar.gz" exist
sudo mv gspcav1-20070508.tar.gz /usr/src
cd /usr/src
sudo tar xfvz gspcav1-20070508.tar.gz
cd gspcav1-20070508
export CC=gcc-4.1
sudo ln -f -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build  (not sure if I really need to force ln -s but it can't hurt anyone ;) )
make
sudo modprobe -r gspca
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/gspca*
sudo make install
sudo modprobe gspca

---

### Post by djtob on 2007-05-18
> **swejuggalo said:**
> New driver, gspcav1-20070508 , works fine (on Ubuntu 7.04) unlike the previous driver gspcav1-20070426.

cd "the folder the tar.gz" exist
sudo mv gspcav1-20070508.tar.gz /usr/src
cd /usr/src
sudo tar xfvz gspcav1-20070508.tar.gz
cd gspcav1-20070508
export CC=gcc-4.1
sudo ln -f -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build  (not sure if I really need to force ln -s but it can't hurt anyone ;) )
make
sudo modprobe -r gspca
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/gspca*
sudo make install
sudo modprobe gspca

I did this manual and all is ready, I see there is gspca.ko in usb/media folder but with modprobe gspca will show nothing in terminal and Logitech QC pro 4000 webcam's green light is still showing. What's wrong?:(

EDIT: Kernel is 2.6.17-11-generic and I'm using Ubuntu 6.10 Edgy Eft.
I don't want use spca5xx drivers because it did crash my Ubuntu graphic Desktop three time,
everytime when I restart my computer and everytime I must re-setup my graphic desktop.

---

### Post by swejuggalo on 2007-05-20
maybe not the answer you wanted...but [http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/) is a good driver too. Used it when I had a QC pro 4000 cam. Works good mostly, but slow with aMsn.

---

### Post by mssever on 2007-05-28
Compiling the spca5xx driver manually is for the birds. [These instructions]("http://scottabbey.org/node/12") are much simpler and don't require you to mess with your kernel or any other such stuff. Just make sure you have the Universe repository enabled.

---

### Post by bob365 on 2007-09-03
Will this method also work on Ubuntu 7.04?

---

### Post by binselam on 2007-09-04
Hi Bob,
Yes, It should work. But, make sure you download latest drivers.

New driver, gspcav1-20070508 , works fine (on Ubuntu 7.04) unlike the previous driver gspcav1-20070426.

cd "the folder the tar.gz" exist
sudo mv gspcav1-20070508.tar.gz /usr/src
cd /usr/src
sudo tar xfvz gspcav1-20070508.tar.gz
cd gspcav1-20070508
export CC=gcc-4.1
sudo ln -f -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build (not sure if I really need to force ln -s but it can't hurt anyone  )
make
sudo modprobe -r gspca
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/gspca*
sudo make install
sudo modprobe gspca

---

### Post by parvinder on 2007-09-09
Hi,

I see that many were able to install the logitech camera... sorry for the long message but it is the output of the commands I tried from this post....

I downloaded spca5xx-v4l1goodbye.tar.gz and followed the instructions to download dependecy etc and set the gcc version.. everything went great..

But, When I run make it gives me lot of warnings and terminates.

  CC [M]  /home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:39:26: error: linux/config.h: No such file or directory
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca50x_init_isoc’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:1623: warning: assignment from incompatible pointer type
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_open’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2394: warning: implicit declaration of function ‘video_devdata’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2394: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2399: warning: implicit declaration of function ‘video_get_drvdata’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2399: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_close’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2489: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_do_ioctl’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2549: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_ioctl’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3093: warning: implicit declaration of function ‘video_usercopy’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_read’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3112: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_mmap’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3211: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: At top level:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3263: error: variable ‘spca50x_template’ has initializer but incomplete type
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: error: unknown field ‘owner’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: error: unknown field ‘name’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: error: unknown field ‘type’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: error: unknown field ‘hardware’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: error: unknown field ‘fops’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: error: unknown field ‘release’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: error: ‘video_device_release’ undeclared here (not in a function)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: error: unknown field ‘minor’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘cd_to_spca50x’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3340: warning: implicit declaration of function ‘to_video_device’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3340: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3341: warning: return makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca50x_create_sysfs’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3450: warning: implicit declaration of function ‘video_device_create_file’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_probe’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5509: warning: implicit declaration of function ‘video_device_alloc’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5509: warning: assignment makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5514: error: dereferencing pointer to incomplete type
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5516: warning: implicit declaration of function ‘video_set_drvdata’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: warning: implicit declaration of function ‘video_register_device’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: (Each undeclared identifier is reported only once
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: for each function it appears in.)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5550: error: dereferencing pointer to incomplete type
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5551: warning: implicit declaration of function ‘video_device_release’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5553: warning: implicit declaration of function ‘video_unregister_device’
make[2]: *** [/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o] Error 1
make[1]: *** [_module_/home/localuser/Downloads/spca5xx-v4l1goodbye] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2


Whne I run modprobe -r spca5xx it gives
root@my-laptop:~/Downloads/spca5xx-v4l1goodbye# sudo modprobe -r spca5xx
FATAL: Module spca5xx not found.

dmesg gives the output as follows...

[   19.832000] usbcore: registered new interface driver gspca
[   19.832000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   19.992000] NET: Registered protocol family 17
[   20.004000] usbcore: registered new interface driver snd-usb-audio


I don't think the Logitech QC for notebook that comes with mic is installed???? any help??? :confused:

---

### Post by binselam on 2007-09-11
What versio of ubuntu you are using?
If you are using 7.04, you should install gspcav1. For that there is another set of instructions toward the end
--------------------------------------------------------------------------------

New driver, gspcav1-20070508 , works fine (on Ubuntu 7.04) unlike the previous driver gspcav1-20070426.

following instruction is listed by swejuggalo :
cd "the folder the tar.gz" exist
sudo mv gspcav1-20070508.tar.gz /usr/src
cd /usr/src
sudo tar xfvz gspcav1-20070508.tar.gz
cd gspcav1-20070508
export CC=gcc-4.1
sudo ln -f -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build (not sure if I really need to force ln -s but it can't hurt anyone  )
make
sudo modprobe -r gspca
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/gspca*
sudo make install
sudo modprobe gspca



 Otherwise, 
make sure you are uncomressed and installed the files into 
cd /usr/src
(after downlading them into your local user space).

---

### Post by jpgeerets on 2007-09-16
hi folks,

im trying to install my webcam too to ubuntu-server 704.
but it still doesnt work.
it is a logitech webcam. 
im trying to install it remote by ssh -X

finaly i want to use apache (already installed and in use) or another http-server to view cam cam like a stream.
i hope someone can give me some advice...

thanks in advanced...


Jean-Paul

---

### Post by FooAtari on 2007-11-08
Hi,

I'm using a Logitech Communicate STX.  The first thing I tried was Camorama.  It worked but the colours were all messed up, light shades of blues and oranges. I saw the same problem in Kopete.

So I tried using an install guide that was very basic but think I messed it up.

I then installed Camstream and it was great, good colours and VGA resolution available.  However in Camorama and Kopete the colours are still all messed up.

I tried this guide using the gscav1 driver but no difference.

I have no idea if the microphone is working but my first priority is the video, can someone help with the odd problem.  Obviously something is working somewhere as Camstream looks fine.

---

### Post by bdgraue on 2007-11-09
hello, i have a webcam, that worked out of the box in feisty, now with gutsy i have a problem and no one in the irc can help me out.

in feisty wengophone told me something about gspca in gutsy sn9c1xx.
dmesg tell me in gutsy that gspca and sn9c102 modules are loaded.
i have really no idea what to do to get the webcam running, and i don't know, why i have to do something, cause it work out of the box in feisty, also in feisty-live-cd.

i will be really happy if someone can help me, thanks

bdgraue

---

### Post by irv on 2007-11-10
> **bdgraue said:**
> hello, i have a webcam, that worked out of the box in feisty, now with gutsy i have a problem and no one in the irc can help me out.

in feisty wengophone told me something about gspca in gutsy sn9c1xx.
dmesg tell me in gutsy that gspca and sn9c102 modules are loaded.
i have really no idea what to do to get the webcam running, and i don't know, why i have to do something, cause it work out of the box in feisty, also in feisty-live-cd.

i will be really happy if someone can help me, thanks

bdgraue

I agree with your post 100%. I wish someone could really help with this problem. I have everything working (all my hardware) except my Quick Cam.This is not a good mark for 7.10.

---

### Post by FooAtari on 2007-11-10
yeah same here, everything is good except the cam.  Im really not sure where Im going wrong.

---

### Post by jadedjay on 2007-11-14
Not sure if this will help you guys but I use to have a bit of a problem setting up my Logitech camera when I was on Dapper, Feisty and Edgy.  So I followed this thread to get it up a running.  

Then I moved to Gutsy and simply followed this website. 
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)  and used Easycam and now my camera is working fine.  
The only other thing that I installed at the time was the new Skype beta 2.0 for linux.  

Maybe it might work for you.

---

### Post by irv on 2007-11-14
> **jadedjay said:**
> Not sure if this will help you guys but I use to have a bit of a problem setting up my Logitech camera when I was on Dapper, Feisty and Edgy.  So I followed this thread to get it up a running.  

Then I moved to Gutsy and simply followed this website. 
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)  and used Easycam and now my camera is working fine.  
The only other thing that I installed at the time was the new Skype beta 2.0 for linux.  

Maybe it might work for you.

Thanks for the tip, but this did not work either. I tried easycam 1 & 2 and neither worked.
Thanks again for the tip.

---

### Post by binselam on 2007-11-14
Hi IRV,

I have questions to you.

1) what is the model and maker of your web cam?

2) do you get an error message? (if you do get an error message, what is it?

I will try to help you, if I can.

Please try to be more specific.

Thanks

---

### Post by irv on 2007-11-15
> **binselam said:**
> Hi IRV,

I have questions to you.

1) what is the model and maker of your web cam?

2) do you get an error message? (if you do get an error message, what is it?

I will try to help you, if I can.

Please try to be more specific.

Thanks

Thanks for the offer to help.
I will have to wait until I get home to get this information for you. I am on the road and won't be home until Nov. 26th. Will dig it up and post it then.
Thanks again
Irv

---

### Post by mimiko on 2007-11-16
Excellent, I got it to work, just had to change to  gspca wherever it said spca...Thanks so much!

For reference, I have logitech quickcam deluxe for notebooks and kubuntu gutsy gibbon.


> **cblanquer said:**
> Hi,

As I am fully reinstalling my system ](*,) , it is the webcam turn so I shall try to document whatever I do in order to help.
But I am basically cloning the instructions quite well detailed on the first post.
I hope this helps. :) 
======

**STEP 1**
Not necessary for me, as I knew already I would need it (ekiga/gnomemeeting does not find it as a device). 

**STEP 2**
I downloaded the new driver from the site [http://mxhaard.free.fr/](http://mxhaard.free.fr/). The file name used that time is: gspcav1-20070110.tar.gz
New versions will have different names. 
I copied it to a directory in my home folder that I called ~/lib/webcam.driver.

**STEP 3**
Skipped it, I preferred to use "sudo".
I opened a terminal (by the way I reduce the size and set it to "always on top").

**STEP 4**
Similar to former instructions - please follow them:



or 
Depending on which is available. Remember this for a later instruction.
As my system was fresh installed, I did get only the compile tools.

**STEP 5**
Here comes the fun! Instead of moving I just copy to avoid a reload next time...


Please do not forget the space-dot at the end in order to properly copy your file.

Now next actions:


**STEP 6**

If gcc-4.1 was not available :

**STEP 7**


**STEP 8**
First prepare and eliminate the former driver:

Then set and load the new one:


**THE END**
Type

And see results at the bottom (specs will depend on your H/W)


Now it seems ready. 
Actually I had to review and redo as I made first a mistake building and then calling the new module (gspcav1 instead of gspca ].

Test with ekiga is SUCCESSFUL ! :)  Now waiting for a linux new Skype version (my contacts use all Skype). Good luck !

See 3 screenshots...

=============================================
Updates since I installed Ubuntu 7.04.
My TV card DVB-T features were not enabled by default so that I reinstalled the TV drivers for DVB.
Since then the card works ok (by means of Kaffeine I have access to the TV digital terrestial channels) but the webcam is driver is BROKEN.
I have tried the reinstall for several of the new versions of the webcam drivers, unsuccessful. There is a conflict somewhere that does not allow the webcam device to be created (I would expect a "video2" device).

Here is the end of dmesg after the last compilation:
[11861.956000] gspca: disagrees about version of symbol video_devdata
[11861.956000] gspca: Unknown symbol video_devdata
[11861.956000] gspca: disagrees about version of symbol video_unregister_device
[11861.956000] gspca: Unknown symbol video_unregister_device
[11861.956000] gspca: disagrees about version of symbol video_device_alloc
[11861.956000] gspca: Unknown symbol video_device_alloc
[11861.956000] gspca: disagrees about version of symbol video_register_device
[11861.956000] gspca: Unknown symbol video_register_device
[11861.956000] gspca: disagrees about version of symbol video_device_release
[11861.956000] gspca: Unknown symbol video_device_release

---

### Post by chapterthree on 2007-12-24
> **OakRand said:**
> I had the same problem. Check out the following page:[http://www.myl.ro/forum/index.php?showtopic=2185](http://www.myl.ro/forum/index.php?showtopic=2185)

Here are the necessary instructions. Following the guide in the first post of this thread, then:

1. Install Video4Linux if you haven't done so already
> sudo apt-get install libpt-plugins-v4l

2. Open xorg.conf 
> sudo gedit /etc/X11/xorg.conf

3. Add the following to 'Section "Module'
Load "v4l"

4. Make an init script that loads the webcam:
> sudo touch /etc/init.d/webcam
> sudo chmod +x /etc/init.d/webcam
> sudo gedit /etc/init.d/webcam

and add the following two lines:

!#/bin/sh
for i in 0 1 ;do if [ ! -f /dev/video$i ]; then echo "Creating /dev/video$i" && mknod /dev/video$i c 81 $i && chown :adm /dev/video$i && chmod 660 /dev/video$i; else echo "/dev/video$i already exists";fi;done

5. Update
> sudo update-rc.d webcam defaults

6. Reboot

For anybody using these instructions there is a typo in the webcam startup script above (the interperter specification line should be #!/bin/sh and not !#/bin/sh).  So for cut-and-paste clarity, it should be:

```
#!/bin/sh
for i in 0 1 ;do if [ ! -f /dev/video$i ]; then echo "Creating /dev/video$i" && mknod /dev/video$i c 81 $i && chown :adm /dev/video$i && chmod 660 /dev/video$i; else echo "/dev/video$i already exists";fi;done
```

They key component of the script is that it sets the group to adm, which your user should be a member of.  For some reason the system sets up the /dev/video# ownership to root:video with 660 permissions.

---

### Post by cwhisperer on 2007-12-27
works like a charm :)))

---

### Post by Ni85 on 2008-01-22
Hey everybody.
I've followed the how-to and didn't get any error and with the dmesg command I got back something similar to what was shown in the first post.
Still I can't make it work.. I have another integrated camera on my laptop and when I launch Camorama it seems it's trying to use that one (which doesn't work) instead of my Logitech QuickCam Connect: the led on the integrated one turns on while I get this error

Could not connect to video device (/dev/video0).
Please check connection.

Nothing happens to the Logitech cam (led doesn't even turn on).
How could i fix this?
In case it would help, this is what I get after a lsusb command:

```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 174f:5a35  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 046d:08d9 Logitech, Inc. QuickCam IM/Connect
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

thanks in advance

---

### Post by binselam on 2008-02-03
Hi,
Your Logitech Cam is recognized as Device 004 on your system.
Easy way:
So, remove all devide intalletions or unplug other camera devices. Then,  uninstall previous intallation. Nec step connect the logitec as only cam device, and proceed with installation.


If you are good with unix commands:
You have to changes your video device 0 assigment to Device 004.

Bus 003 Device 004: ID 046d:08d9 Logitech, Inc. QuickCam IM/Connect

---

### Post by Carbon Tiger on 2008-02-09
Weird problem here. I just got a Quickcam Deluxe for Notebooks and Camorama is the only thing it won't work on it works on skype and I can record sound of it with the sound recorder easily. 

Anyone know an easy way to capture video ?

EDIT: Cheese seems to work well for just pulling up and recording a feed so nvm I guess.

---

### Post by pjbgravely on 2008-03-07
> **Ni85 said:**
> Hey everybody.
I've followed the how-to and didn't get any error and with the dmesg command I got back something similar to what was shown in the first post.
Still I can't make it work.. I have another integrated camera on my laptop and when I launch Camorama it seems it's trying to use that one (which doesn't work) instead of my Logitech QuickCam Connect: the led on the integrated one turns on while I get this error

Could not connect to video device (/dev/video0).
Please check connection.

Nothing happens to the Logitech cam (led doesn't even turn on).
How could i fix this?


Simply open a terminal and type:
```

camorama --device=/dev/video1


```

Paul

---

