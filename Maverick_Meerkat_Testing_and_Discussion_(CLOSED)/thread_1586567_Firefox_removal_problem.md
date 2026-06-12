---
title: "Firefox removal problem"
date: 2010-10-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ankspo71 on 2010-10-02
Hello,
I just installed Kubuntu 10.10 RC (clean install) about an hour ago so I could see if the install process of grub2 was fixed (and it is). Then I installed sun-java6-plugin and sun-java6-jre which brought in Firefox (firefox_3.6.10+build1+nobinonly-0ubuntu3_i386). Well, I didn't want to have firefox 3.6.10 installed this time, but I installed java anyways figuring I could simply remove firefox later. (I prefer to use firefox4 beta because it is more compatible with specific sites that I visit frequently.)

Here is the results of the command "sudo apt-get remove firefox":
```

james@Kubuntu:~$ sudo apt-get remove firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="DarkRed"]The following extra packages will be installed:
  epiphany-browser epiphany-browser-data evince evince-common gir1.0-atk-1.0 gir1.0-clutter-1.0 gir1.0-freedesktop gir1.0-gdkpixbuf-2.0 gir1.0-gstreamer-0.10 gir1.0-gtk-2.0 gir1.0-json-glib-1.0 gir1.0-pango-1.0
  gnome-doc-utils gnome-icon-theme gnome-js-common gnome-user-guide launchpad-integration libavahi-gobject0 libclutter-1.0-0 libcroco3 libevdocument3 libevview3 libkpathsea5 liblaunchpad-integration1 libnautilus-extension1
  libpoppler-glib5 librarian0 librsvg2-2 librsvg2-common libseed0 libt1-5 libwebkit-1.0-2 libwebkit-1.0-common python-libxml2 rarian-compat scrollkeeper xsltproc xulrunner-1.9.2 yelp[/COLOR]
Suggested packages:
  poppler-data nautilus konqueror librsvg2-bin
The following packages will be REMOVED:
  firefox firefox-branding
[COLOR="DarkRed"]The following NEW packages will be installed:
  epiphany-browser epiphany-browser-data evince evince-common gir1.0-atk-1.0 gir1.0-clutter-1.0 gir1.0-freedesktop gir1.0-gdkpixbuf-2.0 gir1.0-gstreamer-0.10 gir1.0-gtk-2.0 gir1.0-json-glib-1.0 gir1.0-pango-1.0
  gnome-doc-utils gnome-icon-theme gnome-js-common gnome-user-guide launchpad-integration libavahi-gobject0 libclutter-1.0-0 libcroco3 libevdocument3 libevview3 libkpathsea5 liblaunchpad-integration1 libnautilus-extension1
  libpoppler-glib5 librarian0 librsvg2-2 librsvg2-common libseed0 libt1-5 libwebkit-1.0-2 libwebkit-1.0-common python-libxml2 rarian-compat scrollkeeper xsltproc xulrunner-1.9.2 yelp
0 upgraded, 39 newly installed, 2 to remove and 0 not upgraded.
Need to get 33.3MB of archives.[/COLOR]
After this operation, 63.7MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

Could it be that the Sun Java packages requires that some sort of GTK browser needs to be installed? Hmm, I'll be back to see if removing Sun Java6 will allow me to remove firefox later without adding a bunch of depends.

PS. I can live with firefox 3.6 installed on my system, it's just that I want to find out why the removal process wants to install a bunch of packages, so I can report a bug.

---

### Post by ankspo71 on 2010-10-02
Hi Again,

Okay, I am getting somewhere. Removal of sun-java6-jre and sun-java6-plugin and then later removing firefox worked (but now I don't have java lol)
```

james@Kubuntu:~$ sudo apt-get remove sun-java6-plugin sun-java6-jre
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  java-common unixodbc
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  sun-java6-bin sun-java6-jre sun-java6-plugin
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 103MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 92549 files and directories currently installed.)
Removing sun-java6-plugin ...
Removing sun-java6-bin ...
Removing sun-java6-jre ...
Processing triggers for menu ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'virtual/bluedevil-input'

Unknown media type in type 'virtual/bluedevil-audio'

Unknown media type in type 'virtual/bluedevil-sendfile'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'
                                                                                                                                                                                                                                 
Unknown media type in type 'fonts/package'                                                                                                                                                                                       
                                                                                                                                                                                                                                 
Unknown media type in type 'interface/x-winamp-skin'                                                                                                                                                                             
                                                                                                                                                                                                                                 
james@Kubuntu:~$ sudo apt-get autoremove
Reading package lists... Done                                                                                                                                                                                                    
Building dependency tree                                                                                                                                                                                                         
Reading state information... Done                                                                                                                                                                                                
The following packages will be REMOVED:                                                                                                                                                                                          
  java-common unixodbc                                                                                                                                                                                                           
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.                                                                                                                                                                   
After this operation, 1,065kB disk space will be freed.                                                                                                                                                                          
Do you want to continue [Y/n]? y                                                                                                                                                                                                 
(Reading database ... 91639 files and directories currently installed.)                                                                                                                                                          
Removing java-common ...                                                                                                                                                                                                         
Removing unixodbc ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
[COLOR="Blue"]james@Kubuntu:~$ sudo apt-get remove firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox firefox-branding
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 30.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 91575 files and directories currently installed.)
Removing firefox ...
Removing firefox-branding ...
Processing triggers for menu ...
james@Kubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libstartup-notification0 libxcb-event1 ubufox xul-ext-ubufox
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 549kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 91316 files and directories currently installed.)
Removing libstartup-notification0 ...
Removing libxcb-event1 ...
Removing ubufox ...
Removing xul-ext-ubufox ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place[/COLOR]
james@Kubuntu:~$
```

---

### Post by ankspo71 on 2010-10-02
Hello again,
I do believe I found the reason for my original firefox removal problem (see the code below to see depends of sun-java6-plugin). Hmm... I wonder if symlinking the firefox4.0 executable to /usr/bin/firefox will trick Java into thinking I have firefox3 installed. Wouldn't it be better to have sun-java6-plugin NOT require a browser though... to make our custom installations a little easier? If not, why isn't Rekonq  listed as an optional depend (for Kubuntu 10.10 users)? I still have Rekonq installed btw.

```
james@Kubuntu:~$ apt-cache show sun-java6-plugin
Package: sun-java6-plugin
Source: sun-java6
Priority: optional
Section: web
Installed-Size: 60
Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 6.21-1ubuntu1
[COLOR="DarkRed"]Depends: libasound2, libx11-6, libxext6, libxi6, libxtst6, sun-java6-bin (>= 6.21-1ubuntu1), firefox | firefox-2 | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epiphany-gecko | epiphany-webkit | epiphany-browser | galeon | midbrowser | moblin-web-browser | xulrunner | xulrunner-1.9 | konqueror | chromium-browser | midori[/COLOR]
Filename: pool/partner/s/sun-java6/sun-java6-plugin_6.21-1ubuntu1_i386.deb
Size: 1854
MD5sum: 90d96885d364cdc577b7681bc008280c
SHA1: 066a7752b905a8a52e54095fbf185bd9da97e2ce
Description: The Java(TM) Plug-in, Java SE 6
 Java Plug-in enables applets written to the Java Platform 6
 specification to be run in Mozilla and other web browsers.
 Java Plug-in comes with the Java Runtime Environment (JRE).
 .
 This is a metapackage containing dependencies for running Java in
 various browsers.
Npp-Mimetype: application/x-java-vm, application/x-java-applet, application/x-java-applet;version=1.1, application/x-java-applet;version=1.1.1, application/x-java-applet;version=1.1.2, application/x-java-applet;version=1.1.3, application/x-java-applet;version=1.2, application/x-java-applet;version=1.2.1, application/x-java-applet;version=1.2.2, application/x-java-applet;version=1.3, application/x-java-applet;version=1.3.1, application/x-java-applet;version=1.4, application/x-java-applet;version=1.4.1, application/x-java-applet;version=1.4.2, application/x-java-applet;version=1.5, application/x-java-applet;version=1.6, application/x-java-applet;jpi-version=1.6.0_07, application/x-java-bean, application/x-java-bean;version=1.1, application/x-java-bean;version=1.1.1, application/x-java-bean;version=1.1.2, application/x-java-bean;version=1.1.3, application/x-java-bean;version=1.2, application/x-java-bean;version=1.2.1, application/x-java-bean;version=1.2.2, application/x-java-bean;version=1.3, application/x-java-bean;version=1.3.1, application/x-java-bean;version=1.4, application/x-java-bean;version=1.4.1, application/x-java-bean;version=1.4.2, application/x-java-bean;version=1.5, application/x-java-bean;version=1.6, application/x-java-bean;jpi-version=1.6.0_07
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a
Npp-Name: The Java(TM) Plug-in, Java SE 6

james@Kubuntu:~$ 
```

---

### Post by ankspo71 on 2010-10-02
Hi again,
Nope, symlinking firefox4 executable to /usr/bin/firefox is NOT enough to trick sun-java6-plugin into thinking firefox (3.6.10) is installed.

Does anybody know if sun-java6-jre (without the plugin) is enough to run browser java applets in firefox4? 

Anyways, I'm going to file a bug later today and request that Rekonq be included as an optional dependency in sun-java6-plugin for us Kubuntu 10.10 users, if it isn't already reported I mean. Or maybe request that they do not list browsers as dependencies just like they don't for openjdk.

---

### Post by ronacc on 2010-10-02
what the sun-java6-plugin depends on  is ANY one of the browsers that are in the REPOS ,  Konq would satisfy that dependency or FF3.6 or epiphany but not FF4 or Opera . open synaptic click on sun-java6-plugin then right lcick and select properties then dependencies .

---

### Post by xebian on 2010-10-02
They  should have made it a recommend.

Anyway, you can rebuild it to not depend or just get the java from Sun.

---

### Post by ankspo71 on 2010-10-02
> **ronacc said:**
> what the sun-java6-plugin depends on  is ANY one of the browsers that are in the REPOS ,  Konq would satisfy that dependency or FF3.6 or epiphany but not FF4 or Opera . open synaptic click on sun-java6-plugin then right lcick and select properties then dependencies .


Hi Ronacc,
Yes, you're right. The only trouble is sun-java6-plugin does not have Rekonq listed as a browser dependency. Rekonq is the browser that replaced Konq in Kubuntu 10.10. I could install firefox 3.6 or Konq just to satisfy Java, but I already have a browser installed (Rekonq) that Kubuntu gave me. Edit: I have installed Konqueror to satisfy the dependencies for now. Thanks.

---

### Post by ankspo71 on 2010-10-02
> **xebian said:**
> They  should have made it a recommend.

Anyway, you can rebuild it to not depend or just get the java from Sun.

Hi Xebian,
Those ideas are what I was thinking I could have done too. I also checked out the Sun Java6 community PPA and the dependencies don't list Rekonq as a browser there either. I have already installed Konqueror to satisfy java for now. Thanks for the advice.

---

### Post by ronacc on 2010-10-02
> **ankspo71 said:**
> Hi Ronacc,
Yes, you're right. The only trouble is sun-java6-plugin does not have Rekonq listed as a browser dependency. Rekonq is the browser that replaced Konq in Kubuntu 10.10. I could install firefox 3.6 or Konq just to satisfy Java, but I already have a browser installed (Rekonq) that Kubuntu gave me. Edit: I have installed Konqueror to satisfy the dependencies for now. Thanks.

unless there is a problem with disk space tou can have more than one browser installed , right now I have FF3.6 , 
ff4.0 , Opera 10.62 , Opera 10.70 (beta) , epiphany, galeon , chromium and chrome ( plus a couple others ) all coexisting more or less peacefully .

---

