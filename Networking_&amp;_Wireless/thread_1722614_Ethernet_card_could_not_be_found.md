---
title: "Ethernet card could not be found"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by sandy0594 on 2011-04-06
Hi all, i am new to linux..i have just now installed ubuntu 10.10  desktop edition..I am unable to configure n/w connections in  linux..btw,i tried this

```

sudo pppoeconf

Sorry,no working ethernet card could be found.If you do have an interface card which was not autodetected so far,you probably wish to load the driver manually using the modconf utility.Run modconf now?  

 /usr/sbin/pppoeconf: 523: modconf: not found
 
 Ifconfig
  
   Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:20 errors:0 dropped:0 overruns:0 frame:0
            TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
              RX bytes:1304 (1.3 KB)  TX bytes:1304 (1.3 KB)


  
lspci -nn | grep Ethernet

  01:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)

```


Any suggestions are highly appreciated

---

### Post by dineshs on 2011-04-06
What do you get for```
sudo lshw -C network
```

---

### Post by sandy0594 on 2011-04-06
i have tried this as per your suggestion

```


sudo lshw -C network

*-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:febc0000-febfffff ioport:ec00(size=128)


```

---

### Post by dineshs on 2011-04-06
> Atheros Communications Device [1969:1083] (rev c0)Pl see if this post is related
[http://ubuntuforums.org/showthread.php?t=1677122](http://ubuntuforums.org/showthread.php?t=1677122)

---

### Post by Bucky Ball on 2011-04-06
Plug in an ethernet cable if you can and haven't already and get all updates.

Then look in System>Administration>Additional Drivers. Anything in there? 10.04 LTS is probably a safer start for newcomers and has longer support. 

Welcome. ;)

---

### Post by sandy0594 on 2011-04-06
Can u be more specific i went through that post by m0gwai([http://ubuntuforums.org/showthread.php?t=1677122](http://ubuntuforums.org/showthread.php?t=1677122))..I downloaded the patch and linux driver

As i am new to linux,i am finding it difficult for the commands of how to apply the patch and how to execute after cd to src.Kindly bear me as i am completely layman to linux

---

### Post by sandy0594 on 2011-04-06
hey,i tried the steps..but it's not working..Kindly explain me where i am doing wrong

```


 [FONT=&quot]sandy@ubuntu:/media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/AR81Family-linux-v1.0.1.14/src$ sudo make install[/FONT]
  [FONT=&quot]Makefile:105: *** Linux kernel source not configured - missing autoconf.h.  Stop.[/FONT]
   
  [FONT=&quot]sandy@ubuntu:~$ patch -p1  /media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/AR81Family-linux-v1-1.0.1.14.patch/AR81Family-linux-v1-1.0.1.14.patch[/FONT]
  [FONT=&quot]The program 'patch' is currently not installed.  You can install it by typing:[/FONT]
  [FONT=&quot]sudo apt-get install patch[/FONT]
   
  [FONT=&quot]sandy@ubuntu:~$ sudo apt-get install patch[/FONT]
  [FONT=&quot]Reading package lists... Done[/FONT]
  [FONT=&quot]Building dependency tree       [/FONT]
  [FONT=&quot]Reading state information... Done[/FONT]
  [FONT=&quot]E: Unable to locate package patch[/FONT]
  


```

---

### Post by Bucky Ball on 2011-04-06
You've plugged in an ethernet cable?

---

### Post by chili555 on 2011-04-06
> **Bucky Ball said:**
> You've plugged in an ethernet cable?His ethernet is exactly what he can't get working. If there is no working driver, plugging in an ethernet cable solves nothing.

---

### Post by sandy0594 on 2011-04-06
I have windows running and simultaneously ubuntu..In windows it works fine,in linux i don't know how to configure but as per u people advice,i tried to configure which resulted in the above errors which i posted..

I downloaded AR81Family-linux-v1.0.1.14 and AR81Family-linux-v1-1.0.1.14.patch,I am trying to install them but to vain.Kindly someone suggest how to solve this issue?

```


 sandy@ubuntu:~$ tar xvvf '/media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/AR81Family-linux-v1-1.0.1.14.patch.tar.gz' 
  -rw-r--r-- kalcher/staff  2905 2011-01-28 08:20 AR81Family-linux-v1-1.0.1.14.patch
  sandy@ubuntu:~$ sudo make install
  make -C ./src/ install
  make[1]: Entering directory `/home/sandy/src'
  Makefile:105: *** Linux kernel source not configured - missing autoconf.h.  Stop.
  make[1]: Leaving directory `/home/sandy/src'
  make: *** [install] Error 2
  



```

---

### Post by Bucky Ball on 2011-04-06
> **chili555 said:**
> His ethernet is exactly what he can't get working. If there is no working driver, plugging in an ethernet cable solves nothing.

Thought OP was attempting to get wireless working. Does a cable work? That is my question. If so, will it download the appropriate drivers with an update? ;)

---

### Post by chili555 on 2011-04-06
> Thought OP was attempting to get wireless working. Does a cable work? That is my question. If so, will it download the appropriate drivers with an update? No on all points.

---

### Post by sandy0594 on 2011-04-07
I am using the same PC which i am running windows and ubuntu..from windows,i am replying u..So,where is the point that my cable is not working..i don't understand..

To my knowledge,i am wrong with installation of **AR81Family-linux-v1.0.1.14** and **AR81Family-linux-v1-1.0.1.14.patch**.Kindly,suggest me as of how to install these things

---

### Post by dineshs on 2011-04-07
I think (not sure-[COLOR="Red"]someone in the forum please correct me if I am wrong[/COLOR])
Step-I
You need to to get and install patch and build-essential before the driver which is difficult  without internet connection.
Pl try if this works.
Go to synaptic package manager and mark [COLOR="Blue"]patch[/COLOR] and [COLOR="Blue"]build-essential[/COLOR] for installation  (do not apply). You will see a list of packages and dependencies that need to be installed. Note them all and download them seperately via any other OS.(You may use a thumb drive to transfer them to ubuntu). Copy all the files and paste them to /var/cache/apt/archives. ie run 
```
gksudo nautilus /var/cache/apt/archives
```
A folder will be opened. Copy the downloaded files on thumb drive and paste it here.
Note:To download packages go to [packages.ubuntu.com]("http://packages.ubuntu.com/") and select your distribution  
After copying them go back to synaptic package manager and apply the marked packages for installation.
Step-II 
Make a folder on Desktop ,name it as AR and copy the driver (AR81Family-linux-v1.0.1.14.tar.gz)to it
Let the patch be on desktop(AR81Family-linux-v1-1.0.1.14.patch.tar.gz).Rightclick on the patch and click extract here (to get AR81Family-linux-v1-1.0.1.14.patch on desktop) .
Now run
```
cd ~/Desktop/AR
tar xvvf AR81Family-linux-v1.0.1.14.tar.gz
cd src
patch -p1 < ~/Desktop/AR81Family-linux-v1-1.0.1.14.patch
```
Step-III
```
cd ~/Desktop/AR
sudo make install
sudo modprobe atl1e
```

---

### Post by sandy0594 on 2011-04-07
hey,i did as per ur advice

> 

Make a folder on Desktop ,name it as AR and copy the driver (AR81Family-linux-v1.0.1.14.tar.gz)to it

Let the patch be on  desktop(AR81Family-linux-v1-1.0.1.14.patch.tar.gz).Rightclick on the  patch and click extract here (to get AR81Family-linux-v1-1.0.1.14.patch  on desktop) .



Below are the results:

```


 sandy@ubuntu:~$ cd ~/Desktop/AR
  sandy@ubuntu:~/Desktop/AR$ tar xvvf AR81Family-linux-v1.0.1.14.tar.gz
  drwxrwxrwx root/root         0 2010-09-14 03:34 ./
  -r-xr-Sr-x root/root      4402 2010-07-21 22:40 ./atl1e.7
  -rwxrwSrwx root/root     11502 2010-06-25 04:54 ./atl1e.spec
  -rwxrwSrwx root/root      2648 2010-06-25 04:54 ./at_osdep.h
  -rwxrwSrwx root/root     18671 2010-06-25 04:54 ./copying
  -rwxrwSrwx root/root       198 2010-06-25 04:54 ./dkms.conf
  -rwxrwSrwx root/root      4596 2010-06-25 04:54 ./ldistrib.txt
  -r-xr-Sr-x root/root       977 2010-08-06 04:48 ./Makefile
  -rwxrwSrwx root/root       673 2010-06-25 04:54 ./pci.updates
  -rwxrwSrwx root/root      7525 2010-06-25 04:54 ./readme
  -r-xr-Sr-x root/root      1729 2010-09-14 03:28 ./release_note.txt
  drwxrwxrwx root/root         0 2010-09-14 03:21 ./src/
  -rwxrwSrwx root/root     20480 2010-08-19 07:36 ./src/.atl1c_main.c.swo
  -r-xr-Sr-x root/root     22306 2010-07-21 02:32 ./src/atl1c.h
  -r-xr-Sr-x root/root     10893 2010-06-25 00:42 ./src/atl1c_ethtool.c
  -r-xr-Sr-x root/root     19417 2010-06-25 00:42 ./src/atl1c_hw.c
  -r-xr-Sr-x root/root     33678 2010-08-06 04:48 ./src/atl1c_hw.h
  -rwxrwSrwx root/root     91461 2010-09-14 03:21 ./src/atl1c_main.c
  -r-xr-Sr-x root/root      7041 2010-06-25 00:42 ./src/atl1c_param.c
  -r-xr-Sr-x root/root      4826 2010-06-25 00:42 ./src/atl1e.h
  -r-xr-Sr-x root/root     15949 2010-06-25 00:42 ./src/atl1e_ethtool.c
  -r-xr-Sr-x root/root     24225 2010-06-25 00:42 ./src/atl1e_hw.c
  -r-xr-Sr-x root/root     52924 2010-06-25 00:42 ./src/atl1e_hw.h
  -r-xr-Sr-x root/root    101017 2010-06-25 00:42 ./src/atl1e_main.c
  -r-xr-Sr-x root/root      7981 2010-06-25 00:42 ./src/atl1e_param.c
  -r-xr-Sr-x root/root      4075 2010-06-25 00:42 ./src/at_common.h
  -rwxrwSrwx root/root      7092 2010-09-14 03:20 ./src/at_common_main.c
  -r-xr-Sr-x root/root      2732 2010-06-25 00:42 ./src/at_osdep.h
  -r-xr-Sr-x root/root      5997 2010-06-25 00:42 ./src/kcompat.c
  -rwxrwSrwx root/root     50085 2010-09-14 03:16 ./src/kcompat.h
  -r-xr-Sr-x root/root     30563 2010-06-25 00:42 ./src/kcompat_ethtool.c
  -r-xr-Sr-x root/root     10858 2010-06-25 00:42 ./src/Makefile
   
  gzip: stdin: decompression OK, trailing garbage ignored
  -rwxrwSrwx root/root         0 2010-08-06 02:05 ./src/Module.markers
  -r-xr-Sr-x root/root         0 2010-06-25 00:42 ./src/Module.symvers
  -rwxrwSrwx root/root        63 2010-09-13 22:38 ./src/modules.order
  tar: Child returned status 2
  tar: Error is not recoverable: exiting now
  


```

So,again the same story:

   **[FONT=&quot]The program 'patch' is currently not installed.  You can install it by typing:[/FONT]**
**[FONT=&quot]sudo apt-get install patch[/FONT]**

**[FONT=&quot][/FONT]**
[FONT=&quot]I can't understand what is going wrong,i am attaching the patch and the driver in this post
[/FONT]

---

### Post by chili555 on 2011-04-07
> So,where is the point that my cable is not working..i don't understand..The point is that you were advised to connect an ethernet cable and download things. Clearly, if your ethernet card is not working, this won't work. 

I think you will also need to install linux-headers-generic. Are you able to install the needed packages in Synaptic by using the install CD as a software source? Or how?> I can't understand what is going wrong,Didn't you install patch and build-essential as dineshs advised?

---

### Post by sandy0594 on 2011-04-07
with the guidance from [https://help.ubuntu.com/community/In...ded%20packages]("https://help.ubuntu.com/community/InstallingSoftware#Installing%20downloaded%20packages")

I got synaptic script which is below,i viewed from firefox browser

```


wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libgssrpc4_1.8.1+dfsg-5ubuntu0.1_i386.deb
wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm5clnt-mit7_1.8.1+dfsg-5ubuntu0.1_i386.deb
wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkdb5-4_1.8.1+dfsg-5ubuntu0.1_i386.deb
wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm5srv-mit7_1.8.1+dfsg-5ubuntu0.1_i386.deb
wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/krb5-doc_1.8.1+dfsg-5ubuntu0.1_all.deb
wget -c http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl-doc_0.9.8o-1ubuntu4.1_all.deb
wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-dbg_1.8.1+dfsg-5ubuntu0.1_i386.deb
wget -c http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8o-1ubuntu4.1_i386.deb


```

what should i do with that script..i am getting 404 error if i am trying to open the links
eg:[http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8o-1ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8o-1ubuntu4.1_i386.deb)

So,can anyone explain what should i do now..i installed ubuntu through windows installer **wubi**

---

### Post by chili555 on 2011-04-07
Where did you come up with that list of packages? I doubt that krb5 has much to do with your ethernet card's driver.

---

### Post by sandy0594 on 2011-04-07
with synaptic package manager,i marked them for installation and generated a script with .sh extension..i added the .sh extension file in my previous post..can anyone say me what to do next
I used the following link for reference [https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

---

### Post by chili555 on 2011-04-07
Why did you pick those particular packages? dineshs asked you to install patch and build-essential and I asked you to install linux-headers. None of the packages in your script have anything to do with the packages we recommended. 

Without an internet connection, your script, even with the correct package names, will never work.

It will be a bit arduous to do this without an internet connection, but if you are persistent and careful, we can do it. Are you game? Do you have a USB drive?

I downloaded, patched and installed the driver myself a few moments ago. It works without error.

---

### Post by sandy0594 on 2011-04-07
Oh god,how can i reply u without an internet connection..i am running windows and linux on same pc.i am a new user in linux..In windows my internet works well..so,i copied the script generated by synaptec package manager to USB drive and then tried to run the script from windows which costed me the error as seen above in my previous posts

> 

what should i do with that script..i am getting 404 error if i am trying to open the links
eg:[http://security.ubuntu.com/ubuntu/po...tu4.1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8o-1ubuntu4.1_i386.deb")



how can i know what packages to install..i just marked the ones which are not installed

---

### Post by chili555 on 2011-04-07
> how can i know what packages to install.I was sort of hoping old Dr. Chili and, perhaps, dineshs might help you. Print or copy this off so that when you go back to the Ubuntu side, you can follow these instructions. I propose that we determine the packages we need, download them on the Windows side and put them on a USB drive; reboot to Ubuntu and install them. Then run the patch and install the driver as dineshs previously detailed.

We will get the packages here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  Notice at the bottom is a search feature. Be sure to search for Maverick and 32-bit.

We know we need patch.

We need linux-headers matching your running kernel. While in Ubuntu, open a terminal and do:```
uname -r
```For example, in my case, it comes back 2.6.35-28-generic. So if I were installing linux-headers, I'd get linux-headers-2.6.35-28-generic. 

We need build-essential. It is a meta-package that has several dependencies which must also be installed. They are: libc6-dev, gcc, g++, make and dpkg-dev.

Get all those packages, and install them with:```
sudo dpkg -i patch*
```You can use the wildcard * to keep from having to type all the version number stuff. Continue for each package and then do the patch and install.

I'll be nearby in case you get stuck.

---

### Post by Bucky Ball on 2011-04-07
> **chili555 said:**
> No on all points.

Cheers chilli555. ;)

---

### Post by sandy0594 on 2011-04-07
I did as u said

#code#

 sandy@ubuntu:~$ uname -r
  2.6.35-22-generic
  

#code#

but in the synaptec package manager i din't find packages with **patch **and **build-essential**..I even searched for them in package manager..the search for package **patch** yielded results but all of them are **installed** and for **build-essential** there are no results..So,can u kindly say me is there any command by which we can know what are the packages to be installed

---

### Post by chili555 on 2011-04-07
They are undoubtedly *not* installed. If you are determined to check, open Synaptic and search for each of the packages. If they are not found, or if there is no little green box next to the name, they are not installed.

Without either an internet connection or the install CD, Synaptic is useless.

You could also check:```
sudo dpkg -s patch
```If it's installed, you will see:> Package: patch
Status: install ok installed
If you have not been able to connect to the internet, it is doubtful any of these are installed. I recommend you download and install them as I outlined.

---

### Post by sandy0594 on 2011-04-07
Actually,these packages are not my problem chilli..i couldn't configure the n/w connections that's what my primary area of concern..

For configuring the n/w connections i have downloaded **AR81Family-linux-v1-1.0.1.14.patch **and **AR81Family-linux-v1.0.1.14**..i am unable to install them,this is what bothers me..

```


 sandy@ubuntu:~$ tar xvvf '/media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/AR81Family-linux-v1-1.0.1.14.patch.tar.gz' 
  -rw-r--r-- kalcher/staff  2905 2011-01-28 08:20 AR81Family-linux-v1-1.0.1.14.patch
  sandy@ubuntu:~$ sudo make install
  make -C ./src/ install
  make[1]: Entering directory `/home/sandy/src'
  Makefile:105: *** Linux kernel source not configured - missing autoconf.h.  Stop.
  make[1]: Leaving directory `/home/sandy/src'
  make: *** [install] Error 2
  


```



```


sandy@ubuntu:~$ sudo apt-get install build-essential
   [sudo] password for sandy: 
   Reading package lists... Done
   Building dependency tree       
   Reading state information... Done
   E: Unable to locate package build-essential
   


```

I am confused with the way i am going..in windows it's just a cakewalk for me to configure n/w connection..it's taking hell out of me to configure it in linux..

Can anyone kindly explain me in the way i could probably understand

---

### Post by chili555 on 2011-04-07
> Actually,these packages are not my problem chilliThey are exactly your problem! In order to compile these packages, you _must_ _have_ build-essential and its dependencies, patch and linux-headers.

dineshs and I have suggested how you proceed, but you seem to reject all advice. If there was another, easier way, we would have recommended it.> sudo apt-get install build-essentialThis will never work until you have an internet connection.

---

### Post by sandy0594 on 2011-04-07
I think i got u in some points...i am on my way to downloading **linux-headers-2.6.35-28_2.6.35-28.49_all.deb**..I downloaded it in windows and i am about to copy it in a USB drive,Can you explain me how to install these packages

---

### Post by chili555 on 2011-04-07
You need ***all*** the packages in my post. Then install:```
sudo dpkg -i linux-headers*
```Continue until you have installed them all.

---

### Post by sandy0594 on 2011-04-07
hey chilli,only **linux-headers-2.6.35-28_2.6.35-28.49_all.deb  **got installed,the rest all got errors.below is the info:

```


 [FONT=&quot]$ sudo dpkg -i package.deb[/FONT]
   
  [FONT=&quot]sandy@ubuntu:~$ cd '/media/SANDY/packages' [/FONT]
  [FONT=&quot]sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i linux-headers*[/FONT]
  [FONT=&quot][sudo] password for sandy: [/FONT]
  [FONT=&quot]Selecting previously deselected package linux-headers-2.6.35-28.[/FONT]
  [FONT=&quot](Reading database ... 118296 files and directories currently installed.)[/FONT]
  [FONT=&quot]Unpacking linux-headers-2.6.35-28 (from linux-headers-2.6.35-28_2.6.35-28.49_all.deb) ...[/FONT]
  [FONT=&quot]Setting up linux-headers-2.6.35-28 (2.6.35-28.49) ...[/FONT]
  [FONT=&quot]sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i libc6-dev*[/FONT]
  [FONT=&quot](Reading database ... 130774 files and directories currently installed.)[/FONT]
  [FONT=&quot]Preparing to replace libc6-dev 2.12.1-0ubuntu6 (using libc6-dev_2.12.1-0ubuntu10.1_i386(1).deb) ...[/FONT]
  [FONT=&quot]Unpacking replacement libc6-dev ...[/FONT]
  [FONT=&quot]Preparing to replace libc6-dev 2.12.1-0ubuntu10.1 (using libc6-dev_2.12.1-0ubuntu10.1_i386.deb) ...[/FONT]
  [FONT=&quot]Unpacking replacement libc6-dev ...[/FONT]
  [FONT=&quot]More than one copy of package libc6-dev has been unpacked[/FONT]
  [FONT=&quot] in this run !  Only configuring it once.[/FONT]
  [FONT=&quot]dpkg: dependency problems prevent configuration of libc6-dev:[/FONT]
  [FONT=&quot] libc6-dev depends on libc6 (= 2.12.1-0ubuntu10.1); however:[/FONT]
  [FONT=&quot]  Version of libc6 on system is 2.12.1-0ubuntu6.[/FONT]
  [FONT=&quot] libc6-dev depends on libc-dev-bin (= 2.12.1-0ubuntu10.1); however:[/FONT]
  [FONT=&quot]  Version of libc-dev-bin on system is 2.12.1-0ubuntu6.[/FONT]
  [FONT=&quot]dpkg: error processing libc6-dev (--install):[/FONT]
  [FONT=&quot] dependency problems - leaving unconfigured[/FONT]
  [FONT=&quot]Errors were encountered while processing:[/FONT]
  [FONT=&quot] libc6-dev[/FONT]
  [FONT=&quot]sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i libc6-dev_2.12.1-0ubuntu10.1_i386.deb[/FONT]
  [FONT=&quot](Reading database ... 130774 files and directories currently installed.)[/FONT]
  [FONT=&quot]Preparing to replace libc6-dev 2.12.1-0ubuntu10.1 (using libc6-dev_2.12.1-0ubuntu10.1_i386.deb) ...[/FONT]
  [FONT=&quot]Unpacking replacement libc6-dev ...[/FONT]
  [FONT=&quot]dpkg: dependency problems prevent configuration of libc6-dev:[/FONT]
  [FONT=&quot] libc6-dev depends on libc6 (= 2.12.1-0ubuntu10.1); however:[/FONT]
  [FONT=&quot]  Version of libc6 on system is 2.12.1-0ubuntu6.[/FONT]
  [FONT=&quot] libc6-dev depends on libc-dev-bin (= 2.12.1-0ubuntu10.1); however:[/FONT]
  [FONT=&quot]  Version of libc-dev-bin on system is 2.12.1-0ubuntu6.[/FONT]
  [FONT=&quot]dpkg: error processing libc6-dev (--install):[/FONT]
  [FONT=&quot] dependency problems - leaving unconfigured[/FONT]
  [FONT=&quot]Errors were encountered while processing:[/FONT]
  [FONT=&quot] libc6-dev[/FONT]
  [FONT=&quot]sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i build-essential*[/FONT]
  [FONT=&quot]Selecting previously deselected package build-essential.[/FONT]
  [FONT=&quot](Reading database ... 130774 files and directories currently installed.)[/FONT]
  [FONT=&quot]Unpacking build-essential (from build-essential_11.5_i386.deb) ...[/FONT]
  [FONT=&quot]dpkg: dependency problems prevent configuration of build-essential:[/FONT]
  [FONT=&quot] build-essential depends on libc6-dev | libc-dev; however:[/FONT]
  [FONT=&quot]  Package libc6-dev is not configured yet.[/FONT]
  [FONT=&quot]  Package libc-dev is not installed.[/FONT]
  [FONT=&quot]  Package libc6-dev which provides libc-dev is not configured yet.[/FONT]
  [FONT=&quot] build-essential depends on g++ (>= 4:4.4.3); however:[/FONT]
  [FONT=&quot]  Package g++ is not installed.[/FONT]
  [FONT=&quot] build-essential depends on dpkg-dev (>= 1.13.5); however:[/FONT]
  [FONT=&quot]  Package dpkg-dev is not installed.[/FONT]
  [FONT=&quot]dpkg: error processing build-essential (--install):[/FONT]
  [FONT=&quot] dependency problems - leaving unconfigured[/FONT]
  [FONT=&quot]Errors were encountered while processing:[/FONT]
  [FONT=&quot] build-essential[/FONT]
  [FONT=&quot]sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i dpkg-dev*[/FONT]
  [FONT=&quot]Selecting previously deselected package dpkg-dev.[/FONT]
  [FONT=&quot](Reading database ... 130783 files and directories currently installed.)[/FONT]
  [FONT=&quot]Unpacking dpkg-dev (from dpkg-dev_1.15.8.4ubuntu3.1_all.deb) ...[/FONT]
  [FONT=&quot]dpkg: dependency problems prevent configuration of dpkg-dev:[/FONT]
  [FONT=&quot] dpkg-dev depends on libdpkg-perl (= 1.15.8.4ubuntu3.1); however:[/FONT]
  [FONT=&quot]  Package libdpkg-perl is not installed.[/FONT]
  [FONT=&quot] dpkg-dev depends on patch; however:[/FONT]
  [FONT=&quot]  Package patch is not installed.[/FONT]
  [FONT=&quot]dpkg: error processing dpkg-dev (--install):[/FONT]
  [FONT=&quot] dependency problems - leaving unconfigured[/FONT]
  [FONT=&quot]Processing triggers for man-db ...[/FONT]
  [FONT=&quot]Errors were encountered while processing:[/FONT]
  [FONT=&quot] dpkg-dev[/FONT]
  [FONT=&quot]sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i g++-multilib*[/FONT]
  [FONT=&quot]Selecting previously deselected package g++-multilib.[/FONT]
  [FONT=&quot](Reading database ... 130965 files and directories currently installed.)[/FONT]
  [FONT=&quot]Unpacking g++-multilib (from g++-multilib_4.4.4-1ubuntu2_i386.deb) ...[/FONT]
  [FONT=&quot]dpkg: dependency problems prevent configuration of g++-multilib:[/FONT]
  [FONT=&quot] g++-multilib depends on g++ (>= 4:4.4.4-1ubuntu2); however:[/FONT]
  [FONT=&quot]  Package g++ is not installed.[/FONT]
  [FONT=&quot] g++-multilib depends on g++-4.4-multilib (>= 4.4.4-1); however:[/FONT]
  [FONT=&quot]  Package g++-4.4-multilib is not installed.[/FONT]
  [FONT=&quot]dpkg: error processing g++-multilib (--install):[/FONT]
  [FONT=&quot] dependency problems - leaving unconfigured[/FONT]
  [FONT=&quot]Errors were encountered while processing:[/FONT]
  [FONT=&quot] g++-multilib[/FONT]
  [FONT=&quot]sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -s patch[/FONT]
  [FONT=&quot]Package `patch' is not installed and no info is available.[/FONT]
  [FONT=&quot]Use dpkg --info (= dpkg-deb --info) to examine archive files,[/FONT]
  [FONT=&quot]and dpkg --contents (= dpkg-deb --contents) to list their contents[/FONT]


```

I downloaded [B]linux-headers-2.6.35-28_2.6.35-28.49_all.deb,libc6-dev_2.12.1-0ubuntu10.1_i386.deb,build-essential_11.5_i386.deb,dpkg-dev_1.15.8.4ubuntu3.1_all.deb,g++-multilib_4.4.4-1ubuntu2_i386.deb..
[/B]What all the packages should i need to sort out the problem?

---

### Post by chili555 on 2011-04-07
> sandy@ubuntu:~$ cd '/media/SANDY/packages' 
  sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i linux-headers*
  [sudo] password for sandy: 
  Selecting previously deselected package linux-headers-2.6.35-28.
  (Reading database ... 118296 files and directories currently installed.)
  Unpacking linux-headers-2.6.35-28 (from linux-headers-2.6.35-28_2.6.35-28.49_all.deb) ...
  Setting up linux-headers-2.6.35-28 (2.6.35-28.49) ...Perfect!
  > sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i libc6-dev*
  (Reading database ... 130774 files and directories currently installed.)
  Preparing to replace libc6-dev 2.12.1-0ubuntu6 (using libc6-dev_2.12.1-0ubuntu10.1_i386(1).deb) ...
  Unpacking replacement libc6-dev ...
  Preparing to replace libc6-dev 2.12.1-0ubuntu10.1 (using libc6-dev_2.12.1-0ubuntu10.1_i386.deb) ...
  Unpacking replacement libc6-dev ...
  More than one copy of package libc6-dev has been unpacked
   in this run !  Only configuring it once.
  dpkg: dependency problems prevent configuration of libc6-dev:
   libc6-dev depends on libc6 (= 2.12.1-0ubuntu10.1); however:
    Version of libc6 on system is 2.12.1-0ubuntu6.
   libc6-dev depends on libc-dev-bin (= 2.12.1-0ubuntu10.1); however:
    Version of libc-dev-bin on system is 2.12.1-0ubuntu6.
  dpkg: error processing libc6-dev (--install):
   dependency problems - leaving unconfigured
  Errors were encountered while processing:
   libc6-devIt looks like you downloaded two versions of libc6-dev. Please do:```
sudo dpkg -r libc6-dev 2.12.1-0ubuntu[COLOR="Red"]10.1[/COLOR].deb
```Your system uses libc6-2.12.1-0ubuntu[COLOR="Red"]6[/COLOR]. Please try to install the 6 version again after you remove the 10.1 version.
  > sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i libc6-dev_2.12.1-0ubuntu10.1_i386.deb
  (Reading database ... 130774 files and directories currently installed.)
  Preparing to replace libc6-dev 2.12.1-0ubuntu10.1 (using libc6-dev_2.12.1-0ubuntu10.1_i386.deb) ...
  Unpacking replacement libc6-dev ...
  dpkg: dependency problems prevent configuration of libc6-dev:
   libc6-dev depends on libc6 (= 2.12.1-0ubuntu10.1); however:
    Version of libc6 on system is 2.12.1-0ubuntu6.
   libc6-dev depends on libc-dev-bin (= 2.12.1-0ubuntu10.1); however:
    Version of libc-dev-bin on system is 2.12.1-0ubuntu6.
  dpkg: error processing libc6-dev (--install):
   dependency problems - leaving unconfigured
  Errors were encountered while processing:
   libc6-devHandled above.
  > sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i build-essential*
  Selecting previously deselected package build-essential.
  (Reading database ... 130774 files and directories currently installed.)
  Unpacking build-essential (from build-essential_11.5_i386.deb) ...
  dpkg: dependency problems prevent configuration of build-essential:
   build-essential depends on libc6-dev | libc-dev; however:
    Package libc6-dev is not configured yet.
    Package libc-dev is not installed.
    Package libc6-dev which provides libc-dev is not configured yet.
   build-essential depends on g++ (>= 4:4.4.3); however:
    Package g++ is not installed.
   build-essential depends on dpkg-dev (>= 1.13.5); however:
    Package dpkg-dev is not installed.
  dpkg: error processing build-essential (--install):
   dependency problems - leaving unconfigured
  Errors were encountered while processing:
   build-essentialWill be solved after the issues above are solved. Then you'll need to re-install it.
  ```
sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i dpkg-dev*
  Selecting previously deselected package dpkg-dev.
  (Reading database ... 130783 files and directories currently installed.)
  Unpacking dpkg-dev (from dpkg-dev_1.15.8.4ubuntu3.1_all.deb) ...
  dpkg: dependency problems prevent configuration of dpkg-dev:
   dpkg-dev depends on libdpkg-perl (= 1.15.8.4ubuntu3.1); however:
    Package libdpkg-perl is not installed.
```Please download and install libdpkg-perl-1.15.8.4ubuntu3.1.
   ```
dpkg-dev depends on patch; however:
    Package patch is not installed.
  dpkg: error processing dpkg-dev (--install):
   dependency problems - leaving unconfigured
  Processing triggers for man-db ...
  Errors were encountered while processing:
   dpkg-dev
```Please download and install patch as request previously.
  ```
sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i g++-multilib*
  Selecting previously deselected package g++-multilib.
  (Reading database ... 130965 files and directories currently installed.)
  Unpacking g++-multilib (from g++-multilib_4.4.4-1ubuntu2_i386.deb) ...
  dpkg: dependency problems prevent configuration of g++-multilib:
   g++-multilib depends on g++ (>= 4:4.4.4-1ubuntu2); however:
    Package g++ is not installed.
   g++-multilib depends on g++-4.4-multilib (>= 4.4.4-1); however:
    Package g++-4.4-multilib is not installed.
  dpkg: error processing g++-multilib (--install):
   dependency problems - leaving unconfigured
  Errors were encountered while processing:
   g++-multilib
```It is not g++-multilib. It's g++.
  > sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -s patch
  Package `patch' is not installed and no info is available.
  Use dpkg --info (= dpkg-deb --info) to examine archive files,
  and dpkg --contents (= dpkg-deb --contents) to list their contentsPlease download and install patch.

---

### Post by jawilljr on 2011-04-07
Hey chilli,

It looks like she downloaded and installed the wrong Kernel Headers for her installed version of the kernel.

According to her post # 24 she has:

```
2.6.35-22-generic
```And she downloaded and installed:

```
linux-headers-2.6.35-28_2.6.35-28.49_all.deb
```She needs to get the right Kernel Header.

Please correct me if I'm wrong.

Jerry

---

### Post by chili555 on 2011-04-07
Quite correct! Please do so, Sandy.

---

### Post by sandy0594 on 2011-04-07
Hey chilli,i made it..i finally configured ubuntu n/w connection..
Thank you very much for your time
But,not all the packages got installed..if u have time,kindly guide me where i am wrong
```


sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i libc6-dev*
(Reading database ... 131084 files and directories currently installed.)
Preparing to replace libc6-dev 2.12.1-0ubuntu10.1 (using libc6-dev_2.12.1-0ubuntu10.1_i386.deb) ...
Unpacking replacement libc6-dev ...
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.12.1-0ubuntu10.1); however:
  Version of libc6 on system is 2.12.1-0ubuntu6.
 libc6-dev depends on libc-dev-bin (= 2.12.1-0ubuntu10.1); however:
  Version of libc-dev-bin on system is 2.12.1-0ubuntu6.
dpkg: error processing libc6-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev



```


```


sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i g++*
(Reading database ... 131084 files and directories currently installed.)
Preparing to replace g++ 4:4.4.4-1ubuntu2 (using g++_4.4.4-1ubuntu2_i386.deb) ...
Unpacking replacement g++ ...
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.4 (>= 4.4.4-1); however:
  Package g++-4.4 is not installed.
dpkg: error processing g++ (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 g++


``````


sandy@ubuntu:/media/SANDY/packages$ sudo dpkg -i libc6-dev*
(Reading database ... 131084 files and directories currently installed.)
Preparing to replace libc6-dev 2.12.1-0ubuntu10.1 (using libc6-dev_2.12.1-0ubuntu10.1_i386.deb) ...
Unpacking replacement libc6-dev ...
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.12.1-0ubuntu10.1); however:
  Version of libc6 on system is 2.12.1-0ubuntu6.
 libc6-dev depends on libc-dev-bin (= 2.12.1-0ubuntu10.1); however:
  Version of libc-dev-bin on system is 2.12.1-0ubuntu6.
dpkg: error processing libc6-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev


```As i am online now in ubuntu..kindly guide me how to get those packages from online


btw,**jawilljr **is so excited by my gender..[I] I am a male u 
[/I]

---

### Post by jawilljr on 2011-04-07
Sorry about the gender...you user name sound to me like a girls name.

My question is are you running 32 bit or 64 bit.

do this:

```
uname -a
```and post the results.

BTW you can get both versions [here.]("http://packages.ubuntu.com/maverick/linux-headers-2.6.35-22-generic")

If you're 64 bit choose AMD64, 32 bit choose I386.

Jerry

---

### Post by sandy0594 on 2011-04-07
I sorted out the issue..anyhow,here is the result:

```


sandy@ubuntu:/media/SANDY/packages$ uname -a
Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux


```

Some packages didn't install,which i posted in my last post.Can u explain me how to install those packages through online in ubuntu

---

### Post by chili555 on 2011-04-07
> As i am online now in ubuntu..kindly guide me how to get those packages from onlineWoo hoo! Glad to hear it. You can repair the installation with:```
sudo apt-get install build-essential
```Delete the files you downloaded ***if and only if*** the installation of build-essential goes well. You should be all set.

---

### Post by jawilljr on 2011-04-07
[This is what you need]("http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-22-generic_2.6.35-22.35_i386.deb")

I don't know... I will let Chiili take over again... I just wanted Chilli to know that by accident you installed the wring version of the headers.

Hope you get it working!!

Jerry

---

### Post by sandy0594 on 2011-04-07
hey chilli,

```



sandy@ubuntu:/media/SANDY/packages$ sudo apt-get install build-essential
[sudo] password for sandy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


```

---

### Post by chili555 on 2011-04-07
Please open Synaptic. Then go to Settings > Repositories. Check off everything as per attached. Close Software Sources and when prompted, press Reload. Now look for and install build-essential. Use the server location appropriate for you if it's not US.

---

### Post by sandy0594 on 2011-04-08
Hey chilli,i think it got installed..thanks anyway

---

