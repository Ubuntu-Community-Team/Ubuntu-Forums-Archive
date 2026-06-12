---
title: "release of Catalyst 11.3 - 11.4, gpu harnessing, linux benefit"
date: 2011-04-08
forum: Multimedia Software
---

### Post by Claus7 on 2011-04-08
Hello,

I'm using ubuntu maverick 10.10 for the time being, while having installed the proprietary fglrx driver provided from canonical and the repositories.

I would like to harness the gpu power of my graphics card which is an ati 5670. Has anyone installed the latest driver for maverick and experienced any improvement in performance?

It is supposed that the latest catalyst drivers are a remarkable improvement both in games support and opencl support. I'm interested on the latter so any feedback would be greatly appreciated, as a new installation would require some effort.

Regards!

---

### Post by Yellow Pasque on 2011-04-08
I'd suggest you try it. If you know how to copy/paste commands and boot to recovery mode (hold down Shift after BIOS screen), then you can recover to your existing driver even if you can't start the Xserver.
Remove the Ubuntu version first: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

Get new driver and install it: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

If it doesn't work out and you get stuck in a terminal, just keep the removal commands handy, and then install the repo version:
```
sudo install fglrx
```

---

### Post by Claus7 on 2011-04-10
Hello,

thank you for your reply. From here:
[http://drpaneas.com/?p=66](http://drpaneas.com/?p=66)

Dr. Paneas seems that he has accomplished this with remarkable boost performance on games, whereas from here:
[http://developer.amd.com/gpu/AMDAPPSDK/Pages/default.aspx](http://developer.amd.com/gpu/AMDAPPSDK/Pages/default.aspx)

it states that from catalyst 11.3 and on the opencl drivers are included in the gpu drivers! 

So great improvement so far. The problem is that every time a new kernel of ubuntu arrives the drivers have to be installed anew, and my system is the most stable I have for a long long time...
Also there it not a sound way of installing the drivers on top of each other. Every time there has to be a fresh install...

I'll think about it and thanks for the links.

Regards!

---

### Post by Yellow Pasque on 2011-04-10
> The problem is that every time a new kernel of ubuntu arrives the drivers have to be installed anew.
That's why you follow the instructions and install the driver using dkms ;)

> Also there it not a sound way of installing the drivers on top of each other. Every time there has to be a fresh install...
If you install the driver as recommended, removal can be done with one command and a fresh install can be done with a handful of commands. You can probably do it quicker than the Windows-style point/click, download and run .exe method. Also, I've seen plenty of complaints where Windows graphics drivers don't install properly on top of each other.

---

### Post by Claus7 on 2011-04-10
Hello,

installation proceeded as normal and now I'm back again. I hope that I will be able to harness this opencl support with these drivers via ubuntu. One step at a time though.

Any feedback will be welcome!

Just to point out that during recovery mode (from BIOS keeping the shift button) I had to switch to my profile in order to remove the old fglrx driver and install the new one. Also, when it removed the old one, it mentioned something about some directories that they are not empty, so they will not be removed.
In the end the ccc reported v. 11.3. So, while everything tested up to now are ok, the installation should be ok too.

Regards!

---

### Post by alphacrucis2 on 2011-04-10
> **Claus7 said:**
> Hello,

thank you for your reply. From here:
[http://drpaneas.com/?p=66](http://drpaneas.com/?p=66)

Dr. Paneas seems that he has accomplished this with remarkable boost performance on games, whereas from here:
[http://developer.amd.com/gpu/AMDAPPSDK/Pages/default.aspx](http://developer.amd.com/gpu/AMDAPPSDK/Pages/default.aspx)

it states that from catalyst 11.3 and on the opencl drivers are included in the gpu drivers! 

So great improvement so far. The problem is that every time a new kernel of ubuntu arrives the drivers have to be installed anew, and my system is the most stable I have for a long long time...
Also there it not a sound way of installing the drivers on top of each other. Every time there has to be a fresh install...

I'll think about it and thanks for the links.

Regards!

I install catalyst using the buildpkg method. This creates a set of deb files that you install using dpkg. I always keep the previous set of deb files so I can roll back if AMD release a lemon. The steps I go through are:

1. Purge existing fglrx using apt-get and backup current Catalyst deb files.
2. Run the new AMD Catalyst installer using the buildpkg option. (This always gave an error if I didn't purge the old fglrx first - probably a bug).
3. Install the newly created deb files using dpkg. Do a sudo aticonfig --initial -f and reboot
4. If no go then boot to command line and purge fglrx as in step 1. Reinstall the backup up deb files that worked. (I haven't had to do this for quite a while - the Catalyst releases have been kind to me)

---

### Post by Claus7 on 2011-04-10
Hello,

thank you all for the responses! I had second thoughts of installing the drivers from amd's website because my system with canonical's fglrx drivers was working like a charm. The problem was that I had to install the opencl drivers, which are supposed to be installed side by side with Catalyst 11.3.

The thing is that I'm trying to see what I can get with that to no avail though.

[LIST]ratgpu does not seem to do the job
[*]vainfo produces errors like others facing here in the forums and
[*]python-pygpu seems to be working only with nvidia cards...
[*]also there is a cups gpu program, yet only available for windows users.
[/LIST]
Thank you for any suggestion up to now. Any suggestion for harnessing gpu in ubuntu with ati drivers will be more than welcome!

Regards!

---

### Post by Yellow Pasque on 2011-04-10
Not sure about the other stuff, but:
> vainfo produces errors like others facing here in the forums
[https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks) and get latest xvba here: [http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)

---

### Post by Claus7 on 2011-04-10
Hello,

> **Temüjin said:**
> Not sure about the other stuff, but:

[https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks) and get latest xvba here: [http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)

thanks for the reply once again. I have to admit that I came across your answer. The point is that I do not want to use vlc player modified. Am I right on this? Doesn't this allow vlc player to work with opencl support? Should I use this version of vlc in order to be able to see some info about opencl and my gpu power?

Regards!

---

### Post by Yellow Pasque on 2011-04-10
The point of the PPA is to get video decode acceleration in VLC. VLC is not modified, but just rebuilt with appropriate libva-dev. I'm not sure how opencl is involved in that.

---

### Post by Claus7 on 2011-04-10
Hello,

it seems from here:
[http://microelectronics.cbronline.com/news/amd-launches-catalyst-113-114-preview-video-drivers-300311](http://microelectronics.cbronline.com/news/amd-launches-catalyst-113-114-preview-video-drivers-300311)

that opencl is enabled by default only for windows users...
*Temüjin* I'm interested in gpu harnessing and that's why I wanted to install vainfo, so as to have a clearer picture of my gpu, and not just to accelerate vlc.

Thanks for the info,
Regards!

---

### Post by Yellow Pasque on 2011-04-11
I still don't know what vainfo/VA-API has to do with OpenCL. vainfo only reports what video formats are available for acceleration.
See this page to get started with OpenCL: [http://developer.amd.com/gpu/AMDAPPSDK/downloads/Pages/default.aspx](http://developer.amd.com/gpu/AMDAPPSDK/downloads/Pages/default.aspx)

---

### Post by Claus7 on 2011-04-12
Hello,

I thought that vainfo was something like this:
[http://www.techpowerup.com/gpuz/](http://www.techpowerup.com/gpuz/)

maybe I misunderstood. The link you provided me, along with some other links show how someone can compile opencl (sdk) on someone's pc. I did make the compilation (which I wanted to avoid), yet I do not know if everything went ok...

What I want to do:
1)find how many gpu power my card has.
2)how I can run programs on my card.

I will report more, yet I'm not on my pc right now.
Till next notice,
Regards!

---

### Post by azwar on 2011-04-13
> **Temüjin said:**
> I still don't know what vainfo/VA-API has to do with OpenCL. vainfo only reports what video formats are available for acceleration.
See this page to get started with OpenCL: [http://developer.amd.com/gpu/AMDAPPSDK/downloads/Pages/default.aspx](http://developer.amd.com/gpu/AMDAPPSDK/downloads/Pages/default.aspx)

VA-API give you GPU acceleration on video processing i.e video decoding, video encoding, blending and rendering.

OpenCL give any application an access to GPU other than CPU beyond graphics application. Traditionally, all application was handled by the CPU. With OpenCL, you get parallel computation in application from both CPU & GPU. In AMD/Ati Linux, OpenCL come with ATI Stream (now called AMD APP SDK).

I've installed the ATI Stream to enable the OpenCL in my Lucid. But up to now, there is no application that I used that take advantage of OpenCL.

But the main reason I still stuck with lucid Lynx, because VA-API is not work for me on Maverick.

---

### Post by Claus7 on 2011-04-22
Hello,

first of, I would like to thank all the people that posted up to now and gave a hand.

Now I'll try to post what I got by exploring the issue a little more.

What we want to do:
harness our GPU. By that I mean to run programs not on **C**PU only, yet on **G**PU, meaning the graphics card of our computer.

In order to take advantage of that chip, we have to install 1) the drivers of our graphics card and 2) an APP interface which will enable us to run programs on our GPU.

For ubuntu maverick 10.10 64 bit and an ATI card someone has to take the aforementioned steps one by one, as opposed (up to now) to windows users. Also, it seems not possible to harness such a feature by only using the open source drivers or the proprietary ones provided by Canonical (yet I have not made any tests on that).
As a result you have to go to amd's website and choose the driver of your card.

In general you have to:

[LIST]
[*]Verify the system has an OPENCL-capable GPU
[*]Verify the system has a supported version of Linux (on maverick you do not have to worry about that as it has already 2.6xx kernels).
[*]Download and install the ATI driver of your card from amd's website.
[*]Download and install the ATI GPU Computing SDK (APP)
[*]Build the tutorial programs
[/LIST]

**Verify the system has an OPENCL-capable GPU**
Go here:
[http://developer.amd.com/gpu/AMDAPPSDK/pages/DriverCompatibility.aspx](http://developer.amd.com/gpu/AMDAPPSDK/pages/DriverCompatibility.aspx)
and check the compatible cards.

**Verify the system has a supported version of Linux**
In the above link, even though there you will find only Lucid as an ubuntu supported operating system, maverick is supposed to do the job as well. 

**Download and install the ATI driver of your card from amd's website.**
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

don't forget to choose between 64 bit and 32 bit, that will play also a role later.

**Download and install the ATI GPU Computing SDK**

The most important part is here. In order to accomplish that you have either to download the package from ati or to go here:
[http://forums.amd.com/](http://forums.amd.com/)

and then to:
AMD Developer Forums->OpenCL->Ubuntu package with ATI Stream SDK

the magnificent guy **noo**, has pre-compiled the necessary package either for 32 or 64 bit boxes in his very first post which I quote here:

> i create deb package with ATi OpenCL libs. you can download it here

amd-app 2.4 i386 and amd64 need to run OpenCL aplication

amd-app-dev 2.4 both header files

For a 64 machine you need to click and install the amd64 package along with the package under the word both. You need these **2** packages for the installation to work!

**Build the tutorial programs**
You can find many tutorial programs on the net. Here I just provide a sample code (named test.c), so as to make a test for your installation:

```
    #include "CL/cl.h"

    int main(int argc, char **argv){
    cl_platform_id test;
    cl_uint num;
    cl_uint ok = 1;
    clGetPlatformIDs(ok, &test, &num);

    return 0;
    }
```

Just type:
```
gcc-4.5 test.c -o prog -lOpenCL
./prog
```

if you get something like this:
> test.c:1:23: fatal error: CL/cl.h: No such file or directory
compilation terminated.

then your installation is wrong and either you have forgotten to install all the packages or the -manual- installation of APP did not go well.


Now, concerning the part of visualising your GPU power, the ratgpu program might work for you. I have installed it on my box, yet while doing so via Software Manager, it keeps saying on the upper right corner to install it again instead of saying reinstall. It recognised half of my GPU power, yet is indicative of weather you have installed correctly the opencl packages or not.

Regards!

---

