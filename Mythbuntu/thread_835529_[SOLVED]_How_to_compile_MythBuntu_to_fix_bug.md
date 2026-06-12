---
title: "[SOLVED] How to compile MythBuntu to fix bug?"
date: 2008-06-20
forum: Mythbuntu
---

### Post by DutchLoki on 2008-06-20
> **superm1 said:**
> If you are trying to change the behavior of an action you will have to recompile the code.

Follow these basic steps:

1) apt-get source mythtv
2) sudo apt-get build-dep mythtv
3) sudo apt-get install devscripts
4) dch -i
Put what you are changing in the changelog.
5) Make changes
6) debuild
7) Profit!

Hi, found the previous information elsewhere in this forum and hate to ask questions in others their posts:

I'm fairly new to linux and programming on MythBuntu (have an background as a java, C#, C++ and assembly programmer, but that was some time ago ;) ). At the moment I'm reading in on linux, C++ and QT4 especiall), this to contribute to MythBuntu and MythTV. Because i'm not there yet, i have the following questions.

At this moment I want to step over from analogue to DVB-C tunercards. Because my cable provider does not follow the dvb standards for providing channel information I need to recompile MythTV with the fix for Myth 0.22 discussed in ticket 3640([http://svn.mythtv.org/trac/ticket/3640](http://svn.mythtv.org/trac/ticket/3640))

I have the following questions about following the above steps from superm1

1) Do I need to reconfigure my mythtv settings after rebuilding? 

2) do I loose any of the MythBuntu specifics? if so, what do I need to do else?

3) Where does apt-get (steps 2+3) places the code en scripts?

4) how to proceed with step 6: rebuilding mythTV 

5) Do I just restart my system after this to use the rebuilded mythTV version? Or are there other actions nessecary?



Any help would be great. 

(I'm also interested in guides about starting developing on MythBuntu and/or MythTV).

---

### Post by uopjohnson on 2008-06-20
Form the info you provided in your post you are in way over you head here.  However here are some basic answers to your general questions.  You will need to do a lot of reading before you can get this working dependably.

> 1) Do I need to reconfigure my mythtv settings after rebuilding?
No, as long as you don't try and update from one myth version to another your settings in the DB will remain.

> 2) do I loose any of the MythBuntu specifics? if so, what do I need to do else?
No, mythbuntu relies on the mythtv package which (I believe) is compiled from pristine source from mythtv.org

> 3) Where does apt-get (steps 2+3) places the code en scripts?
Don't worry about steps 2-3 they are building and installing on your system all of the dependencies and utilities so that you can build your own mythtv package.  What you really need to do is get the mythtv-src which you can get with ```
apt-get source mythtv
``` I believe that will place the source in your current directory.

> 4) how to proceed with step 6: rebuilding mythTV
You are going to need to read the documentation in the source you downloaded.  Basically you apply your path and then do a ```
./configure 
make
```
however if I remember correctly there are some interesting variations on this for myth and you will probably want to figure out what the original configure command was that was used by the mythbuntu devs to generate the package.
At this point you have a choice to make.  The ideal solution is to create a new ubuntu package for yourself with your new version and then install that.  This will let you avoid breaking your system next time you update.  This will certainly require you to learn more about ubuntu packaging and the versioning standards.  
A quick search turne dup this link [https://help.ubuntu.com/ubuntu/packagingguide/C/](https://help.ubuntu.com/ubuntu/packagingguide/C/)
You could also just do a make install and then remove your original myth package however that will be a bit unpredictable and will result in failures when you attempt to upgrade.

> 5) Do I just restart my system after this to use the rebuilded mythTV version? Or are there other actions nessecary?

Once you get through the above you won't even need to restart, however by then you will probably be tired from reading and learning and working for a week so you may want to grab a beer.

---

### Post by superm1 on 2008-06-21
> **uopjohnson said:**
> Form the info you provided in your post you are in way over you head here.  However here are some basic answers to your general questions.  You will need to do a lot of reading before you can get this working dependably.


No, as long as you don't try and update from one myth version to another your settings in the DB will remain.


No, mythbuntu relies on the mythtv package which (I believe) is compiled from pristine source from mythtv.org


Don't worry about steps 2-3 they are building and installing on your system all of the dependencies and utilities so that you can build your own mythtv package.  What you really need to do is get the mythtv-src which you can get with ```
apt-get source mythtv
``` I believe that will place the source in your current directory.

Please do steps 2 and 3.  They will ensure your package build gets all the right options when you build.

> 
You are going to need to read the documentation in the source you downloaded.  Basically you apply your path and then do a ```
./configure 
make
```however if I remember correctly there are some interesting variations on this for myth and you will probably want to figure out what the original configure command was that was used by the mythbuntu devs to generate the package.
At this point you have a choice to make.  The ideal solution is to create a new ubuntu package for yourself with your new version and then install that.  This will let you avoid breaking your system next time you update.  This will certainly require you to learn more about ubuntu packaging and the versioning standards.  
A quick search turne dup this link [https://help.ubuntu.com/ubuntu/packagingguide/C/](https://help.ubuntu.com/ubuntu/packagingguide/C/)
You could also just do a make install and then remove your original myth package however that will be a bit unpredictable and will result in failures when you attempt to upgrade.

The configure options are handled as you do your dpkg-buildpackage/debuild.  Also, all the nice patching and packaging will be done for you assuming you do that it that way.

> 
Once you get through the above you won't even need to restart, however by then you will probably be tired from reading and learning and working for a week so you may want to grab a beer.
Yes sir.

---

### Post by DutchLoki on 2008-06-21
> **uopjohnson said:**
> Once you get through the above you won't even need to restart, however by then you will probably be tired from reading and learning and working for a week so you may want to grab a beer.

Okay I have some reading to do, but thats no problem. To follow your advice exacly i'll start of with a beer (we don't want to make any mistake by not following the instructions ;) ). 

That link was real helpfull for me. Never used this kind of packaging before.

---

### Post by DutchLoki on 2008-06-21
> **superm1 said:**
> Please do steps 2 and 3.  They will ensure your package build gets all the right options when you build.

The configure options are handled as you do your dpkg-buildpackage/debuild.  Also, all the nice patching and packaging will be done for you assuming you do that it that way.
Yes sir.

Thanks again for the great info.

---

### Post by trevmar on 2010-04-04
I am following the 7 steps above, as I need to alter the frontend timeout of 7000ms in mythsocket.cpp which causes timeout with AC3 audio, a Motorola DCX3200 cable box, and the Hauppauge HD-PVR.

I understand all the steps up to 
6) debuild

Is this command going to alter the main developer repositories? All I want to do is fix things locally... although this issue "irrecoverable recorder error" due to slow channel changing has been addressed in previous tickets (and ignored by the developers).

Thanks :)

---

### Post by superm1 on 2010-04-05
> **trevmar said:**
> I am following the 7 steps above, as I need to alter the frontend timeout of 7000ms in mythsocket.cpp which causes timeout with AC3 audio, a Motorola DCX3200 cable box, and the Hauppauge HD-PVR.

I understand all the steps up to 
6) debuild

Is this command going to alter the main developer repositories? All I want to do is fix things locally... although this issue "irrecoverable recorder error" due to slow channel changing has been addressed in previous tickets (and ignored by the developers).

Thanks :)
All that does is changes things locally indeed.

---

### Post by trevmar on 2010-04-13
Sorry to be such a newbie, my Linux knowledge is stuck in the "make install" era of software development, and I am struggling to get my mind around the packaging technologies.

I have gotten to the stage of making the changes to the source, and successfully creating and signing a package with debuild. 

How do I use the packaging software to get the new code installed in place of the binaries currently on my system? Do I use pbuilder? The tutorials I can find are all based on chroot and sandboxes, my problem is simpler than that. I just want to install the new package I compiled from the source :)

---

