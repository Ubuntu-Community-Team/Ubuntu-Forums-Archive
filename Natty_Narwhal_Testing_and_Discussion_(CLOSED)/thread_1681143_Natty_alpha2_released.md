---
title: "Natty alpha2 released"
date: 2011-02-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-02-03
I just got this email:

> Welcome to Natty Narwhal Alpha 2, which will in time become Ubuntu
11.04.

Pre-releases of Natty are *not* encouraged for anyone needing 
a stable system or anyone who is not comfortable running into 
occasional, even frequent breakage.  They are, however, recommended 
for Ubuntu developers and those who want to help in testing, 
reporting, and fixing bugs.

Alpha 2 is the second in a series of milestone CD images that 
will be released throughout the Natty development cycle.  
New packages showing up for the first time include:
 * LibreOffice 3.3 (has replaced OpenOffice.org 3.2)
 * X.org Server 1.10 and Mesa 7.10
 * Linux Kernel 2.6.38-rc2. 
 
Unity is now the default in the Ubuntu Desktop session.  It
is only partially implemented at this stage, so keep an eye on
the daily builds, new features and bug fixes are emerging daily!

Alpha 2 includes a number of software updates that are ready for 
wider testing.  Please refer to [http://www.ubuntu.com/testing/natty/alpha2](http://www.ubuntu.com/testing/natty/alpha2) 
for more detailed information on the new features and known issues 
with this development release of Natty.  
  
You can download Alpha 2 ISOs here:

  [http://cdimage.ubuntu.com/releases/natty/alpha-2/](http://cdimage.ubuntu.com/releases/natty/alpha-2/) (Ubuntu Desktop and Server)
  [http://uec-images.ubuntu.com/releases/natty/alpha-2/](http://uec-images.ubuntu.com/releases/natty/alpha-2/) (Ubuntu Server for UEC and EC2)
  [http://cdimage.ubuntu.com/ubuntu-netbook/releases/natty/alpha-2/](http://cdimage.ubuntu.com/ubuntu-netbook/releases/natty/alpha-2/) (Ubuntu Netbook ARM) 
  [http://cdimage.ubuntu.com/kubuntu/releases/natty/alpha-2/](http://cdimage.ubuntu.com/kubuntu/releases/natty/alpha-2/) (Kubuntu)
  [http://cdimage.ubuntu.com/xubuntu/releases/natty/alpha-2/](http://cdimage.ubuntu.com/xubuntu/releases/natty/alpha-2/) (Xubuntu)
  [http://cdimage.ubuntu.com/ubuntustudio/releases/natty/alpha-2/](http://cdimage.ubuntu.com/ubuntustudio/releases/natty/alpha-2/) (Ubuntu Studio)
  [http://cdimage.ubuntu.com/edubuntu/releases/natty/alpha-2/](http://cdimage.ubuntu.com/edubuntu/releases/natty/alpha-2/) (Edubuntu DVD)
  [http://cdimage.ubuntu.com/mythbuntu/releases/natty/alpha-2/](http://cdimage.ubuntu.com/mythbuntu/releases/natty/alpha-2/) (Mythbuntu)


This is quite an early set of images, so you should expect some bugs.  For a
list of known bugs (that you don't need to report if you encounter), please
see:

  [http://www.ubuntu.com/testing/natty/alpha2](http://www.ubuntu.com/testing/natty/alpha2)

If you're interested in following the changes as we further develop
Natty, have a look at the natty-changes mailing list:

  [http://lists.ubuntu.com/mailman/listinfo/natty-changes](http://lists.ubuntu.com/mailman/listinfo/natty-changes)

We also suggest that you subscribe to the ubuntu-devel-announce list
if you're interested in following Ubuntu development. This is a
low-traffic list (a few posts a week) carrying announcements of
approved specifications, policy changes, alpha releases, and other
interesting events.

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

Bug reports should go to the Ubuntu bug tracker:

  [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Enjoy,

Kate Stewart
on behalf of the Ubuntu release team


---

### Post by Quackers on 2011-02-03
Installed :-)  Not going too well though :-(
It worked fine at first using default video. It still worked fine (in classic) after installing the 3d experimental driver (I have nvidia card) - even compiz ran ok. However, post-updates I have no panels :-( Fortunately I installed cairo dock, so I can access things, but compiz is a bit wonky now. If I try to log in to desktop edition I get an empty desktop. Can the experimental 3d driver operate unity? Not here, anyway!

---

### Post by kansasnoob on 2011-02-03
I was very pleased until I tried to access a partition that's not mounted during boot. At that point things totally hung :oops:

But it is Alpha 2 :lolflag:

Actually I'm fairly impressed given the magnitude of changes involved.

---

### Post by t1497f35 on 2011-02-03
> **kansasnoob said:**
> 
Actually I'm fairly impressed given the magnitude of changes involved.
Me too, Unity spares me up to like 15% of vertical space which in real life (on wide screens) makes quite a lot of difference! I'm impressed, Unity is probably gonna be better than apple's design, and certainly better than that in win7, keep the good work guys, this is the type of decisions I've been waiting for in Linux.

---

### Post by rburkartjo on 2011-02-03
on my end and i am only installing safe upgrades the latest updates killed ubuntu tweak. still cant start the classic desktop it is all still garbage. on the 2d the desktop icons dont show though they do on the 3d. still have docky so this is usable and thank goodness gnome do is still working great

---

### Post by rburkartjo on 2011-02-04
even if you try to download the newest version of tweak from there website it wont work. had this problem in alpha1 hope it is fixed soon

---

### Post by kaehny on 2011-02-04
Some issues encountered using regular update manager (last). 

- Still "partial upgrade"
- First tries with apt-get and aptitude left my machine in unusable no panel state. I restored back to alpha1 and used upgrade manager
- Firefox was blown away. Not there anymore
- Thunderbird fine, what gives?
- pysol (my install) was blown away - key app for me :-)
- I used Ubuntu Software center and just installed those and am running now ok it seems
- will check whether alps touchpad works or I still need to fake as a mouse

---

### Post by KegHead on 2011-02-04
Hi!

Looking at alpha 2.

I concur with everyone---it's an alpha.

Will keep on trying to work w/a2.

KegHead

---

### Post by Kirboosy on 2011-02-04
Its always amazing when playing with Alpha software. You see it in Alpha and you are like "How on earth will they get it done?" but by the time the release date comes its done and ready to go. :D

Keep up the good work all you developers.

---

### Post by tjeremiah on 2011-02-04
> **rburkartjo said:**
> on my end and i am only installing safe upgrades the latest updates killed ubuntu tweak. still cant start the classic desktop it is all still garbage. on the 2d the desktop icons dont show though they do on the 3d. still have docky so this is usable and thank goodness gnome do is still working great

same happening to me too. Its probably due to python 2.7

---

### Post by kaehny on 2011-02-04
Ok some more observations.

- Runs fine now.
- All the grub boot options for various kernels are back on main grub menu. I liked when only the latest was there. I could fix it but, just a note.
- I had to add back again the psmouse.conf file that causes my alps trackpad to be interpreted as a mouse so I can get side scroll on the pad. This was an issue before 10.10, was fixed for that release, but it is broken again in all the 11.04 stuff. A definite regression. I am using the work around but hope this is fixed.

---

### Post by ecr959 on 2011-02-04
I agree with Caboose,  I also wanted to say "great job" to the developers.  Lots of improvements in A2, and by the time Final release comes out, we will all be impressed with how polished it will be.   I am Ubuntu fan since Feisty Fawn or longer, and a big "we appreciate" thumbs up to all involved with development.

Sincerely,

---

### Post by Quackers on 2011-02-04
Hmm, it seems to me that alpha2 is one regression after another. The (empty) desktop is completely unusable, I have no panels, ctrl+alt+t and Alt+f2 does nothing. In order to use it at all I installed cairo dock (to get the use of a terminal). I then installed unity-2d and I now have more usability. Compiz won't run and neither will unity (normal) even though I have the experimental 3D driver installed.
Right-clicking on the desktop has no effect at all, but right-clicking in any window works fine.
Firefox somehow got completely removed! So did Gimp. The Global Menu shows a nice dark background with nice new icons, but clicking on any of them does nothing. 
So, all in all,it's a rather disappointing alpha2 for me.
I know others have unity and compiz working with the experimental 3D driver, so maybe it's just a product of my hardware configuration, or all part of the nvidia problem, I don't know. 
I don't have much option but to use the alpha1 install in the meantime (with about 30 update packages held back).
I'll wait and see :-)

---

### Post by tjeremiah on 2011-02-04
> **rburkartjo said:**
> even if you try to download the newest version of tweak from there website it wont work. had this problem in alpha1 hope it is fixed soon

I get this error in the terminal

```
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
/usr/lib/python2.7/dist-packages/ubuntutweak/mainwindow.py:73: GtkWarning: IA__gtk_widget_get_realized: assertion `GTK_IS_WIDGET (widget)' failed
  self.pack_start(Tip(tip), False, False, 10)
/usr/lib/python2.7/dist-packages/ubuntutweak/mainwindow.py:73: Warning: instance of invalid non-instantiatable type `(null)'
  self.pack_start(Tip(tip), False, False, 10)
/usr/lib/python2.7/dist-packages/ubuntutweak/mainwindow.py:73: Warning: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.pack_start(Tip(tip), False, False, 10)
/usr/lib/python2.7/dist-packages/ubuntutweak/mainwindow.py:73: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.pack_start(Tip(tip), False, False, 10)
Bus error (core dumped)

```
EDIT: SOLVED

---

### Post by grubdude on 2011-02-04
Just installed fresh A2. Looks pretty much the same to me as late A1. Still getting wrong panel colors. Also same updates listed that ended up ininstalling firefox, gwibber, various icons etc.
 
Does anyone know if the curent updates are safe because I do not want to hose a fresh install..

---

### Post by plun on 2011-02-04
"known issues" is a complete disaster IMHO......

> Known issues

  

As is to be expected, at this very early stage of the release process, there are some significant known bugs that users may run into with the Natty Alpha 2 Release. The ones we know about at this point (and some of the workarounds), are documented here so you don't need to spend time reporting these bugs again:   
Graphics and Display

  

    The effectiveness of the current hibernate implementation is under discussion, and it has been disabled for now. Hibernate is not available from the GUI in Alpha 2 (710796).   
    The binary video drivers -fglrx and -nvidia do not have XServer 1.10 compatibility, so do not function in Alpha 2. We anticipate receiving an updated driver with this support from NVIDIA in the coming weeks, and an updated -fglrx from AMD at some point prior to Natty's release, but do not know their exact ETAs.   
    The -nouveau video driver has had an ABI change but lacked a version number increment. Following Debian we're versioning it as 'libdrm-nouveau1a'. Be aware this can cause difficulties in upgrading/downgrading from PPAs that include libdrm packages.   
    The -synaptics driver has received a new acceleration mechanism. Trackpad users may notice a significant decrease (or increase) in acceleration as a result. We are investigating configuration options for this new behavior.   

    Compiz can crash for some people at start, leaving them in an empty session, there is a fix under investigation (709380)   

    Windows sometimes don't appear or you can have the feeling that the interface is stuck (no mouse input) but still responsive to the keyboard. This is due to (709461) and is under investigation   

    Desktop freezes if new window takes focus while menu is open. (603482)   

    In focused dialog, alt-leftclick-dnd doesn't always work, it selects text like if alt was not pressed. (711911)  

    Layout indicator items are not being updated and not working. (711749)
    The unity migration tool crashes on a clean install at startup, the fix is already committed and will arrive just after Alpha2.

    Unity can see a slowdown when places are opened. The places in general are really a first draft (empty sometimes when opened for instance, missing icons…). (711174)

    Some people are reporting issues with LibreOffice interacting with unity.(709138)

    Have temporarily resumed using an older version of glew 1.5.2 since nux/compiz crashes when using glew 1.5.7 (711401, 711396) 


Since Unity is in active development right now, please check the unity bug reports before filing new bugs. 


A real mess......#-o

---

### Post by MacUntu on 2011-02-04
I don't see the problem?

---

### Post by grubdude on 2011-02-04
Well, at this point, I would be happy if they just fix guest additions for virtualbox 4.0. It cannot find the kernel header info.....

---

### Post by plun on 2011-02-04
> **MacUntu said:**
> I don't see the problem?

Well, both Xserver 1.10 and severe Unity problem.

What a mess IMHO.

I am running Ubuntu Classic with locked X-stack including a real nVidia-driver so for me its not a problem...):P

---

### Post by grubdude on 2011-02-04
Yea, running classic here too in vm but ever since releasing the new kernel, guest additions is broken.

---

### Post by Quackers on 2011-02-04
> **MacUntu said:**
> I don't see the problem?

Did you read the preceding poosts?  :-)

---

### Post by plun on 2011-02-04
> **Quackers said:**
> Did you read the preceding poosts?  :-)

Its "awesome".......):P

Kate Stewarts second release must be a real low-mark release....where is Steve L ?

---

### Post by tjeremiah on 2011-02-04
> **rburkartjo said:**
> even if you try to download the newest version of tweak from there website it wont work. had this problem in alpha1 hope it is fixed soon

a recent update fixes the problem. Well, it did for me.

---

### Post by MacUntu on 2011-02-04
> **Quackers said:**
> Did you read the preceding poosts?  :-)

Pre-beta testing is for tough users only! 8)

---

### Post by Quackers on 2011-02-04
> **MacUntu said:**
> Pre-beta testing is for tough users only! 8)

I'm so tough I've got 6 Ubuntu installs to choose from :-)
Even so, it's quite disappointing to install alpha2 and after running updates, and having not installed any extra graphics drivers at all, to get an unusable desktop! Not very good, I think. Alpha1 was much better (if you allow for holding back update packages that you know will break it).

---

### Post by rburkartjo on 2011-02-05
after the latest updates ubuntu tweak is working again

---

### Post by scradock on 2011-02-05
Haven't installed from the new alpha2, just upgrading as usual. It looks like normal alpha experience to me; especially as it's not every time we get a new X, and a completely new desktop shell. I could wish for some faster progress with replacing gnome-panel functionality, but it will be here before release,I'm sure.

Having AIT graphics helps me stay calm at this stage, I guess; I'm not having the problems nvidia users are experiencing. As it is, I can choose Classic (gnome-panels), Unity2d or Unity desktops at log-on, and they all let me do what I need to do - most of the time.

Just my two cents....

---

### Post by Harry33 on 2011-02-05
> **scradock said:**
> Haven't installed from the new alpha2, just upgrading as usual. It looks like normal alpha experience to me; especially as it's not every time we get a new X, and a completely new desktop shell. I could wish for some faster progress with replacing gnome-panel functionality, but it will be here before release,I'm sure.

Having AIT graphics helps me stay calm at this stage, I guess; I'm not having the problems nvidia users are experiencing. As it is, I can choose Classic (gnome-panels), Unity2d or Unity desktops at log-on, and they all let me do what I need to do - most of the time.

Just my two cents....

It is true, that open source ATI driver works much better than nouveau.
Still the best functionality ATM can be gained by downgrading xserver 1.10 to xserver 1.9. and then using nvidia-current.

We do see a new X pretty often, in fact Lucid had new one, Maverick had new one and now Natty has a new one. New ABI each time.
The biggest jump was between xserver 1.7 and xserver 1.8 in Lucid dev cycle.

---

### Post by TenPlus1 on 2011-02-05
Ubuntu 11.04 alpha 1 installed fine and worked ok, but alpha 2 wont even boot from cd, it brings up a kernel panic and stops dead...

---

### Post by spych102 on 2011-02-05
I got nothing but a bootsplash and a kernel panic when I used the CD.

---

### Post by JMB74 on 2011-02-05
> **TenPlus1 said:**
> Ubuntu 11.04 alpha 1 installed fine and worked ok, but alpha 2 wont even boot from cd, it brings up a kernel panic and stops dead...

> **spych102 said:**
> I got nothing but a bootsplash and a kernel panic when I used the CD.

There are several bugs reported on that I think?

---

### Post by rburkartjo on 2011-02-05
thought something like that might happen. that is why i am continually updating my alpha1 install. there are still a lot of stuff being held back due to dependency problems

---

### Post by xeizo on 2011-02-05
Updating from Alpha 1 daily from one day before the X 1.10-breakage, but had to update to 1.10 since other things started breaking by not using 1.10 when I upgraded the other stuff. All updates possible made, as of now, and Nvidia-current thrown out.  I've had all of the problems mentioned in the thread, even the free Nvdia-driver was problematic with current Gnome/Unity, I grew tired of it and switched to the Xubuntu desktop for the moment. It's actually fully functional and as it draws very little resources it doesn't suffer as much from using the open source Nvidia driver. In fact, even 1080P video renders without stuttering despite no hw-acceleration available. Using a fairly beefy C2D though.  Xfce 4.8 in Xubuntu-Natty do have some problems of it's own, but they are far less than those in Unity, Gnome or KDE and it is still way more usable than even a functioning Unity at this stage of Unitys development.  We'll see when I can go back to using a "flashy" desktop.

---

### Post by rob.ward78 on 2011-02-05
performed upgrade from Ubuntu 10.10 to 11.04, no major issues.  Only problems i have noticed are:

1. Sometimes unity does not start and need to reboot a few times to get unity desktop working.

2.  the screen that pops up when clicking on Ubuntu logo at top left corner apperas blank, with 11.04Alpha 1 it started pulling up the icons.  possible regression here, i can still work around it tho

3.  sometimes it logs me out of wireless by passing an invalid password error which i know is false as i went onto router to check password which was what i set it.  click on show password on password dialogue to confirm i am entering correct password, which i am, but it still fails.  

these are minor issues considering it is an alpha release, and i am sure that these will be fixed before beta or rc

i would also like to suggest to move the unity launcher by putting it down bottom of screen as gnome was, as it will be less of a move from 10.10 Desktop to 11.04 desktop.  

Just my opinion.

---

### Post by rob.ward78 on 2011-02-05
the problem here is as follows

About the Ubuntu tweak 0.5.10
Dependency is not satisfiable: python (< 2.7)

would appreciate a fix for this although it might not be through here.

---

### Post by dext on 2011-02-05
> **rob.ward78 said:**
> the problem here is as follows

About the Ubuntu tweak 0.5.10
Dependency is not satisfiable: python (< 2.7)

would appreciate a fix for this although it might not be through here.

did you Bug it , im sure there is something in the release notes about how to Bug something  like that , that requires python2.7

    **Python 2.7**

> All main packages have now been built and and are installable with Python 2.7. If any incompatibilities are detected during runtime, please report them on the broken package in Ubuntu, and add the official tag 'python27' on the bug. 

[http://www.ubuntu.com/testing/natty/alpha2](http://www.ubuntu.com/testing/natty/alpha2)

---

