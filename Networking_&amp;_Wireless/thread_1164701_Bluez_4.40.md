---
title: "Bluez 4.40"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by paraplegicpanda on 2009-05-19
I'm working on getting my Motorola PC850 bluetooth dongle to work with my HP dv6704nr laptop and having some issues. I'm hoping that I can solve them by installing the latest version of bluez-utils, 4.40.

Everything has ran relatively smoothly so far... I downloaded the file from here:
[http://www.bluez.org/download/]("http://www.bluez.org/download/")

Then I ran the normal compiling method:
```
tar -xvf bluez-4.40.tar.gz
cd bluez-4.40
./configure

```

Here I ran into a glitch and needed to install libdbus-1-dev... No big deal. After installing it I proceeded to use the ./configure command again and it worked just fine. Unfortunately I got a message that befuddled me when I ran the make command:

```
libtool: link: cannot find the library `../sbc/libsbc.la' or unhandled argument `../sbc/libsbc.la'                                                                                    
make[3]: *** [ipctest] Error 1                                                                                                                                                        
make[3]: Leaving directory `/home/god/Desktop/bluez-4.40/audio'                                                                                                                       
make[2]: *** [all] Error 2                                                                                                                                                            
make[2]: Leaving directory `/home/god/Desktop/bluez-4.40/audio'                                                                                                                       
make[1]: *** [all-recursive] Error 1                                                                                                                                                  
make[1]: Leaving directory `/home/god/Desktop/bluez-4.40'                                                                                                                             
make: *** [all] Error 2
```

Any suggestions on this one? Google has failed me so far so I am coming to the ever-astute Ubuntu community for assistance. Thanks in advance guys!

---

### Post by g00f on 2009-05-21
I have the same issue. Googled & only found this thread. Anyone?

---

### Post by g00f on 2009-05-22
I had a bit more time to spend on this today. Turns out you have to look more closely at the output of the configure command, even if it didn't exit with an error. Scroll back up and look for lines that have 'no' in them, prioritise and resolve them.

In this case, one of interest is:

```
checking for ALSA... no
```

Do a

```
sudo apt-get install libasound2-dev
```

then that configure line changes to 'yes' and the code compiles.


Edit: FWIW, I also had to install: libusb-dev libgstreamer-plugins-base0.10-dev libsndfile1-dev libnl-dev gtk-doc-tools

---

### Post by NICU on 2009-06-05
I had the same error.  Thanks for finding the dependency. 

After installing that dependency I had to re-run ./configure then make again.

---

### Post by PreviousN on 2009-06-09
After you compiled bluez from source, did you in fact fix your original problem? I'm hoping the same thing, trying to compile the latest bluez (I think its now at 4.42) to get a dongle to work. 

Are you getting the "connection timed out" error? I'm getting that and it's becoming a time-sink. 

Thanks in advance for replying.

---

### Post by jkatabathuni on 2009-07-28
I believe this is a bug in the configure script that turns on SBC only when gstreamer or alsa is enabled. I believe SBC must be unconditionally enabled. If you don't have alsa-devel or don't want to enable alsa (--enable-alsa=no to configure), you must still be able to build bluez.

So, the following line in the script:

if test "${alsa_enable}" = "yes" || test "${gstreamer_enable}" = "yes"; then

may be modified to  the following:

if test "${alsa_enable}" = "yes" || test "${gstreamer_enable}" = "yes" || test "yes" = "yes"; then

to let sbc dir be built.

---

### Post by jkatabathuni on 2009-07-28
A clarification to my previous posting. SBC is required for building audio/ipctest.c. However, this file is not controlled by TEST_TRUE variable and so even if --enable-test=no is passed to the configure script, ipctest will still be built.

---

