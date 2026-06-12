---
title: "ShrewSoft VPN 1.7.1 Compiling"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by Webnet on 2013-02-19
[This thread]("http://ubuntuforums.org/showthread.php?p=12518509") contains outdated information about compiling ShrewSoft VPN with libqt3. I'm needing to set this up as well. I found resources telling me to setup 

```
sudo apt-get install libqt4-dev
```
but that package wasn't found. Here's my command log:

```
user@ubuntu:~/Programs/ShrewSoft VPN$ cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DQTGUI=YES -DETCDIR=/etc -DNATT=YES
-- The CXX compiler identification is unknown
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Using install prefix /usr/local ...
-- Using etc path /etc ...
-- Using lib path /usr/local/lib ...
-- Using man path /usr/local/man ...
-- Using binary /usr/bin/flex ...
-- Using binary /usr/bin/bison ...
-- Enabled NAT Traversal support ...
-- Could NOT find Qt3 (missing:  QT_QT_LIBRARY QT_INCLUDE_DIR QT_MOC_EXECUTABLE) 
CMake Error at CMakeLists.txt:423 (message):
  Unable to locate required package : QT
```
What package do I need in order to compile Shrewsoft VPN? One person said I could use
Code:
```
sudo apt-get install ike
```
Of course that didn't work either :-\

---

### Post by chili555 on 2013-02-19
I know nothing about ShrewSoft but I know a thing or two about compiling. Where did you download the package? I looked up 'ShrewSoft' and the latest version on their site is 2.1.7 dated late 2010. The answer to how you can compile that is as soon as you install Ubuntu 10.04 or so. It's too old to compile correctly on a recent kernel.> One person said I could use
```
sudo apt-get install ike
```

Of course that didn't work either :-\ What about ike-scan?> ike-scan discovers IKE hosts and can also fingerprint them using the
retransmission backoff pattern.

ike-scan does two things:

a) Discovery: Determine which hosts are running IKE.
   This is done by displaying those hosts which respond to the IKE requests
   sent by ike-scan.
   .
b) Fingerprinting: Determine which IKE implementation the hosts are using.
   This is done by recording the times of the IKE response packets from the
   target hosts and comparing the observed retransmission backoff pattern
   against known patterns.
   .
   The retransmission backoff fingerprinting concept is discussed in more
   detail in the UDP backoff fingerprinting paper which should be included
   in the ike-scan kit as udp-backoff-fingerprinting-paper.txt.I don't know what you are trying to accomplish, so I have no idea if this is suitable.

---

### Post by Webnet on 2013-03-05
Sorry for my lack of reply.  I'm trying to setup Shrewsoft VPN so I can connect my work's VPN and work remotely while in Linux.  *ike-scan* looks like something different than what I'm looking for.

I downloaded the software here: [http://www.shrew.net/download/ike](http://www.shrew.net/download/ike)

I don't remember where I got this document, but this is from the linux install instructions:

[SIZE=4][B]IPSec Client Installation

[/B][/SIZE]
[SIZE=2]**Download and Install Software Dependencies**[/SIZE]
The following packages are required for installing the Shrew Soft VPN Client:
&#8226; GCC (or c++ compiler)
&#8226; Stock C libraries
&#8226; Stock C Includes
&#8226; Pthread support
&#8226; Lex (or flex)
&#8226; Bison 2.3 (or higher)
&#8226; Cmake 2.4 (or higher)
&#8226; Openssl 0.9.x
&#8226; Qt (only required for GUI)


To Install these packages on Ubuntu execute the following command:
[I]         $> apt-get install gcc flex bison cmake openssl libssl-dev qt3-dev-tools

[/I]
To install these packages on Fedora execute the following command:
*$> yum install gcc flex bison cmake openssl openssl-devel qt3-devel*


For other systems, refer to your Distribution package manager for details on locating and installing
packages.	


**[SIZE=2]Compile the Source Code for the Shrew Soft VPN Client[/SIZE]**
1. Change to Download directory	
*$> cd ~/Downloads*
	

2.Unpack the Source files.
[I]         $> tar &#8211;xzvf shrewsoft-client.tgz

[/I]
3. Change to the source directory.
*$> cd ~/Downloads/ike*


4. Run cmake.


For GUI Installation (recommended):
*$> cmake &#8211;DQTGUI=YES &#8211;DETCDIR=/etc &#8211;DNATT=YES*


For non-GUI Installation:
[I]         $> cmake -DNATT=YES

[/I]
5. Run make.
*         $> make*


6. Run make install. NOTE: Run as root.
*         $> make install*

---

### Post by chili555 on 2013-03-05
My suggestion is the same; it's too old to compile correctly on a recent kernel. I'm afraid I have no other recommendations.

---

