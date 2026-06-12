---
title: "Getting Skype video to work"
date: 2012-02-26
forum: Multimedia Software
---

### Post by edanto on 2012-02-26
I'm wondering if anyone could give just a little extra help with these instructions that I found in an ubuntu discussion on the Skype website.  I would like to get video working in Skype calls.

The instructions are here - [http://community.skype.com/t5/Linux/video-is-not-working-on-Ubuntu-11-10/m-p/395723#M783](http://community.skype.com/t5/Linux/video-is-not-working-on-Ubuntu-11-10/m-p/395723#M783)
-----------------------------------------------------------
Hi,
 
I have no idea how to edit the Startup Applications  or the Main Menu item for Skype in Ubuntu (I am using 11.10 64bit  version), but there is simply workaround.
Skype entry in the  Startup Applications or the Main Menu points to binary file  /usr/bin/skype, so it is enough to modify this binary file in order to  add needed startup parameter:
 
*LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so*
 
(You can use your version of LD_PRELOAD parameter: *LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so)*
 
To do this perform following steps:
 
1. Rename original binary skype file:
 
*sudo mv /usr/bin/skype /usr/bin/oldskype*
 
2. Write following bash script and store it in file named *skype*:
 
*#!/bin/bash*

*LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so oldskype*
 
3. Add executive property to newly created file:
 
*chmod +x skype*
 
4. Copy script skype to /usr/bin
 
*sudo cp skype /usr/bin*
 
That's all [IMG]http://skypec.i.lithium.com/html/images/smilies/smile_20.png[/IMG],  next when you run skype from Main Menu or just from console by typing  skype the LD_PRELOAD parameter will be automatically added and video  will be avialable.
 
BR,
 
esso
--------------------------------------

The person that posted them is using the 64 bit version, and I am not.  What might be different for me? Is it safe for me to experiment with both LD_PRELOAD parameters and see what works?  I really don't want to break my ubuntu and I'm out of my depth!

Clearly, I am a real beginner with Ubuntu, and don't know much at all about editing files. I really only know about 4 CLI commands.  I don't actually know how to do step 2 above.  Do I just go to that directory, make a new text file with that info in it?  How do I make that a script instead of just a text file?  I'll be researching those questions online...

thanks

---

### Post by davidvandoren on 2012-02-27
here is what I did to get it working in Ubuntu 10.04

```
 sudo gedit /usr/local/bin/skype
```

Paste this into the file that opens up
```
#!/bin/bash LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
```


In the terminal one more thing 
```
sudo chmod a+x /usr/local/bin/skype
```

That's it.

---

