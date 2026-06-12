---
title: "Opening Blender"
date: 2013-12-17
forum: Multimedia Software
---

### Post by rolfUser on 2013-12-17
I've had Ubuntu for almost a year now.  I picked up some interest in 3D model design and since I'm using Ubuntu 12.04 LTS, I thought I could just download an open source program that does just that.  On google, I learned about programs like **Blender** and **K-3D**.  Alright, so it sounded easy enough to get started.

After downloading and installing the programs from Ubuntu Software Center, they just don't open.   I don't understand.  
There has to be some configuring to help get the programs to open, right?

Where would I start, b/c I wouldn't know.

---

### Post by monkeybrain20122 on 2013-12-17
Open the terminal and type "blender" (without quotes)
and see what error messages it outputs.

Do same for k3d (if the command k3d says not found try k-3d)

Anyway, instead of getting a very outdated version from the Software Centre with possibly messed up dependencies, you are better off downloading the latest blender from its own site. [http://www.blender.org/download/](http://www.blender.org/download/) 

Save the download to your home, extract, open the extracted folder and click blender to start, it doesn't require installation.
If you want to make a launcher icon, see this thread.[http://ubuntuforums.org/showthread.php?t=2183179](http://ubuntuforums.org/showthread.php?t=2183179)

---

### Post by rolfUser on 2013-12-17
Hold on. Here's what came up:

[FONT=courier new]X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  32
  Current serial number in output stream:  32
Segmentation fault (core dumped)[/FONT]

I want to at least know what this all means.

---

### Post by monkeybrain20122 on 2013-12-17
Do you have an AMD graphic card? I just did a search on google and these came up
askubuntu.com/questions/175744/x-error-of-failed-request-badrequest-invalid-request-code-or-no-such-operation
[https://coderwall.com/p/hkm3oa](https://coderwall.com/p/hkm3oa)

---

### Post by rolfUser on 2013-12-17
Do I have an AMD graphic card?
I'm not sure how to check. But I searched here:   System Settings > Hardware > Additional Drivers 
After some time loading, the text, **No proprietary drivers in use on this system**, is outputed on a dialog box

I searched online for another clue and typed: [FONT=courier new]lspci | grep "VGA"[/FONT]   into the terminal.
This was outputted:
[FONT=courier new]00:02.0 [COLOR=#ff0000]VGA[/COLOR] compatible controller: Intel Corporation 2nd Generation Core Process
or Family Integrated Graphics Controller (rev 09)[/FONT]

Does this help?

---

### Post by monkeybrain20122 on 2013-12-17
You don't have an ATI/AMD card so those solutions don't work.
Take a look at
[http://ubuntuforums.org/showthread.php?t=2169099](http://ubuntuforums.org/showthread.php?t=2169099)
[http://ubuntuforums.org/showthread.php?t=2107004](http://ubuntuforums.org/showthread.php?t=2107004)

Can you do
```
sudo apt-get install mesa-utils

```
then

```
glxinfo | grep OpenGL
```

Did you download blender from blender.org? Try if that works, just in case it may be a problem with the program.

---

### Post by rolfUser on 2013-12-17
Okay well, I typed in:  

[FONT=courier new]sudo apt-get install mesa-utils[/FONT]
and got... 
```

[FONT=courier new]Reading package lists... Done
Building dependency tree       
Reading state information... Done
mesa-utils is already the newest version.
The following packages were automatically installed and are no longer required:
  libstlport4.6ldbl thunderbird-globalmenu gir1.2-ubuntuoneui-3.0
  libcmis-0.2-0 libubuntuoneui-3.0-1 linux-headers-3.5.0-23
  linux-headers-3.5.0-23-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]

```


Then typed....

[FONT=courier new]glxinfo | grep OpenGL[/FONT]

and got
```

[FONT=courier new]X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12[/FONT]

```


So now what?

Hold on, I am receiving updates via **Update Manager** with files that start with Qt 4.
[LIST]
[*]Qt 4 SVG module 
[*]Qt 4 XML module 
[*]Qt 4 core module 
[*]et cetera 
[/LIST]
13 updates for 10.6MB
Is this relevant to Blender?

---

### Post by rolfUser on 2013-12-17
Did I download Blender from Blender.org?
No I did not.

---

### Post by rolfUser on 2013-12-18
Blender still will not open.
I ended up trying different things.
I went here:    [http://www.ubuntubuzz.com/2012/04/things-to-do-after-installing-ubuntu.html](http://www.ubuntubuzz.com/2012/04/things-to-do-after-installing-ubuntu.html)
And typed "[FONT=courier new]sudo apt-get install bcmwl-kernel-source[/FONT]" and "[FONT=courier new]sudo apt-get install ubuntu-restricted-extras[/FONT]".
I'm still a novice with Ubuntu, so I have not installed many applications.     On the positive side, Windows fonts like Times New Roman and Verdana can now be processed and used on my system.   Is there something else I should pick up from that site? 

I even tried deleting Blender and downloading it from Blender.org.   I got to putting this down in the terminal: [FONT=courier new]sudo apt-get install nvidia-cuda-toolkit[/FONT]
I got it from:   [http://ubuntuhandbook.org/index.php/2013/11/install-blender-2-69-ppa-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2013/11/install-blender-2-69-ppa-ubuntu-linux-mint/)
thinking that it might help. The program I'm after still does not want to open.

What is wrong with my computer?

---

### Post by monkeybrain20122 on 2013-12-19
Cuda has nothing to do with your problem. It is for gpu programing and works only with Nvidia graphic cards.
bcmwl-kernel source is for certain broadcom wifi card, has nothing to do with graphic card.

What happens with the download from blender.org? Does it open when you go into the extracted folder and click the file 'blender'?

Your outputs suggest that there is something seriously messed up with your graphic driver, but since your card appears to be intel the solutions in those links don't apply (all ATI cards apparently) 

Did you do an OS upgrade, or is it a fresh install?

Can you post the outputs of 
```
lshw -C display
```

---

### Post by rolfUser on 2013-12-19
**What happens with the download from blender.org? Does it open when you  go into the extracted folder and click the file 'blender'?**
I deleted Blender from the Software Center.
From blender.org, I selected USA version, under 32-bit.
Instead of saving the file, I chose to open the file.
Then extracted with Archive Manager without changing the directory.
A folder called "blender-2.69-linux-glibc211-i686" shows up in the Home Folder.
I typed [FONT=lucida console]sudo apt-get install blender-2.69-linux-glibc211-i686[/FONT] into the terminal, but it won't open.
Then I tried [FONT=lucida console]sudo apt-get install blender[/FONT] and that made no difference.



**Did you do an OS upgrade, or is it a fresh install?**
What I did was take my USB drive and had it formatted to boot Ubuntu 12.04 LTS (32-bit version) from the BIOS.
I have it running alongside Windwos XP since I have important files running on both OSs. 


Entering [FONT=courier new]lshw -C display[/FONT] into the terminal outputs:
```

[FONT=courier new]WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.[/FONT]

```

---

### Post by monkeybrain20122 on 2013-12-19
1. The download doesn't require installing (in any case sudo apt-get install is only for installing things from the repository), you just click open the folder ""blender-2.69-linux-glibc211-i686"" and click on the binary (the file called "blender") and it should just start blender.

2. Is it a live usb (creat with unetbootin or similar tool) or did you actually install Ubuntu in your hard drive? Well if it is  a live usb then some operations would not work and it is not up to date. How exactly did you set up your system?

---

### Post by monkeybrain20122 on 2013-12-19
See if this works
[http://ubuntuforums.org/showthread.php?t=1396959](http://ubuntuforums.org/showthread.php?t=1396959)

---

### Post by rolfUser on 2013-12-20
> **monkeybrain20122 said:**
> 1. The download doesn't require installing (in any case sudo apt-get install is only for installing things from the repository), you just click open the folder ""blender-2.69-linux-glibc211-i686"" and click on the binary (the file called "blender") and it should just start blender.

2. Is it a live usb (creat with unetbootin or similar tool) or did you actually install Ubuntu in your hard drive? Well if it is  a live usb then some operations would not work and it is not up to date. How exactly did you set up your system?

As I recall, I went to a site like this one: [http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download)   to format my flash drive some months back.

  I was on Windows XP and my plan was to install Ubuntu 12.04 LTS by booting from the BIOS, using the flash drive, instead of a disc.
That site, I think, is the one I used to format my USB drive b/c I remember the symbol at the top-left when you visit the site.   I also remember how the formatting from that site had changed the name of my flash drive to PENDRIVE. 

Anyway, I followed directions, and had Ubuntu running alongside Windows XP in a few short hours.  I think the distro is in my hard drive, I don't see how it cannot be. It is not run through a virtual machine via Windows.  

I hope I answered the question right. I'm sorry if I'm not that savvy with computers. 

One other thing,   Blender shows up as "Blender-2.69-linux-glibc211-i686" in Dash Home, not as Blender.

---

### Post by rolfUser on 2013-12-20
> **monkeybrain20122 said:**
> See if this works
[http://ubuntuforums.org/showthread.php?t=1396959](http://ubuntuforums.org/showthread.php?t=1396959)

I am going to take my time to process this.
For me, it looks pretty advanced, so I'm not sure what you want me to try.
I might even take more than a day to get back on these forums to work on this problem.

Thinking is... kind of hard to do sometimes.

---

### Post by monkeybrain20122 on 2013-12-20
> **rolfUser said:**
> As I recall, I went to a site like this one: [http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download)   to format my flash drive some months back.

  I was on Windows XP and my plan was to install Ubuntu 12.04 LTS by booting from the BIOS, using the flash drive, instead of a disc.
That site, I think, is the one I used to format my USB drive b/c I remember the symbol at the top-left when you visit the site.   I also remember how the formatting from that site had changed the name of my flash drive to PENDRIVE. 

Anyway, I followed directions, and had Ubuntu running alongside Windows XP in a few short hours.  I think the distro is in my hard drive, I don't see how it cannot be. It is not run through a virtual machine via Windows.  

That sounds ok

> One other thing,   Blender shows up as "Blender-2.69-linux-glibc211-i686" in Dash Home, not as Blender.
That is the name of the folder. The binary is inside . Open the folder and click the file "blender"  But before that just make sure two things
1) Open the file manager, on the very top of the screen you will find "Files" Click it, in the drop down menu choose Preferences, click it, go to the behaviour tab and under Executable Text Files, choose "ask each time".
2)Open the folder "Blender-2.69-linux-glibc211-i686" and make sure the file "blender" is executable: right click it and Properties > Permissions check the box "allow executing file as program" if it is not checked already.
Now click on the file and you should get a dialogue asking you what to do with the file, just click run.

---

### Post by monkeybrain20122 on 2013-12-20
> **rolfUser said:**
> I am going to take my time to process this.
For me, it looks pretty advanced, so I'm not sure what you want me to try.
I might even take more than a day to get back on these forums to work on this problem.

Thinking is... kind of hard to do sometimes.

Hmm.. that is probably not the right link, sorry about that..

I am sorry, I don't really know how to fix this. It seems that your problem may have to do with xserver, all the solutions I can find are about AMD/ATI cards but yours is an intel. Maybe you should open a new thread under the title "glxinfo badReaquest" or something like that and post the info of your hardware, i.e outputs from
```
lshw -C display
```
and the outputs of 
```
glxinfo | grep OpenGL
glxinfo | grep rendering

```
Hopefully someone more knowledgeable will help you. Good luck.

---

### Post by rolfUser on 2013-12-27
Please just give me a few more days.
I must have a recurring headache or something from this problem.
Please be patient.  I will get back. Promise.

---

### Post by rolfUser on 2013-12-31
This still did not work.
But I think I would have to resolve the matter where it cannot open first. Then a prompt would come up.

---

### Post by rolfUser on 2013-12-31
Inputting: [FONT=courier new]lshw -C display[/FONT]
```

WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```


inputting [FONT=courier new]glxinfo | grep OpenGL[/FONT]
```

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".

```


and inputting [FONT=courier new]glxinfo | grep rendering[/FONT]
```

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".

```


Okay, so we were not able to resolve the matter of opening the Blender 3-D modeling program.
I suppose this is a bummer, but at least it had a good run while it lasted.
So this is pretty tough, understanding what conventions or protocols that are used to... uh... program ...  the right... file extensions... add ons.... how would I know what the right words are?   Probably b/c I was raised on Windows. :(  In Windows, you hardly have to know all this stuff, as far as I know.

Thanks anyway for the help.
And to you and everyone else reading this, a happy new year to you.

---

