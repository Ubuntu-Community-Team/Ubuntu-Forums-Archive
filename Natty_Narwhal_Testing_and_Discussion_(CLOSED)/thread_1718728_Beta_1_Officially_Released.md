---
title: "Beta 1 Officially Released"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-03-31
A little late:

> The Ubuntu team is pleased to announce the release of Ubuntu 11.04
beta. 

Codenamed "Natty Narwhal", 11.04 continues Ubuntu's proud tradition of
integrating the latest and greatest open source technologies into a
high-quality, easy-to-use Linux distribution.

Ubuntu 11.04 now combines Ubuntu Desktop Edition and Ubuntu Netbook
Edition.  This edition introduces the Unity environment as the default
desktop.  

Ubuntu 11.04 Netbook edition will still be produced for the ARM
platform, and the team is proud to introduce a Headless edition with
11.04 for ARM.

Ubuntu 11.04 Server has made it easier to provision servers, and reduce
power consumption. 

Ubuntu 11.04 Server for EC2 is available as well, with a new kernel and
improved initialization and configuration options. 

The Ubuntu 11.04 family of Kubuntu, Xubuntu, Edubuntu, Mythbuntu, and
Ubuntu Studio, also reach beta status today.


Ubuntu features
---------------

Unity is now the default Ubuntu desktop session. The Unity launcher has
many new features, including drag and drop re-ordering of launcher
icons, full keyboard navigation support, launcher activation through
keyboard shortcuts, right-click context menu quick-list and switching
between running applications.  

Ubuntu 11.04 comes with the latest Firefox 4.0 as standard web browser.

LibreOffice 3.3.2 has been included in 11.04 as the default office
package.

Banshee 1.9.5 is the standard music player now and has been integrated
into the sound menu.

X.org 1.10.0 and Mesa 7.10.1 are the new versions included with 11.04.

11.04 Beta 1 includes the 2.6.38-7.39 kernel which is based on the
latest mainline kernel, 2.6.38. 

GNU toolchain has transitioned to be based off of gcc 4.5 for i386,
amd64, ARM omap3/omap4 and PowerPC architecture

All main packages have now been built and and are installable with
Python 2.7

dpkg 1.16.0-pre brings us up-to-date with staged changes for the
upcoming Debian 1.16.0 dpkg release, as well as pulling in the current
version of the in-progress multiarch work

Upstart has been updated to 0.9.4-1. There are a lot of new features:
its now "chroot-aware", there is support for basic job/event
visualization, there are two new initctrl commands (show-config,
check-config), a socket bridge is now provided, the latest D-Bus version
now allows D-Bus services to be activated via Upstart, a manual job
configuration stanza, and override file support is now available.

The Ubuntu One control panel now allows selective syncing, and the
launcher icon now displays sync progress.  File syncing speed has been
improved as well. 

The Ubuntu Software Center now allows users to "rate & review" installed
applications, share reviews via integration with social networking
services added into Gwibber,  and has other usability improvements.

Please see [http://www.ubuntu.com/testing/natty/beta](http://www.ubuntu.com/testing/natty/beta) for details.


Ubuntu Netbook on ARM
--------------------

The ARM version is the first one to ship with our new Unity 2D interface
by default.

The 2.6.38 kernel for OMAP4 has had many driver improvements, most
notably the display driver was switched to use the HDMI port by default
and auto detect the monitor resolution. 

Ubuntu Headless developer image is being introduced for omap3 and omap4
hardware.  Headless is fully set up for the serial port and contains a
minimal command line install. 


Ubuntu Server
-------------

cobbler and mcollective have been included, which will make provisioning
servers a bit easier.

Powernap 2.0 uses a new method to reduce power consumption and can now
monitor user activity (Console, Mouse, Keyboard), system activity (load,
processors, process IO), and network activity (wake-on-lan, udp ports
tcp ports) 

Default dhcpd server updated from dhcp3 to isc-dhcp (version 4). 

Eucalyptus is now the latest stable point release (2.0.2) with security
and efficiency fixes. (Known bug against the dhcpd server) 

OpenStack (nova) in Universe is a technology preview, with a recent
snapshot of 2011.2 (Cactus) release. 

libvirt is updated to 0.8.8 with new features and bug fixes (see
upstream change log for full information 0.8.3->0.8.8)  


Ubuntu Cloud
------------

cloud-init has been updated to 0.60. This feature includes support
resizing of / at first boot, adds minimal OVF transport (iso) support
and allow setting of hostname when first booting. Rightscale support has
been added to cloud-config and cloud-init. 

Webscale technologies have been packaged and included, Cassandra 0.7.0,
ZeroMQ, Membase, and XtraBackup. 

Running images in EC2, t1.micro is currently limited to arch amd64. 


Kubuntu
-------

Kubuntu 11.04 Beta 1 sports the latest KDE software including KDE
Platform 4.6.1. 

Kubuntu now provides a working Samba file sharing module that lets you
add and manage shares from the folder's Properties dialogs. 

The new Language Selector module allows you to add, remove, and manage
system languages directly from System Settings. 

An updated system-config-printer-kde brings a number of bug fixes to
Kubuntu's printer management tool. 

Please see  [https://wiki.kubuntu.org/NattyNarwhal/Beta1/Kubuntu](https://wiki.kubuntu.org/NattyNarwhal/Beta1/Kubuntu) for
details. 

        
Xubuntu
-------

Xubuntu wallpaper has been updated for this release. The wallpaper is
designed to integrate well with the new graybird theme. 

The installation slide show has been updated for Natty Narwhal, and
really displays the best of Xubuntu. 

The Elementary Xubuntu icon theme has been updated. 

Xubuntu is using the Droid font by default, since it is a lightweight,
good visibility font. 

The newly released Xfce 4.8 is included. The menus in Xfce 4.8 are now
editable with any menu editor that meets the freedesktop.org standards.
The suggested editor is alacarte. 


Edubuntu
--------

You can test Edubuntu 11.04 directly from your web browser by going at
[http://www.edubuntu.org/weblive](http://www.edubuntu.org/weblive) 

WebLive is also directly integrated in the Ubuntu Software Center
letting you test the most popular apps without installing them on your
machine. Just click the "Test drive" button. 

Ubiquity now has an additional step allowing users to fine-tune which
applications should be installed on the final system. 

Edubuntu now ships with Arkose, which provides application sandboxing
for downloaded apps. 

New software packages in Edubuntu include Pencil, Geogebra, Calibre,
LibreCAD, Freemind and Stellarium. 

Theming improvements include a new LDM theme when installing LTSP from
the Edubuntu installer. The text-mode boot mode now displays "Edubuntu"
instead of "Ubuntu". Our ongoing menu refinements include new icons
where they were missing, and more consistent case use in menu entries. 

Edubuntu 11.04 ships with the classical Gnome desktop by default but
Unity is available as an option in the installer.

For more details on what has changed in Edubuntu 11.04, please refer to
[http://edubuntu.org/2011-03-03/edubuntu-1104-beta-1-released](http://edubuntu.org/2011-03-03/edubuntu-1104-beta-1-released) 

        
Ubuntu Studio
-------------

The task selections during installation have been updated. The audio
tasks have been parsed into two groups: generation and recording. 

Currently, Ubuntu Studio is shipping the -generic kernel. We are working
with the Ubuntu Kernel Team to get a -low latency kernel into the
archives.  An interim -lowlatency kernel is available in Allesio
Bogani's PPA. 

network-manager has replaced gnome-network-admin.  

The packages shipped in Ubuntu Studio are now more focused to support
identified tasks and their derived work flows. 

Ubuntu Studio does not currently use Unity. As the user logs in it will
default to Gnome Classic Desktop (i.e. Gnome2). 


Mythbuntu
---------

The Mythbuntu-bare (Backup and Restore for the database and
configuration files) Mythbuntu Control Center plugin now has the 
ability to schedule backups on a daily, weekly, or monthly basis. 

Android and iOS devices can now be used as remote controls. 

MythTV 0.24 is now integrated into the builds. 



Please see [http://www.ubuntu.com/testing/natty/beta](http://www.ubuntu.com/testing/natty/beta) for more details on
the above products.


About Ubuntu
------------

Ubuntu is a full-featured Linux distribution for desktops, laptops, and
servers, with a fast and easy installation and regular releases.  A
tightly-integrated selection of excellent applications is included, and
an incredible variety of add-on software is just a few clicks away.

Professional technical support is available from Canonical Limited and
hundreds of other companies around the world.  For more information
about support, visit [http://www.ubuntu.com/support](http://www.ubuntu.com/support) .


To Get Ubuntu 11.04 Beta 1
------------------------

To upgrade to Ubuntu 11.04 Beta 1 from Ubuntu 10.10, follow 
these instructions:

  [https://help.ubuntu.com/community/NattyUpgrades](https://help.ubuntu.com/community/NattyUpgrades)

Or, download Ubuntu 11.04 Beta 1 images from a location near you: 

  [http://www.ubuntu.com/testing/download](http://www.ubuntu.com/testing/download) (Ubuntu and Ubuntu Server) 

In addition, they can be found at the following links:  

[http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/) (Ubuntu, Ubuntu Server) 
[http://cdimage.ubuntu.com/releases/natty/beta-1/](http://cdimage.ubuntu.com/releases/natty/beta-1/) (Ubuntu DVD, source) 
[http://uec-images.ubuntu.com/releases/natty/beta-1/](http://uec-images.ubuntu.com/releases/natty/beta-1/) (Ubuntu Server EC2) 
[http://cdimage.ubuntu.com/ubuntu-netbook/releases/natty/beta-1/](http://cdimage.ubuntu.com/ubuntu-netbook/releases/natty/beta-1/) (Ubuntu Netbook ARM) 
[http://cdimage.ubuntu.com/netboot/11.04/beta-1/](http://cdimage.ubuntu.com/netboot/11.04/beta-1/) (Ubuntu Netboot) 
[http://releases.ubuntu.com/kubuntu/natty/](http://releases.ubuntu.com/kubuntu/natty/) (Kubuntu) 
[http://cdimage.ubuntu.com/kubuntu/releases/natty/beta-1/](http://cdimage.ubuntu.com/kubuntu/releases/natty/beta-1/) (Kubuntu DVD, preinstalled ARM images) 
[http://cdimage.ubuntu.com/xubuntu/releases/natty/beta-1/](http://cdimage.ubuntu.com/xubuntu/releases/natty/beta-1/) (Xubuntu) 
[http://cdimage.ubuntu.com/edubuntu/releases/natty/beta-1/](http://cdimage.ubuntu.com/edubuntu/releases/natty/beta-1/) (Edubuntu) 
[http://cdimage.ubuntu.com/ubuntustudio/releases/natty/beta-1/](http://cdimage.ubuntu.com/ubuntustudio/releases/natty/beta-1/) (Ubuntu Studio) 
[http://cdimage.ubuntu.com/mythbuntu/releases/natty/beta-1/](http://cdimage.ubuntu.com/mythbuntu/releases/natty/beta-1/) (Mythbuntu) 
    
The final version of Ubuntu 11.04 is expected to be released in April 2011.


Feedback and Participation
--------------------------

If you would like to help shape Ubuntu, take a look at the list of ways
you can participate at:

  [http://www.ubuntu.com/community/participate/](http://www.ubuntu.com/community/participate/)


Your comments, bug reports, patches and suggestions will help turn this
Beta into the best release of Ubuntu ever.  Please note that, where
possible, we prefer that bugs be reported using the tools provided,
rather than by visiting Launchpad directly.  Instructions can be 
found at:

  [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)


If you have a question, or if you think you may have found a bug but are
not sure, first try asking on the #ubuntu IRC channel on freenode, on 
the Ubuntu Users mailing list, or on the Ubuntu forums:

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-users](http://lists.ubuntu.com/mailman/listinfo/ubuntu-users)
  [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)



---

### Post by andrewabc on 2011-03-31
For those looking for Lubuntu beta since lubuntu website never mentions alpha/beta etc, and not included in release notes of ubuntu:
[http://people.ubuntu.com/~gilir/](http://people.ubuntu.com/~gilir/)

If you use/test lubuntu, might as well bookmark that link.

---

### Post by kansasnoob on 2011-04-01
I'd recommend everyone take a few minutes to browse the release notes:

[http://www.ubuntu.com/testing/natty/beta](http://www.ubuntu.com/testing/natty/beta)

Particularly the "known issues" :)

---

### Post by MacUntu on 2011-04-01
Farewell, good old 8.10 &#8594; 9.04 &#8594; 9.10 &#8594; 10.04 &#8594; 10.10 &#8594; 11.04 dev installation on my main rig! Beta 1 came right for a fresh start and everything's running fine. :)

---

### Post by isaacahloe on 2011-04-01
damn i knew i shouldn't have upgraded. now my session randomly logs out. enough that i haven't been able to input a bug report before it logs out/crashes. i'm going to hit post before it logs out again and try to do a bug report again.

---

### Post by juancarlospaco on 2011-04-01
Meh, any Tk program crash the entire Unity desktop ...

---

### Post by giant420 on 2011-04-01
> **isaacahloe said:**
> damn i knew i shouldn't have upgraded. now my session randomly logs out. enough that i haven't been able to input a bug report before it logs out/crashes. i'm going to hit post before it logs out again and try to do a bug report again.
Are you by chance using a laptop with a touchpad? If so, I have having the same issue and a fix has already been released. Check out this thread: [http://ubuntuforums.org/showthread.php?t=1719087](http://ubuntuforums.org/showthread.php?t=1719087)

---

### Post by cariboo on 2011-04-01
This thread really isn't the place to post about problems, as this one will soon disappear when I unstick it.

---

### Post by ikt on 2011-04-01
upgraded and everything is working fine except for proprietary ati drivers.

Considering how buggy the alphas were that's a pretty good upgrade experience if you ask me.

---

### Post by isaacahloe on 2011-04-01
> **giant420 said:**
> Are you by chance using a laptop with a touchpad? If so, I have having the same issue and a fix has already been released. Check out this thread: [http://ubuntuforums.org/showthread.php?t=1719087](http://ubuntuforums.org/showthread.php?t=1719087)
yep, i tried searching forums but didn't realize it was the touchpad as i have a mouse attached as well, but i guess i sometimes use the trackpad. also i couldn't search very long as it would log out, and same problem with reporting the bug.

natty is looking good.  i noticed some programs are buggy in natty like nicotine and audacity but i expect those will be ironed out soon enough as they are popular applications. also sometimes there is still unexpected behavior from the launcher's hiding stuff.

i like the new icon for the launcher and the shortcuts for places, switcher, and trash

kde apps now stay pinned which is cool

design wise my only problem is that the workspace switcher is a bit hard to get to when you have a lot of apps pinned. i've seen some good mockups that deal with this but it's not a big enough deal that i'm not completely please anyways as i use ctrl+s anyways now

the last few iterations of unity have sped up my workflow quite a bit.

---

### Post by bigsmitty64 on 2011-04-01
I've tried installing this (11.04 32 bit) 3 times now. First time I got a bunch of errors before the live cd even loaded. I don't remember what it said but it filled the screen with white auto scrolling text on the black screen.

Second time, (fresh download, burnt to cd at slowest speed) Same thing.

Third time I got to the desktop, but it was asking for a username and password? On the live cd? I looked around here and found a few possible answers (for the username and password thing) of which none worked. Anyone have any idea what I'm doing wrong?

I've tested every release from Karmic on, and never ran into this. Any help is greatly appreciated. Thanks in advance.

---

### Post by kansasnoob on 2011-04-01
> **andrewabc said:**
> For those looking for Lubuntu beta since lubuntu website never mentions alpha/beta etc, and not included in release notes of ubuntu:
[http://people.ubuntu.com/~gilir/](http://people.ubuntu.com/~gilir/)

If you use/test lubuntu, might as well bookmark that link.

Thanks for that. I hope to see Lubuntu becoming a full fledged member of the Ubuntu family soon!

Not knowing what to expect for sure with Gnome3 on the horizon I've been looking at alternatives and Lubuntu tops the list ATM :)

I'd definitely add Lubuntu to my iso-testing itinerary. It's becoming a real shining star.

---

### Post by jerrylamos on 2011-04-01
> **bigsmitty64 said:**
> Third time I got to the desktop, but it was asking for a username and password? On the live cd?

Every time I've had that username and password bug it was some problem with the CD.

Are you burning the CD on the same pc that you're trying to boot?

I had to boot three times on two separate CD's on this pc before I got a successful boot and install.  Do note the CD's were burnt on a different pc, so next time I'll transfer the .iso to this one to burn on the same drive I boot on.

The same CD worked fine first time on my newest pc, of course the one that had made the CD.

I had to try about four times to get my Thinkpad T40 to boot and install.  The T40 couldn't do the "try ubuntu" but would do the install.  Someone on the forums says their T40 ran O.K.

I have no clue.  I was able to get there eventually.  Do note a CD from early March booted and installed first time on all three of these pc's.

Jerry

p.s. I assume you've done MD5SUM on the .iso, and on first booting on the same pc there is an option to check the CD for errors...if I suspect trouble I do that.

---

### Post by bigsmitty64 on 2011-04-01
> **jerrylamos said:**
> every time i've had that username and password bug it was some problem with the cd.

**i thought that to at first so i tried 3 separate downloads on 3 separate cd's **

are you burning the cd on the same pc that you're trying to boot?

**yes sir i am.**

p.s. I assume you've done md5sum on the .iso, and on first booting on the same pc there is an option to check the cd for errors...if i suspect trouble i do that.

**yes sir again!** **on the md5sum, although i didn't get the option to check the cd.**

:p

---

### Post by andrewabc on 2011-04-01
I burned lubuntu, and ran livecd. It loaded somewhat and came to text prompt. I eventually figured out that typing
start lxdm
started the session and showed the desktop. Am now testing it and putting onto liveusb. Liveusb works fine, didn't get text prompt.

Thought I'd share in case someone ended up with similar problem.

---

### Post by cariboo on 2011-04-01
Everybody now seems to be aware that Beta 1 has been officially released, I'm going to unstick this thread.

---

