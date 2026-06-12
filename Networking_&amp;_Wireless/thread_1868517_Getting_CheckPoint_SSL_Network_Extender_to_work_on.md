---
title: "Getting CheckPoint SSL Network Extender to work on oneiric 64 bit"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by agnul on 2011-10-24
Hi,

I'm trying to run the CheckPoint network extender on a 64 bit oneiric install, but I'm stuck. I've downloaded and installed the Check_Point_SNX_R71 software, but when I run the snx command I get a 

[INDENT]snx: error while loading shared libraries: libpam.so.0: cannot open shared object file: No such file or directory[/INDENT]

error message. Of course libpam is there, only it's the 64bit version. If I try to install the ia32-libs-multiarch package from aptitude (which should contain 32 bit pam libraries) aptitude wants to remove half the system, so I'd rather not go there.

Is there any fix? Any alternative software I could use?

TIA

---

### Post by sonearth on 2011-10-25
I have the same problem now when i installed ubuntu 11.10. Snx worked perfectly on 10.10.

I also tried to launch snx on 32bit version (also ubuntu 11.10), but got the same mistake.

Please, help. Thanks!

---

### Post by agnul on 2011-10-26
I got it to run inside a 32 bit chroot following most of the instructions from [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

You'll need to install a kernel image and a couple other packages in the chroot (libstdc++5 and libX6 if I recall correctly).

---

### Post by shukalo83 on 2011-11-12
Hello 

Maybe I am bumping an old thread but does anyone have a better solution than chroot?

What about this here?

[http://kenfallon.com/how-to-install-checkpoint-ssl-extender-vpn-snx-under-fedora-14/](http://kenfallon.com/how-to-install-checkpoint-ssl-extender-vpn-snx-under-fedora-14/)

---

### Post by shukalo83 on 2011-11-12
My output of ldd:


home@xubuntu:~$ sudo ldd /usr/bin/snx
	linux-gate.so.1 =>  (0xf76e2000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf7595000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf757a000)
	libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xf7562000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf755d000)
	libpam.so.0 => not found
	libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xf7544000)
	libstdc++.so.5 => not found
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf73c7000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf73a8000)
	/lib/ld-linux.so.2 (0xf76e3000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf73a4000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf739d000)

---

### Post by agnul on 2011-11-14
It's working in a chroot and I don't feel like experimenting :lolflag: but the problem I had with installing 32bit libpam was a bug in aptitude and not a problem with the libs, so it could be worth retrying an install of ia32-libs.

---

### Post by netdog on 2012-11-22
Hi, 

I had the same output of ldd showing the missing libpam.so.0, I simply installed the 32 bit version of libpam which appeared to have resolved the issue. I can now run snx without any issues and I am not using a chroot.
> 
imesias@ubuntu:~$ sudo apt-get install libpam0g:i386
[sudo] password for imesias: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libpam-doc:i386
The following NEW packages will be installed:
  libpam0g:i386
0 upgraded, 1 newly installed, 0 to remove and 67 not upgraded.
Need to get 61.2 kB of archives.
After this operation, 218 kB of additional disk space will be used.
Get:1 [ftp://mirror.ac.za/ubuntu/ubuntu-archive/ubuntu/](ftp://mirror.ac.za/ubuntu/ubuntu-archive/ubuntu/) quantal/main libpam0g i386 1.1.3-7ubuntu3 [61.2 kB]
Fetched 61.2 kB in 2s (24.9 kB/s)   
Preconfiguring packages ...
Selecting previously unselected package libpam0g:i386.
(Reading database ... 174378 files and directories currently installed.)
Unpacking libpam0g:i386 (from .../libpam0g_1.1.3-7ubuntu3_i386.deb) ...
Setting up libpam0g:i386 (1.1.3-7ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
imesias@ubuntu:~$ sudo ldd $(which snx)
	linux-gate.so.1 =>  (0xf779a000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf7649000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf762e000)
	libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xf7616000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf7611000)
	libpam.so.0 => /lib/i386-linux-gnu/libpam.so.0 (0xf7603000)
	libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xf75e9000)
	libstdc++.so.5 => /usr/lib/i386-linux-gnu/libstdc++.so.5 (0xf752f000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7384000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf7362000)
	/lib/ld-linux.so.2 (0xf779b000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf7336000)
	libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf7318000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf7314000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf730c000)
imesias@ubuntu:~$ snx
failed to open file: /home/imesias/.snxrc
Valid attributes are:
   - server          SNX server to connet to
   - sslport         The SNX SSL port (if not default)
   - username        the user name
   - certificate     certificate file to use
   - calist          directory containing CA files
   - reauth          enable automatic reauthentication. Valid values { yes, no }
   - debug           enable debug output. Valid values { yes, 1-5 }
   - cipher          encryption algorithm to use. Valid values { RC4 / 3DES }
   - proxy_name      proxy hostname 
   - proxy_port      proxy port
   - proxy_user      username for proxy authentication


---

### Post by wildmanne39 on 2012-11-22
Old thread closed. Thanks for sharing.

---

