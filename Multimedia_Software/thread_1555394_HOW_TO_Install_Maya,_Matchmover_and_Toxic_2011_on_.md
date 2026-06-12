---
title: "HOW TO: Install Maya, Matchmover and Toxic 2011 on Linux64 bit Ubuntu 10.04"
date: 2010-08-18
forum: Multimedia Software
---

### Post by AmbientOcclusion on 2010-08-18
The installation packages that come with Maya are .rpm packages. To get this running we need to convert the packages to .deb. For that use Alien.

```
sudo apt-get install alien
```

Now there are a few things we need to make sure are installed, like fonts etc.

```
sudo apt-get install csh, tcsh, libglw1-mesa, libglw1-mesa-dev, libaudiofile-dev, libaudiofile0, libaudiofile0-dbg, elfutils, ttf-liberation, ttf-mscorefonts-installer
```

You may also need to install these if you find packages are missing:

```
sudo apt-get install tcsh fam libxp6 libxpm4 libxprintapputil1 libxprintutil1 cpio rpm ia32-libs
```

We need to set up some symbolic links now:

```
sudo ln -s /usr/autodesk /autodesk
sudo ln -s /usr/aw /aw
```

and then:
```

export RPM_INSTALL_PREFIX=/usr
```

We need to convert all of the rpm files to deb using alien. Make a folder on your drive called Maya2011 and move all of your rpm files into there. There is one package that is not included in the rpm file zip which is called adlmflexnetserver-1.2.26-0.x86_64.rpm. This is the license server so you will need it. It is included with the open source code.[COLOR="Red"]*UPDATE: This file may also be in a zip/folder (or other archive) called Autodesk_license_servertools ****
[/COLOR]
*NOTE Autodesk has only released Backburner in 32 bit for Linux, so you won't be able to convert it. If you did so, just remove any backburner packages from the Maya2011 folder. They aren't compatible with our 64 bit architecture.

Here is a list of all the files you will need:

    * EULA
    * adlmapps-1.3.34-0.x86_64.rpm
    * adlmflexnetclient-1.3.34-0.x86_64.rpm
    * adlmflexnetserver-1.3.34-0.x86_64.rpm
    * Composite2011-2011.0-2459.x86_64.rpm Install this if you want Toxic
    * MatchMover2011_0_64-2011.0-177.x86_64.rpm Install this if you want Matchmover
    * Maya2011_0_64-2011.0-271.x86_64.rpm
    * Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm
    * MID.txt
    * setup
    * setup.xml
    * setupbar.png

Now open terminal and navigate to the Maya2011 folder something like cd/whereveryoupuit/maya2011

Pass the following:

```
for i in *.rpm; do sudo alien -cv $i; done
```

This is where you get to use your extra cores. Alien will convert the packages to deb files. It could take 5-15 minutes depending on your system specs.

Now install the .deb packages:

```
sudo dpkg -i *.deb
```

Now we need to set up some symbolic links for programs like fcheck.

```
cd /usr/local/bin
sudo ln -s /usr/autodesk/maya2011-x64/bin/fcheck fcheck
sudo ln -s /usr/autodesk/maya2011-x64/bin/maya2011 maya
sudo ln -s /usr/autodesk/maya2011-x64/bin/imgcvt imgcvt
sudo ln -s /usr/autodesk/maya2011-x64/bin/Render Render

cd /usr/autodesk
sudo ln -s maya2011-x64 maya
```


Let's make some icons on our desktop for our install by entering the following:

```
sudo ln -sf /usr/autodesk/maya2011-x64/desktop/Autodesk-Maya.desktop /usr/share/applications/Autodesk-Maya.desktop
sudo ln -sf /usr/autodesk/maya2011-x64/desktop/Autodesk-Maya.directory /usr/share/desktop-directories/Autodesk-Maya.directory
sudo ln -sf /usr/autodesk/maya2011-x64/desktop/Maya.png /usr/share/icons/hicolor/48x48/apps/Maya.png
```


Set up Mental Ray:

```
sudo mkdir /usr/tmp
sudo chmod 777 /usr/tmp
```


Set up the user interface:

```
sudo sh -c "echo 'setenv LC_ALL en_US.UTF-8' >> /usr/autodesk/maya2011-x64/bin/maya2011"
```

After this completes, it's time to set up the licensing system:

```
/usr/autodesk/maya2011-x64/bin/licensechooser /usr/autodesk/maya2011-x64/ standalone unlimited
```

Rare for Linux, reboot.

Let's create a fake binary license file:

Go to your home folder and create a .c file named **mayaInstall.c**

Enter:
```

int main (void) {return 0; }

cd /home/usernameexample/Maya2011
sh -c "echo 'int main (void) {return 0; }' >> /home/exempleuser/Maya2011/mayaInstall.c"

```
Open up terminal again and enter:

```
export LD_LIBRARY_PATH=/opt/Autodesk/Adlm/R1/lib64/
```


For the next line of code, the number in red 658D1 is your product code. This can change with different versions of Maya, so be sure to enter it correctly or you will get an error: reason ##

```
/usr/autodesk/maya2011-x64/bin/adlmreg -i S 658C1 658D1 2011.0.0.F &#8220;yourserialnumber&#8221; /var/opt/Autodesk/Adlm/Maya2011/MayaConfig.pit
```

Autodesk recommends a reboot at this point, this has been the only way I have done it as well.

Navigate to your Maya2011 folder.

```
sudo ./setup
```

Follow menu instructions.


Open up a terminal and enter the following:

```
cd /usr/lib

sudo ln -s libtiff.so.4 libtiff.so.3

cd /usr/autodesk/maya2011-x64/lib/

sudo ln -s /usr/lib/libcrypto.so.0.9.8 libcrypto.so.6

sudo ln -s /usr/lib/libssl.so.0.9.8 libssl.so.6
```

We are almost done, we need to add the following symbolic links:

```
ln &#8211;s /usr/lib64/libssl.so.8 libssl.so.6

ln &#8211;s /usr/lib64/libcrypto.so.8 libcrypto.so.6
```

*I have been told that the install documentation that comes with Maya has typos, I haven't looked at it but I know these lines work...


***If the above license setup technique does not work try this:

Open up another terminal to launch the GUI license importer. Input:

```
sudo /opt/Autodesk/Adlm/R1/bin/LTU 657C1 2011.0.0.F -d &#8220;SA&#8221;
```

Enter your license information.


Launch Maya with the maya command!

---

### Post by AmbientOcclusion on 2010-08-18
Let me know if I typo'd or forgot to write down a step...

---

### Post by cppgraphics on 2010-08-27
In the second step I'm getting the following errors. I installed csh, tcsh manually using Ubuntu Software Center. But other packages ubuntu couldn't find it.



sureshkumar@sureshkumar-desktop:~/Desktop$ sudo apt-get install libglw1-mesa-dev, libaudiofile-dev, libaudiofile0, libaudiofile0-dbg, elfutils, ttf-liberation, ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libglw1-mesa-dev,
sureshkumar@sureshkumar-desktop:~/Desktop$ 


Please give a solution.

Thanks

---

### Post by uBeer on 2010-09-06
Dude, this is awesome! It worked!
I have a networked license so I skipped the part with the C-code, but that works awesome as well! You've saved me from having to use Windows the coming half year! :P

---

### Post by AmbientOcclusion on 2010-09-19
> **cppgraphics said:**
> In the second step I'm getting the following errors. I installed csh, tcsh manually using Ubuntu Software Center. But other packages ubuntu couldn't find it.



sureshkumar@sureshkumar-desktop:~/Desktop$ sudo apt-get install libglw1-mesa-dev, libaudiofile-dev, libaudiofile0, libaudiofile0-dbg, elfutils, ttf-liberation, ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libglw1-mesa-dev,
sureshkumar@sureshkumar-desktop:~/Desktop$ 


Please give a solution.

ThanksHi. What repositories are you using?

---

### Post by AmbientOcclusion on 2010-09-19
> **uBeer said:**
> Dude, this is awesome! It worked!
I have a networked license so I skipped the part with the C-code, but that works awesome as well! You've saved me from having to use Windows the coming half year! :P

Thanks man. Glad it worked. Now enjoy the extra processing speed and lack of overhead!

---

### Post by AmbientOcclusion on 2010-09-19
> **cppgraphics said:**
> In the second step I'm getting the following errors. I installed csh, tcsh manually using Ubuntu Software Center. But other packages ubuntu couldn't find it.



sureshkumar@sureshkumar-desktop:~/Desktop$ sudo apt-get install libglw1-mesa-dev, libaudiofile-dev, libaudiofile0, libaudiofile0-dbg, elfutils, ttf-liberation, ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libglw1-mesa-dev,
sureshkumar@sureshkumar-desktop:~/Desktop$ 


Please give a solution.

Thanks
I tried this install on a fresh ubuntu 10.0.4.1 64 bit and ran into the same error you did.

Try a couple of things, first do:
```
sudo apt-get update
```

Then reinstall the line you were having problems with.

If you still receive an error, you can install ***csh*** via **Synaptic**.

Just open **Synaptic**, enter your **admin password** and then click on the magnifying glass (**search**) and enter **csh**. Right Click on it and select **Mark For Installation**. Then click the Green Apply **Checkmark** at the top and it will install.

If other things are missing, installing via **Synaptic** would be a suitable work around. Check your repositories tho'...

---

### Post by AmbientOcclusion on 2010-09-19
One person mentioned having to install ***libfam0*** via Synaptic.

They were attempting to install and encountered ***ldconfig*** deferred processing.

If I am correct, the installation of ***libfam0*** uninstalls ***libgamin0***. But with this, ***ldconfig*** can then be processed.

---

### Post by AmbientOcclusion on 2010-09-19
Installation output. Notice the special instructions for Composite:

> Selecting previously deselected package adlmapps.
(Reading database ... 131706 files and directories currently installed.)
Unpacking adlmapps (from adlmapps_1.3.34-1_amd64.deb) ...
Selecting previously deselected package adlmflexnetclient.
Unpacking adlmflexnetclient (from adlmflexnetclient_1.3.34-1_amd64.deb) ...
Selecting previously deselected package adlmflexnetserver.
Unpacking adlmflexnetserver (from adlmflexnetserver_1.2.26-1_amd64.deb) ...
Preparing to replace adlmflexnetserver 1.2.26-1 (using adlmflexnetserver_1.3.34-1_amd64.deb) ...
Unpacking replacement adlmflexnetserver ...
Selecting previously deselected package composite-2011.
Unpacking composite-2011 (from composite-2011_2011.0-2460_amd64.deb) ...
Selecting previously deselected package matchmover2011-0-64.
Unpacking matchmover2011-0-64 (from matchmover2011-0-64_2011.0-178_amd64.deb) ...
Selecting previously deselected package maya2011-0-64.
Unpacking maya2011-0-64 (from maya2011-0-64_2011.0-272_amd64.deb) ...
Selecting previously deselected package maya2011-0-docs-en-us-64.
Unpacking maya2011-0-docs-en-us-64 (from maya2011-0-docs-en-us-64_2011-89_amd64.deb) ...
More than one copy of package adlmflexnetserver has been unpacked
 in this run !  Only configuring it once.
Setting up adlmapps (1.3.34-1) ...

Setting up adlmflexnetclient (1.3.34-1) ...

Setting up adlmflexnetserver (1.3.34-1) ...

[I][B]Setting up composite-2011 (2011.0-2460) ...
Configuring Composite.
Configure complete.


Finally, in order to have Composite run properly, make sure you make the
following changes.  If you are unsure about the procedure, please
contact your sys admin.

#su - root

Add the following line at the end, after the #@student line.

#vi /etc/security/limits.conf
#@student      -       maxlogins  4
*              soft    nofile     65536
*              hard    nofile     65536

#reboot

Once the machine has rebooted, login as root
# su - root
# tcsh
# limit
descriptors shall be set at 65536[/B][/I]


Setting up matchmover2011-0-64 (2011.0-178) ...

Setting up maya2011-0-64 (2011.0-272) ...

Setting up maya2011-0-docs-en-us-64 (2011-89) ...

---

### Post by el.mustafa on 2010-10-09
Cheers for that AmbientOcclusion.

I've seen it in other forums where, like me, the license transfer GUI fails to launch

3435:server starting (internal)...
3435: deleting Translator Cache
3435:server shutting down...
3435: ==== Closing Conduit for 3435 (init:0, readers:0, writers:0)

the Maya command fails to launch giving an error (too many levels of symbolic links)


 and the serial number is not recognised (despite working fine in Windows and Mac OSx). Terminal asks you to set SerialNumber though not sure what kind of command is this supposed to be. 

If anyone was able to overcome these issues I'd be grateful if you could share your wisdom with here.

Regards
El

---

### Post by Kryptick on 2010-12-19
> libglw1-mesa-dev,
Pretty sure this is because of the ,'s left in the line
remove those and try again....

I can't get this work for the life of me, keeps throwing up the Activation window no matter what sigh

---

### Post by nmpribeir on 2011-01-15
/usr/autodesk/Composite_2011/bin$ ./composite.bin
Cannot load application library: libimf.so: cannot open shared object file: No such file or directory
nuno@nuno-desktop:/usr/autodesk/Composite_2011/bin$ sudo gedit composite
nuno@nuno-desktop:/usr/autodesk/Composite_2011/bin$ ./composite.bin
Cannot load application library: libimf.so: cannot open shared object file: No such file or directory
nuno@nuno-desktop:/usr/autodesk/Composite_2011/bin$ ./composite
Exception encountered: Caught Signal.
Type = "INVALID MEMORY REFERENCE (SIGSEGV)".
What = "Attempt to access unmapped memory at address 0x44 from 0x7f7f4b539862
 RAX = 00000000 RBX = 013EBD58 RCX = 7F7F53FFD064
 RDX = 00000005 RSI = 00000000 RDI = 7F7F54786010
 RIP = 7F7F4B539862 RSP = 7FFF435CD100 RBP = 00000000 EFL = 00010206
".
Exception encountered: [Exception Type = N2Dl15ExInternalErrorE, File = base/atomicLocks/src/lkLockUNIX.cpp, Line=77]
Assertion '::pthread_mutex_destroy( &_mutex ) == 0' failed.
00:00:03.64 [User Message  ] [Messages       ] Initializing libraries.
00:00:03.64 [Fatal Error   ] [Messages       ] Assertion '::pthread_mutex_destroy( &_mutex ) == 0' failed.
^C

libadlmint prob? :]
license issue? what?

Any happy thoughts about it? :]

---

### Post by nmpribeir on 2011-01-15
/usr/autodesk/Composite_2011/bin$ ./composite.bin
Cannot load application library: libimf.so: cannot open shared object file: No such file or directory
nuno@nuno-desktop:/usr/autodesk/Composite_2011/bin$ sudo gedit composite
nuno@nuno-desktop:/usr/autodesk/Composite_2011/bin$ ./composite.bin
Cannot load application library: libimf.so: cannot open shared object file: No such file or directory
nuno@nuno-desktop:/usr/autodesk/Composite_2011/bin$ ./composite
Exception encountered: Caught Signal.
Type = "INVALID MEMORY REFERENCE (SIGSEGV)".
What = "Attempt to access unmapped memory at address 0x44 from 0x7f7f4b539862
 RAX = 00000000 RBX = 013EBD58 RCX = 7F7F53FFD064
 RDX = 00000005 RSI = 00000000 RDI = 7F7F54786010
 RIP = 7F7F4B539862 RSP = 7FFF435CD100 RBP = 00000000 EFL = 00010206
".
Exception encountered: [Exception Type = N2Dl15ExInternalErrorE, File = base/atomicLocks/src/lkLockUNIX.cpp, Line=77]
Assertion '::pthread_mutex_destroy( &_mutex ) == 0' failed.
00:00:03.64 [User Message  ] [Messages       ] Initializing libraries.
00:00:03.64 [Fatal Error   ] [Messages       ] Assertion '::pthread_mutex_destroy( &_mutex ) == 0' failed.
^C

libadlmint prob? :]
license issue? what?

Any happy thoughts about it? :]

---

### Post by Ahz The Cat on 2011-02-23
My install went south in a hurry.  When I try to start Maya now it just spins for a bit then stalls.  No error messages when started from the CL either.  Just nothing.  Apparently I made a bollocks of the whole thing or at least something and need to start again.  

My question is how do I go about uninstalling all the Maya files and do I need to undo the rest of the stuff as well?  

I'm not sure where exactly I went wrong, so there's not much hope of troubleshooting...just a Charlie Brown pick yerself up, dust off and try again.

--Edit--

Not a complete loss then.  It fires up when I use "sudo Maya", but now I'm stuck at the license screen.  Closer!

---

### Post by caedocha on 2011-04-18
Hi, 

I was able to install Maya2011 following a similar guide to the one on this thread. Im able to launch maya, the problem im having is that the camera controls dont work, im not able to move around, to rotate, im only able to zoom with the mouse wheel. Its like maya dont recognize the mouse events. Besides that problem, maya is working great. Does anybody knows a workaround for this issue?
Im using maya 2011 in ubuntu 10.10

thx

caedocha

---

### Post by Pandaluke on 2011-05-16
hey, Im really new to ubuntu

could you tell me where to get the .rpm files 
because the only installer I can fined on the autodesk site is the .exe one 

thanks

---

### Post by transformania on 2011-06-22
I checked into this and, unfortunately, Autodesk does not provide a trial download for the Linux version of Maya.

---

