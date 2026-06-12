---
title: "Problem with Pure Data (Pd)"
date: 2012-06-01
forum: Multimedia Software
---

### Post by blemon on 2012-06-01
Hello.

I have Ubuntu 12.04 and just now tried to install Pure Data via the Software Center.  I found Pure Data, initiated the install and it has complete.  Yet, no matter what I try, the program never actually opens.  Even after reboot.

Do I have to use another version of Pure Data to be compatible in 12.04?  I'm confused.  Anyone out there get Pd to work in 12.04?

Thank you for any help.

B

[http://puredata.info/](http://puredata.info/)

[http://puredata.info/downloads/pd-extended](http://puredata.info/downloads/pd-extended)

(I would like Extended please, that's what I'm used to on Windows)

---

### Post by greypa on 2012-10-11
Hi
I also recently installed ubuntu studio 12.04.. and could not get pd to work.

after lots of attempts, i seem to have got it running. this is what i did:

uninstall all puredata stuff using synaptic.

download the pd-0.43.1-extended-ubuntu-precise-i386.deb package from puredata.info/downloads > in the experimental releases section

install using ubuntu software centre.

i then found out that for some reason to get jack+pd to work together, you first have to run Patchage. so open applications in this order 1- patchage (just open, no need to do anything); 2-jack (setup+run); 3-pd-extended (might appear in 'development' section of application drop down menu).

im still ironing out a few bugs.. but seems to work ok so far..

hope that helps!

---

### Post by cetag on 2013-01-13
Yes, no luck for me either, so I will try the .deb pack install advice above. 
 
FYI:  I am still on Oneiric 11.10.  I installed via the Software Centre, then ran PD.  It failed to run and reported pd-gui.tcl was unavailable.  I loaded that via Synaptic, and a few other packs. 
 
PD then ran, (complained about no Courier font), but at this point I was unable to set the Audio to ALSA, as it kept complaining about bad audio.  So at this point I had run out of things to try, apart from compiling from source. 

So I'll try as per the last post re the .deb install approach.  Thanks, and what a pity the Software Centre approach seems to have such a high failure rate.

- - - - - - - - Several minutes later - - - - - - 

No luck. I downloaded both the Precise and the Oneiric versions, and tried Oneiric first.  Right-clicked and attempted to install with Software Centre. The SC  "install button" went grey, unstall started but it never came back.  After a while I closed Software Centre, looked at System Monitor to see if any rogue activity but nothing apparent. 
 
I then attempted to install the Precise version. When it opened in Software Centre, there was the message 
"Dependency is not satisfiable: libc6 (>= 2.15)" 

And that's where I've left matters, unable to proceed.  Cannot install PD on Oneiric. Any suggestions gratefully received. Not urgent, just frustrating.

- - - - - - - - Several days later - - - - - -  

Grr. Now I have PD up and running, but cannot confirm which method of install worked. So its now available under Applications, and can be run from the Command line, and the Help system inside PD works. 

After PD signs on, going to the ->Help ->About PD  window, I get the following Application Error; 
couldn't open "/usr/lib/puredata/doc/1.manual/1.introduction.txt": no such file or directory 
so maybe ->Media ->Preferences ->Paths  needs to be set better, current it is set to  /usr/lib/puredata  

~/pd -version   reports back:   Pd-0.43.0 ("") compiled 11:49:52 Jun 16 2011

This shows not the Pd-0.43.4  version, which confirms I had trouble installing that new version. 
[http://autobuild.puredata.info/auto-build/latest/Pd-0.43.4-extended-ubuntu-oneiric-i386.deb](http://autobuild.puredata.info/auto-build/latest/Pd-0.43.4-extended-ubuntu-oneiric-i386.deb)

---

### Post by decodersignal on 2013-01-17
I just installed pd-extended on 12.10 without any problems.

add the ppa from [https://launchpad.net/~eighthave/+archive/pd-extended]("https://launchpad.net/~eighthave/+archive/pd-extended") and just use ```
sudo apt-get install pd-extended
```

---

### Post by dioioib on 2013-03-22
> **decodersignal said:**
> I just installed pd-extended on 12.10 without any problems.

add the ppa from [https://launchpad.net/~eighthave/+archive/pd-extended]("https://launchpad.net/~eighthave/+archive/pd-extended") and just use ```
sudo apt-get install pd-extended
```

The correct ppa is:

 sudo add-apt-repository ppa:eighthave/pd-extended

but otherwise everything works on 12.10

---

