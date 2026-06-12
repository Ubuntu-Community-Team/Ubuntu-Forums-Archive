---
title: "Need suggestions on webcam viewing programs"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by pjbgravely on 2008-03-02
I am trying to set up a Ubuntu 7.10 laptop to use the Intel play QX3 microscope. The webcam inside is supported, and I can view it on Cheese. The problem is the laptop already has a built in webcam and Cheese only seems to be able to use /dev/video0 while the microscope is at /dev/video1

What I have tried already:

-Compiling the QtX3 program, even after rewriting the make file, the program is too old to compile.

-Camorama is able to change devices but refuses to work with 4 out of 5 webcams I have tried including this one.

-Ucview, refuses to work with any webcam I have tried.

Does anyone know of another webcam viewer that can switch devices ( command line is fine) and has adjustments? I can setup launchers to turn the lights on and off, so I just need a viewer.

Paul

---

### Post by soerenp on 2008-05-04
Did you have any luck with your work on Qtx3 ?

Tonight I managed to get mine working on Hardy Heron. It's a bit laborious. I'm not a programmer but here's what I did :

With the Synaptic Package Manager install these Qt packages :

[B]libqt3-mt
libqt3-mt-dev[/B]

Next add the colorspace_conv=1 parameter to the cpia kernel module.

Open the /etc/module.d/options file:

**sudo gedit /etc/module.d/options**

Add these lines:

[B]# cpia parameter
options cpia colorspace_conv=1[/B]

In your home directory unzip your qtx3-0.3.tar.gz file. Right-click and choose "extract here"

Go to the /qtx3/QtX3 directory

**cd /qtx3/QtX3**

Clean up the directory

**make clean**

Generate a new makefile

**qmake -o Makefile QtX3.pro**

Edit the new makefile by adding the bold lines:

####### Files

HEADERS = 
SOURCES = main.cpp [B]\
		Qx3Model.cc[/B]
OBJECTS = .obj/main.o \
		**.obj/Qx3Model.o \**
		.obj/mainform.o \
		.obj/qmake_image_collection.o

- and further down the makefile:

####### Compile

.obj/main.o: main.cpp .ui/mainform.h \
		Qx3Model.hh
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/main.o main.cpp

**.obj/Qx3Model.o: Qx3Model.cc Qx3Model.hh**
    **$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/Qx3Model.o Qx3Model.cc**

Next you have to edit the actual QtX3 code a bit. 

Open the file Qx3Model.cc

**gedit QtX3Model.cc**

Replace all instances of "/proc/cpia/video2" with cpia_file.data(). It's three places in all :

First section:

bool Qx3Model::getLineBoolean( string token ) {
	std::ifstream from(**"/proc/cpia/video2"**);
	char line[256];

replace with

bool Qx3Model::getLineBoolean( string token ) {
	std::ifstream from(**cpia_file.data()**);
	char line[256];

- and

void Qx3Model::setTopLight(bool state) {
	std::ofstream to(**"/proc/cpia/video2"**);
	to << "toplight: " << (state ? "on":"off") << endl;
	to.close();
}

bool Qx3Model::getBottomLight(void) {
	return getLineBoolean("bottomlight:");
}

void Qx3Model::setBottomLight(bool state) {
	std::ofstream to(**"/proc/cpia/video2"**);
	to << "bottomlight: " << (state?"on":"off") << endl;
	to.close();
}

replace with

void Qx3Model::setTopLight(bool state) {
	std::ofstream to(**cpia_file.data()**);
	to << "toplight: " << (state ? "on":"off") << endl;
	to.close();
}

bool Qx3Model::getBottomLight(void) {
	return getLineBoolean("bottomlight:");
}

void Qx3Model::setBottomLight(bool state) {
	std::ofstream to(**cpia_file.data()**);
	to << "bottomlight: " << (state?"on":"off") << endl;
	to.close();
}

Now you can compile QtX3

**make**

Check which video device was assigned to your Qx3 (assuming the Qx3 is your only cpia device)

**ls /proc/cpia**

Mine is video0

Run QtX3 like this :

**./QtX3 /dev/video0 /proc/cpia/video0**

Cheers

Soeren

---

### Post by soerenp on 2008-05-04
I'm sorry, make that:

Next add the colorspace_conv=1 parameter to the cpia kernel module.

Open the /etc/modprobe.d/options file:

[B]sudo gedit /etc/modprobe.d/options
[/B]
Add these lines:

[B]# cpia parameter
options cpia colorspace_conv=1
[/B]

---

### Post by pjbgravely on 2008-05-04
Thanks so much. If it works for me I will try to make a .deb so no one else has to go through all that. 

Paul

---

### Post by soerenp on 2008-05-05
Please do make a .deb package. This process is still a mystery to me.

I spotted another typo :

Next you have to edit the actual QtX3 code a bit. 

Open the file Qx3Model.cc

**gedit Qx3Model.cc**

Some additional comments that I would like to make are that you probably have to reboot to make the cpia module parameter effectice. And to avoid any doubts about the device name (video?) I will try to add a udev rule to recognize the Qx3 and assign a fixed device name, probably qx3

Soeren

---

### Post by pjbgravely on 2008-05-11
I found another typo

.obj/Qx3Model.o: Qx3Model.cc Qx3Model.hh
$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/Qx3Model.o Qx3Model.cc

Needs to be:

.obj/Qx3Model.o: Qx3Model.cc  \
		Qx3Model.hh
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/Qx3Model.o Qx3Model.cc


After that the program compiled fine and ran.
There are some flashings in the output but it doesn't effect captures. Considering the cpia module was completely broken when I started testing Hardy I am just happy it works.

You don't need to reboot to effect the configuration changes to the module, you just need to unplug all webcams using the cpia module.

I created a patch file for your changes. It needs to be submitted to the bug section of QtX3 so that I can create a .deb. If you want to add your name and email to it, just replace "anonymous" in the patch file with your name and email(if you would like) or send them to me to add. If not I will submit it as is and start with the .deb, which hopefully will install the program, create a menu item, and change the options for cpia. 

Paul 

PS So much for the .diff, I can't seem to upload, but will try again tomorrow.

---

