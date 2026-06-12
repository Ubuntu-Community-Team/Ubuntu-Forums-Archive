---
title: "Terminal Service Client and Card Reader Login"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by randyklein99 on 2009-04-11
I'm trying to login to my work computer.  It requires first a VPN with a DOD CAC using a card reader and pin. Then a remote desktop connection using the same CAC and pin. 

I have successfully followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=564763") to establish a VPN connection through a web-based Cisco anyconnect.  

But all my attempts at a remote desktop connection failed because I don't have the option of logging in with the CAC and pin.  

The only google searches I have found that address this problem is this [one]("http://symbolik.wordpress.com/2007/02/25/smartcards-dod-cac-and-rdp-with-rdesktop-15x/"). 

But I'm new to linux, so I may not be following the guide that well.  I especially don't know what step 2 is all about. 

Any ideas?

---

### Post by randyklein99 on 2009-04-21
So I finally figure it out, or all my random tinkering since the OP did it by magic.  But I think what made it work was the following interpretation to the second hyper link in the OP:
1. downloaded the rdesktop to /usr/local/src instead of /home
2. a -- looks like a long dash in my browser

Those two things seemed to do the trick.  So now I can rdesktop -r scard server just fine.

And if anyone reading this knows knows, must you download files into that directory?

---

### Post by randyklein99 on 2009-04-21
Also, is there a way to integrate the "-r scard" parameter in the Terminal Server Client?

---

### Post by randyklein99 on 2009-04-29
Ok, I think I have figured it out.  Apparently it was the random tinkering that did it and not what I mentioned above.  But I have been able re-tinker the randomness after a clean install of Jaunty.  

Hopefully this isn't only my application-specific instructions.  But if it is, rest assured that this will allow you to VPN into AFIT's servers and then rdesktop to one of the terminal servers using only your DoD CAC and pin.

And since this seems to be a thread to only me and myself, I imagine no one will mind me laying out the steps here so I can re-do again in the future.

The steps are a compilation from two websites:
[http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/]("http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/")
[http://symbolik.wordpress.com/2007/02/25/smartcards-dod-cac-and-rdp-with-rdesktop-15x/]("http://symbolik.wordpress.com/2007/02/25/smartcards-dod-cac-and-rdp-with-rdesktop-15x/")

And just in case these links ever die, here's what they say (with the appropriate credit due):


> #  Download the following tarball files and extract them (tar xvfz filename.tar.gz):

    * libusb - Project URL:&#8221;[http://libusb.sourceforge.net/&#8221;](http://libusb.sourceforge.net/&#8221;)
    * pcsc-lite - Project URL:&#8221;[http://pcsclite.alioth.debian.org/&#8221;](http://pcsclite.alioth.debian.org/&#8221;)
    * pcsc-tools - Project URL:&#8221;[http://ludovic.rousseau.free.fr/softwares/pcsc-*tools/&#8220;](http://ludovic.rousseau.free.fr/softwares/pcsc-*tools/&#8220;)
    * ccid - Project URL:&#8221;[http://pcsclite.alioth.debian.org/ccid.html&#8220;](http://pcsclite.alioth.debian.org/ccid.html&#8220;)
    * CoolKey - Project URL:&#8221;[http://directory.fedora.redhat.com/wiki/CoolKey&#8220;](http://directory.fedora.redhat.com/wiki/CoolKey&#8220;)

# Make the install directories, along with a critical build-time directory - &#8220;mkdir -p /usr/cac/lib/pkgconfig&#8221;
# Set the build variable - &#8220;declare -x PKG_CONFIG_PATH=/usr/cac/lib/pkgconfig&#8221; - this is only needed for building, not later using these tools.
# Change to the respective directories and configure/make/make install:

    * cd libusb0.1.12 && ./configure &#8211;prefix=/usr/cac && make && make install, then cd up one directory
    * cd pcsclite1.4.0 && ./configure &#8211;prefix=/usr/cac && make && make install, then cd up one directory
    * cd pcsctools1.4.8 && edit &#8220;Makefile&#8221; - change &#8220;DESTDIR&#8221; to &#8220;/usr/cac&#8221; && make && make install, then cd up one directory
    * cd ccid1.2.1 && ./configure &#8211;prefix=/usr/cac && make && make install, then cd up one directory
    * cd coolkey-1.1.0 && ./configure &#8211;prefix=/usr/cac && make && make install, then cd up one directory


> In continuing to integrate CAC into Linux, I went to the RDesktop SourceForge CVS website, followed the cvs download directions (using &#8220;rdesktop&#8221; as the modulename), and downloaded the latest version of rdesktop, which is supposed to have smartcard reader support. This piggybacks off of the installation of the CAC reader software in the previous post.

Once downloaded, cd to the rdesktop directory and do the following:

   1. Run the command &#8220;declare -x PKG_CONFIG_PATH=/usr/cac/lib/pkgconfig&#8221;
   2. &#8220;./configure &#8211;prefix=/usr/cac &#8211;enable-smartcard&#8221; - look for the line, &#8220;checking for PCSCLITE:&#8221; - it should say &#8220;yes&#8221; (thanks to the previous &#8220;declare&#8221; command)
   3. make && make install
   4. Run with &#8220;rdesktop -r scard <remote IP>:<remote port>


Also, keep in mind that I did this after following the instructions on this [link]("https://help.ubuntu.com/community/CommonAccessCard"). So I have no idea if the following is redundant or overwrites what I previously did. Hopefully someone else can figure that out.

Now for the nifty code stuff that I actually ran after extracting all the files to their directories in my home/user directory (with updated version numbers than in the above quotes):

```

sudo mkdir -p /usr/cac/lib/pkgconfig

```

```

declare -x PKG_CONFIG_PATH=/usr/cac/lib/pkgconfig

```

```

cd libusb-1.0.0 && ./configure --prefix=/usr/cac && make && sudo make install && cd

```

```

cd pcsc-lite-1.5.3 && ./configure --prefix=/usr/cac && make && sudo make install && cd

```


```

cd pcsc-tools-1.4.15 && gedit Makefile

****Not code but text changes inside Makefile**** 
change &#8220;DESTDIR&#8221; to &#8220;/usr/cac&#8221;
****code continues****

./configure --prefix=/usr/cac && make && sudo make install && cd

```

```

cd ccid-1.3.10 && ./configure --prefix=/usr/cac && make && sudo make install && cd

```

```

cd coolkey-1.1.0 && ./configure --prefix=/usr/cac && make && sudo make install && cd

```

```

cd rdesktop-1.6.0 && declare -x PKG_CONFIG_PATH=/usr/cac/lib/pkgconfig && ./configure --prefix=/usr/cac --enable-smartcard && make && sudo make install && cd

```

That's it.  If you then VPN in and run:
```
rdesktop -r scard <remote IP>:<remote port>
```
you should have CAC login ability to a terminal server.

Or for a full-screen (toggle with CTRL - ALT - ENTER):
```
rdesktop -fr scard <remote IP>:<remote port>
```

Also, I found out that in order to get my VPN with Cisco Anyconnect working, I needed the latest JRE and java plugin:
```

sudo apt-get install sun-java6-jre sun-java6-plugin

```

Otherwise the Anyconnect would just sit there and then fail.

Well, hopefully I have properly captured the random tinkering I did to accomplish this from a fresh install.  And if anyone else reads this thread with a similar problem, I hope it works for you.

---

### Post by randyklein99 on 2009-07-04
Update:

The Cisco AnyConnect does not work with 64 bit ubuntu, since there doesn't seem to be a 64bit AnyConnect.  However, there seems to be a work around using a 32 bit Firefox, but I haven't tried that yet.

---

### Post by derAuslander on 2009-07-09
Thanks for your excellent write up and work. I'm currently working on getting this all to work in Ubuntu 9.04 and I'll edit this post with my findings.

Just wanted to let you know that someone is paying attention.

---

### Post by particle02 on 2009-08-22
I'm also trying to get this to work on 9.04.  I have my CAC working with Firefox, but not with AnyConnect client or the web-based VPN service.  I was hoping randyklein99 might be able to help me out.  I just started at AFIT.  Thanks for your help.

---

### Post by randyklein99 on 2009-08-23
If you're using 64 bit, I haven't figured out a way yet.  Not that there isn't a way, I just haven't explored it yet.  

Let me know if you're using 64 or 32 bit 9.04

---

### Post by particle02 on 2009-08-23
I'm using 32-bit 9.04.

I have the anyconnect software installed from the web-based vpn server.  When I launch it I get the screen asking for the IP address.  I use the one I found in the .PCF file for VPN access (ends with 246.249).  It then pops a warning with Certificate information and the message: "Warning: The following Certificate received from the Server could not be verified:".  I click accept.  It then gives the following error "Certificate Validation Error" at the bottom of the window.  I have tried to send stderr and stdout to a file, but it is always blank.  I do have Java installed.

When I try to use the web-based SSL VPN, everything works fine until I try to connect to one of the servers with RDP.  It pops up a window asking to select a certificate (looks like a java pop-up) but doesn't list any certs.

Thanks for your help.

---

### Post by randyklein99 on 2009-08-23
So have you compiled rdesktop with smart card enabled?  And if so, are you sure you are running the compiled version and not the previous one?

---

### Post by particle02 on 2009-08-23
I'm having problems getting all the parts to compile, but my problem is even before that.

I can't get AnyConnect to connect to the VPN.  Does the AnyConnect software somehow depend on the newer version of rDesktop?  I thought you needed to get AnyConnect to create the VPN tunnel first, then use rDesktop to connect to the server.

I'm working on getting the newer rDesktop compiled.  Am I confusing the process?  I thought it looked like this:

Launch AnyConnect --> Create VPN using CAC Cert --> Launch rDesktop --> Connect to Terminal server with CAC Cert

I will post an update when I get rDesktop compiled.  Thanks again for your help.

---

### Post by particle02 on 2009-08-23
Yes, I have rdesktop with smart card enabled and I'm running the correct one.  The problem is that I can't get the Cisco AnyConnect VPN Client to connect to the AFIT servers.  I keep getting the error message "Certificate Validation Error".  I have Java installed.  Any ideas?  Thanks.

---

### Post by randyklein99 on 2009-08-24
The only way I've connected with VPN is via the AnyConnect/AFIT website, not the client software.  I have noticed that sometimes I need to restart Firefox before I do that though.

Is that what you're trying or are you trying with client version?

---

### Post by particle02 on 2009-08-26
After some trial and error, I have figured out how the system works (still doesn't work for me, but at least I know how it is suppose to work.  The client software needs to be activated by the website (website passes the CAC certs to client).  I have been able to get this to work on two different computers with the 9.04 Live CD and the Cruncheee 8.10 Live CD.  However, once I have either of them installed on the machine, I get an error in Java when I try to launch the AnyConnect web app.  The Java error is below.  I have done some google searches on this "magic number" problem and it seems to be a server side issue.  However, since I had it working on the Live CDs and you seem to be able to get it to work, I'm at a loss.  I have tried clean installs of Ubuntu 9.04 (without running any updates) and it still gives the same error.  Did you run across this issue at all?  I'm trying to figure out what is different between the Live CD and a fresh install.  I might open a new thread on that topic.  Thanks again for your help.

Also, do you have wireless access on your linux machine at AFIT?  It seems the policy is not to give wireless access to linux boxes.


Error from Java:
java.lang.ClassFormatError: Incompatible magic value 1013478509 in class file VPNJava/VPNJava
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
    at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:140)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:417)
    at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2866)
    at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1395)
    at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.ClassFormatError: Incompatible magic value 1013478509 in class file VPNJava/VPNJava

---

### Post by randyklein99 on 2009-08-27
It's been a while since I set this up, but I remember getting errors and/or just not working problems when trying the web app anyconnect.  But everything worked after I installed the java jre and java plugin.

---

### Post by butsam on 2009-09-16
Thanks for this post! I am on 64-bit, and got the Cisco AnyConnect *client* to work by patching. I *cannot* configure the client to use my CAC card, though, even though my CAC card works in Firefox. I am not sure how I need to edit the PCF Configuration file to give it the needed secret sauce to use my CAC instead of the default. (I am also at AFIT, so I have that PCF file.)

Any thoughts? I may just have to go with 32-bit Firefox and use the web-based version, it looks like...how do you get to the web-based version?

---

### Post by randyklein99 on 2009-09-18
Well I'm no longer at AFIT, but I'll try to help.  The web-based version is installed via a flash application (why the java plugin needs to be installed) when you visit the vpn.afit.edu website. But if you don't have a 32-bit browser, the flash install will fail and offer you the client instead via download.  Of course, all the certificates must be already installed in Firefox.

---

