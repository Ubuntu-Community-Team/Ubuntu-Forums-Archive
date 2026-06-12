---
title: "Linux version for Fortinet VPN client"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by namtuocbongdem on 2010-02-21
Hi All,

I am currently using FortiClient (from Fortinet) tool to connect to company VPN server for working from home but this tool can only run on Windows. I have been searching for Linux version for long time but no luck so far. This is the only app I need for my work on Ubuntu though I am using Ubuntu for my work for 2 years but it's really inconvenient when working away the office.

This is the tool we are using: [http://www.fortinet.com/products/endpoint/forticlient.html](http://www.fortinet.com/products/endpoint/forticlient.html)

I found this link but could not get the tool written for Linux due to access permission:

[http://www.ucalgary.ca/it/networks/vpn/admin/linux](http://www.ucalgary.ca/it/networks/vpn/admin/linux)

Great thanks if anyone know an alternative solution or Linux version of the tool. Thanks.

---

### Post by namtuocbongdem on 2010-02-21
No one knows anything about this?

---

### Post by maconthebeach on 2010-03-13
Check this out!
Works great for me @ 9.10
--> [http://paulgrenyer.blogspot.com/2010/02/linux-fortinet-vpn-client.html](http://paulgrenyer.blogspot.com/2010/02/linux-fortinet-vpn-client.html)


Cheers
mac

---

### Post by d2theg on 2010-11-11
Went to the site mentioned above, chromium thinks it's a malware site -

---

### Post by jeabus on 2011-01-27
You can get it from the fortinet website, but it's listed under the fortigate firmware:

[ftp://support.fortinet.com/FortiGate/v4.00/4.0/4.0.0/SSL%20VPN%20Clients/](ftp://support.fortinet.com/FortiGate/v4.00/4.0/4.0.0/SSL%20VPN%20Clients/)

---

### Post by coffebeans on 2011-07-20
dear all,

I am a new linux user having the same problem connecting to a corporate network using forticlient.

The IT dept does not know how to setup the client in ubuntu linux.

They have provided a config file,   .vpl file with the settings inside.

As a new user i am not sure how to go about setting up a vpn and using the client to get on to the corporate network.

i am using the ubuntu 10.10 desktop edition.

Any help would be appreciated.

---

### Post by SpawnHappyJake on 2011-09-23
Jeabus's link gave me a username/ password prompt as well. First, I found the ucalgory one, but again, a username / password prompt.

I am still searching for the Foriclient for Linux. Oddly, if one goes to the Forticlient website, there is no link, or link to a link, or link to a link to a link that lets you download the Linux version. I tried using their search box searching for "Linux", but their search bar is broke.

""linux" site:*.forticlient.com" at Google and Bing yielded no results.

Forticlient actually inserts kernel-level code to emulate a modem (yes, actual kernel-level hardware emulation). That means it can't work in WINE, unless WINE does something very interesting. Kernel-level code must be written for the kernel it is to work with. Remember that WINE is not a virtual machine or an operating system in an operating system. It "merely" translates program calls from Windows form to "Unix-like" form and back. It stands as a translator between the Windows program and the operating system. The operating system really is running the Windows program (shows up in gnome-system-monitor), unlike if you used a virtual machine to do the job.

Well, I'll keep searching, and let y'all know if I find it.

Cheers,
Jake

---

### Post by SpawnHappyJake on 2011-09-23
[http://internal.enterprisecomponent.com/download/FortiClientSSLVPN/forticlientsslvpn_linux_4.0.2010.tar.gz](http://internal.enterprisecomponent.com/download/FortiClientSSLVPN/forticlientsslvpn_linux_4.0.2010.tar.gz)

Don't worry, it's not source code, despite the file extension. You won't have to compile anything.

The above be the meat 'n' patatas!

But ya also need your vegtables:

Download this PDF: [http://portal.modeldriven.org/sites/default/files/SSL_VPN_Client_User_Guide.pdf](http://portal.modeldriven.org/sites/default/files/SSL_VPN_Client_User_Guide.pdf), it has instructions on how to get Forticlient for Linux working.

In that PDF is where I found the link to the actual thing.

Here was the story of finding it, if you like acquiring searching skills:

I searched "forticlient for linux" on Bing, and the fourth link was to a PDF. Thinking it was nothing, I skipped over it. But then I decided to look back at it after a few bogus sites that simply use your search words as tags (I **detest** those sites! :evil:), and in the "sample snippet" of this PDF link, I saw "Installing the stand alone **FortiClient** SSL VPN Client for **Linux** 1. Download the **Linux** archive...". So I downloaded the PDF ([http://portal.modeldriven.org/sites/default/files/SSL_VPN_Client_User_Guide.pdf](http://portal.modeldriven.org/sites/default/files/SSL_VPN_Client_User_Guide.pdf), opened it, and Ctrl+F'ed for "Linux". Ta-da! There it was! A link that worked!

Ok, it wasn't a particularly intense searching effort, but it's still good to post how you find things. It can't touch how intense it was trying to find a graphics emulator 6 years ago. Not a wrapper, an emulator. One that you can run from within the operating system, not something embedded into VirtualBox or QEMU or something. It took hours. 3D Analyze was on, like, page 22. It's the closest thing to kernel-level graphics card emulation that I know of. But now it's the first link that comes up. The other intense one was finding a free optical drive emulator that supports "burning" to a disk image. KernSafe TotalMounter was completely cut off from all search results, and I found it in some obscure forum, pages down in the thread. That actually took years to find, but has floated closer to the surface now, and actually shows up on page 2. Pretty sure it's still the only one. Unfortunately, the program doesn't work, though maybe it does now. One last one: try and find a place online that sells vacuum cleaner bags for a vacuum cleaner that's not made anymore, especially one where they changed the model name of the bag.

---

### Post by SpawnHappyJake on 2011-10-05
Ok, the issue with my network that wasn't letting me log on has been fixed, and I have confirmed that this FortiClient for Linux does in fact work!

For me, after inputting my user name and password into FortiClient, I just opened Nautilus, went to "location", and typed in smb://[ip address]/[path] , a prompt for a user name and password came up (different user name and password than previous, first is my user name and password for the network, and the second is my user name and password for my roaming user account that I would log into Windows with on a computer in the network with that roaming user thing enabled. Then once I log into such a computer, I have a personal "Z:\" drive on a local server in "Computer". I like to call it "fog storage". The contents of the Z:\ drive is made available to me by FortiClient on an external computer.)

Cheers,
Jake

---

### Post by SpawnHappyJake on 2011-10-05
BTW, just wanted to add that FortiClient for Linux does not emulate hardware. Meaning it does not make the kernel lie and report extra non-existent hardware, in this case (not) a network adapter. You see, like with CDEmu, a kernel module is installed that makes the kernel report additional no-existent hardware: an optical drive and SCSI controller. All software ran by the OS acquires hardware info from the kernel, so to the software ran by the OS, the optical drive is just as real as the rest of the hardware.

However, with the Windows version of FortiClient, a kernel-level driver is installed that emulates a FortiClient Modem. It actually shows up in the list of hardware. All software ran by Windows gets hardware info from the kernel, and thus sees this FortiClient Modem as real hardware: just like a keyboard or a thumb drive. It actually shows up in Device Manager, WMI, etc.

Cheers,
SpawnHappy

---

### Post by crabbyC on 2012-01-06
Great!  This is exactly what I've been looking for.  Works perfectly.

---

### Post by linuxque on 2012-01-27
> **SpawnHappyJake said:**
> [http://internal.enterprisecomponent.com/download/FortiClientSSLVPN/forticlientsslvpn_linux_4.0.2010.tar.gz](http://internal.enterprisecomponent.com/download/FortiClientSSLVPN/forticlientsslvpn_linux_4.0.2010.tar.gz)

Don't worry, it's not source code, despite the file extension. You won't have to compile anything.

The above be the meat 'n' patatas!

But ya also need your vegtables:

Download this PDF: [http://portal.modeldriven.org/sites/default/files/SSL_VPN_Client_User_Guide.pdf](http://portal.modeldriven.org/sites/default/files/SSL_VPN_Client_User_Guide.pdf), it has instructions on how to get Forticlient for Linux working.

In that PDF is where I found the link to the actual thing.

Here was the story of finding it, if you like acquiring searching skills:

I searched "forticlient for linux" on Bing, and the fourth link was to a PDF. Thinking it was nothing, I skipped over it. But then I decided to look back at it after a few bogus sites that simply use your search words as tags (I **detest** those sites! :evil:), and in the "sample snippet" of this PDF link, I saw "Installing the stand alone **FortiClient** SSL VPN Client for **Linux** 1. Download the **Linux** archive...". So I downloaded the PDF ([http://portal.modeldriven.org/sites/default/files/SSL_VPN_Client_User_Guide.pdf](http://portal.modeldriven.org/sites/default/files/SSL_VPN_Client_User_Guide.pdf), opened it, and Ctrl+F'ed for "Linux". Ta-da! There it was! A link that worked!

Ok, it wasn't a particularly intense searching effort, but it's still good to post how you find things. It can't touch how intense it was trying to find a graphics emulator 6 years ago. Not a wrapper, an emulator. One that you can run from within the operating system, not something embedded into VirtualBox or QEMU or something. It took hours. 3D Analyze was on, like, page 22. It's the closest thing to kernel-level graphics card emulation that I know of. But now it's the first link that comes up. The other intense one was finding a free optical drive emulator that supports "burning" to a disk image. KernSafe TotalMounter was completely cut off from all search results, and I found it in some obscure forum, pages down in the thread. That actually took years to find, but has floated closer to the surface now, and actually shows up on page 2. Pretty sure it's still the only one. Unfortunately, the program doesn't work, though maybe it does now. One last one: try and find a place online that sells vacuum cleaner bags for a vacuum cleaner that's not made anymore, especially one where they changed the model name of the bag.

Hi,
 Link not working. Kindly update if you know...

Thanks

---

### Post by mechanizedmedic on 2012-03-03
could someone please post a new link? this is not working for me either.

---

### Post by rmarrs on 2012-08-10
I just was looking for the same thing and came across this link. I haven't tested it yet.

[http://it.greenstonehomes.com/vpn/forticlientsslvpn_linux_4.0.2082.tar.gz](http://it.greenstonehomes.com/vpn/forticlientsslvpn_linux_4.0.2082.tar.gz)

---

### Post by wshaddix on 2012-08-19
I have downloaded forticlientsslvpn_linux_4.0.2069 but when I try to open the forticlientsslvpn file nothing happens. I've manually ran \helper\setup.linux.sh and accepted the license, but I can never get forticlientsslvpn to run in order to setup the vpn credentials. 

Anyone have any ideas?

Thanks

---

### Post by azhargiri on 2013-01-01
Try this link :
[ftp://support.fortinet.com/FortiGate/v4.00/4.0MR3/MR3_Patch_8/SSL-VPN/forticlientsslvpn_linux_4.4.2267.tar.gz](ftp://support.fortinet.com/FortiGate/v4.00/4.0MR3/MR3_Patch_8/SSL-VPN/forticlientsslvpn_linux_4.4.2267.tar.gz)

I found it in fedora forum
[http://forums.fedoraforum.org/showthread.php?t=280553](http://forums.fedoraforum.org/showthread.php?t=280553)


or you may try the newest one :
[ftp://support.fortinet.com/FortiGate/v4.00/4.0MR3/MR3_Patch_9/SSL-VPN/forticlientsslvpn_linux_4.4.2270.tar.gz](ftp://support.fortinet.com/FortiGate/v4.00/4.0MR3/MR3_Patch_9/SSL-VPN/forticlientsslvpn_linux_4.4.2270.tar.gz)

---

### Post by hockeybum27 on 2013-12-30
Ubuntu 12.04 64-bit:

I downloaded from the forticlient ftp site, but got the version 4.4.2294.tar.gz (from the 5.0 directory on the ftp site),  thinking it would be the latest/greatest. 

When I follow the above directions and try launch the forticlientsslvpn from terminal, it says 'command not found'.    I do confirm it is in the directory, however.  The weird thing is, ls shows these files in light green, not  sure what significance that is (I tried running via sudo but same  result).

If I try to run from Nautilus, is says some files are list, check to see if the installation package is corrupt.  

If I run an older version (4.0.2254.tar.gz), it initially runs (it says it's first-time setup, prompts to do config, I enter my pwd, etc., and I get the GUI), but it does not stay connected, I have to kill via system monitor, and when I try to reconnect it says failed.

[ftp://support.fortinet.com/FortiGate/v4.00/4.0MR3/MR3_Patch_15/SSL-VPN/](ftp://support.fortinet.com/FortiGate/v4.00/4.0MR3/MR3_Patch_15/SSL-VPN/)

which is 4.4.2287, I still cannot run from command line, but when I try to run from Nautilus, it starts - it says it's the first time, and I need to config - BUT instead of running the config, I get a popup that says 'set up failed'.  Thinking this was due to the older version, I deleted it (that is, I removed the directory containing all the extracted files) but this did not resolve anything.

---

### Post by JCCyC on 2014-01-21
> **azhargiri said:**
> Try this link :
[ftp://support.fortinet.com/FortiGate/v4.00/4.0MR3/MR3_Patch_8/SSL-VPN/forticlientsslvpn_linux_4.4.2267.tar.gz](ftp://support.fortinet.com/FortiGate/v4.00/4.0MR3/MR3_Patch_8/SSL-VPN/forticlientsslvpn_linux_4.4.2267.tar.gz)

I found it in fedora forum
[http://forums.fedoraforum.org/showthread.php?t=280553](http://forums.fedoraforum.org/showthread.php?t=280553)


or you may try the newest one :
[ftp://support.fortinet.com/FortiGate/v4.00/4.0MR3/MR3_Patch_9/SSL-VPN/forticlientsslvpn_linux_4.4.2270.tar.gz](ftp://support.fortinet.com/FortiGate/v4.00/4.0MR3/MR3_Patch_9/SSL-VPN/forticlientsslvpn_linux_4.4.2270.tar.gz)

All of these FTP links ask for an username/password!

---

### Post by asto2 on 2014-01-24
> **JCCyC said:**
> All of these FTP links ask for an username/password!

[ftp://pftpintl:F0rt1intl@support.fortinet.com](ftp://pftpintl:F0rt1intl@support.fortinet.com)

(source [http://forums.fedoraforum.org/showthread.php?t=280553](http://forums.fedoraforum.org/showthread.php?t=280553))

---

