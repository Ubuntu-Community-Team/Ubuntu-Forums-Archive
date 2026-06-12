---
title: "DVD --&gt; AVI (DivX/Xvid)"
date: 2008-08-31
forum: Multimedia Software
---

### Post by RealG187 on 2008-08-31
I want to convert a DVD Movie into a single avi file for easier viewing.

I also want to convert a music video DVD, except I do not want the whole thing in one file, but a file for each video.

I bet in windows you have to pay for a program, so I never bothered, but now I am in the wonderful world of Linux, so I am sure there is a free program.

(Sound Converter/SoundKonverter are free, but the windows program I used wasnt)

---

### Post by thebigfatgeek on 2008-08-31
I have created a DVD::RIP PXE server that will create a cluster from a bunch of machines to do what you are intending to do quickly and easily. I have written a HOWTO if people are interested in it, which should take less than an hour to configure the first time around, and less than 5 minutes after that.

My cluster consists currently of 7 machines, one master (AMD 64 Dual Core, 512mb ram, 2 x Gb Ethernet cards, HDD and DVD-RW) and 6 nodes (AMD 64 Dual Core, 1280Mb Ram, No HDD, no DVD, PXE Ethernet card) and I am able to rip at 70fps per machine, all on a Belkin gigabit switch. A 2h30min DVD transcode in 55 minutes, and a 90min movie in 26 minutes.

The system can probably go quicker if my network could be improved, as that is my major bottleneck at present. 

The beauty of the systems is that can PXE boot any machine (even windows machines etc, with existing operating systems) and they will mount an NFS drive on the main RIP server and act as a node without any impact on their operating systems. Any server administrators with nothing to do on nightshift with a couple hundred CPU's and a nice network can now rip dvd's at the speed of light!!

Let me know if there are any interest

---

### Post by RealG187 on 2008-08-31
that's confusing, why would you need a network?

What's PXE boot?

---

### Post by thebigfatgeek on 2008-09-01
This configuration would assist you to do a very time consuming activity (3-4h) per movie much quicker. PXE is a method of allowing computers to start up using network resources rather than physical resources on the computer. It is often used in thin client-server architectures.

If you do not want to do it this way, just install DVD::RIP itself in Linux, either through Synaptics, or through the command line:

sudo apt-get install dvdrip

and then run it afterwards (under Applications->DVD::Rip)

You may have to install a number of additional programs to actually accomplish your task. Another good choice could be cinelerra, which is a Non Linear Editor, which could also be installed with Synaptics or via the command line:

sudo apt-get install cinelerra

This does require significant horsepower however to run, and is not so easy unless you know what you want to do.

A good resource for video related activities can be found at [http://www.bunkus.org/dvdripping4linux/en/separate/index.html#toc](http://www.bunkus.org/dvdripping4linux/en/separate/index.html#toc)

Good luck

---

### Post by RealG187 on 2008-09-01
How can you make the computers work together like that?

And how can you PXE boot?

---

### Post by thebigfatgeek on 2008-09-01
To boot a PC with PXE you have to have a PXE network card (most modern cards are PXE enabled) and you need to change the settings in your computer's BIOS to select the PXE network card as the first startup device in the boot sequence. This is only necessary for the cluster nodes, and not the main PC, although your main computer WILL require TWO network cards as a minimum.

You need to consult your motherboard manual here if you are uncertain on how to do this, as not all machines are the same, and you will have to have some network equipment, such as a network switch, to interconnect your PC's into a coherent network. You could use your ADSL (broadband) router as well if you have one.

The actual software configuration of your machine will take some time, and require an Ubuntu based PC, an internet connection, preferably broadband, some time and a limited amount of understanding of the Ubuntu desktop and command line environment.

If you want, I can post the howto for you in the forum. It is quite long, and I am not sure what the forum limits are

---

### Post by Mic_Droz on 2008-09-01
although the script sounds awesome, (and when i have a network, i will so totally do that... - does it work wireless?) what you need is a program called Handbrake. there is a gui for it, and you can read about it in a thread called "Handbrake now with 'real' GTK GUI" in the ubuntu forums. 

there are full instructions on how to install it from source, however, if you're not too confident of how to do that, i think there may be a .deb floating around somewhere on one of the pages...

---

### Post by ad_267 on 2008-09-01
There's a list of applications here for ripping dvds: [https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

dvdrip, ogmrip, thoggen and handbrake should do what you want.

---

### Post by axel206 on 2008-09-01
[How to backup your DVDs (in dvd, xvid, mpeg-4, x264 formats) using k9copy](http://www.my-guides.net/en/content/view/77/26/)

I think k9copy is what you are looking for. ;)

---

### Post by RealG187 on 2008-09-01
> **thebigfatgeek said:**
> To boot a PC with PXE you have to have a PXE network card (most modern cards are PXE enabled) and you need to change the settings in your computer's BIOS to select the PXE network card as the first startup device in the boot sequence. This is only necessary for the cluster nodes, and not the main PC, although your main computer WILL require TWO network cards as a minimum.

You need to consult your motherboard manual here if you are uncertain on how to do this, as not all machines are the same, and you will have to have some network equipment, such as a network switch, to interconnect your PC's into a coherent network. You could use your ADSL (broadband) router as well if you have one.

The actual software configuration of your machine will take some time, and require an Ubuntu based PC, an internet connection, preferably broadband, some time and a limited amount of understanding of the Ubuntu desktop and command line environment.

If you want, I can post the howto for you in the forum. It is quite long, and I am not sure what the forum limits are

SO the card has to have it on the client.

Thats kinda bad since the clients are usually older PCs and may not have that.

I know one of my old machines has the option to boot off the network, is that the same?

I think my school did PXE boot, but Windows was still on the hard drive. Did it boot off both (PXE and hard drive)?

Also, why would you need internet if it's just using local resources?

---

### Post by thebigfatgeek on 2008-09-03
RealG187

That is exactly what you need (PXE=network boot). So, as long as the PC bios allows you to setup network booting, you should be fine.

---

### Post by RealG187 on 2008-09-03
So that old computer allowed PXE boot?

So do I need the bios and network card to support it? What if the BIOS supported Network boot but the card didn't support PXE boot? Would network boot show up?

---

### Post by jod on 2008-10-19
> **thebigfatgeek said:**
> I have written a HOWTO if people are interested in it, which should take less than an hour to configure the first time around, and less than 5 minutes after that.


thebigfatgeek: Please post your how-to, I know that I would love to try this one out. :)

Thanks.


  Johnny

---

### Post by thebigfatgeek on 2008-10-23
I will try and do it this weekend when I am back at my PC. I am not sure if it will comply with the publishing standards, but I am sure I will be informed if I need to fix it.

---

### Post by jod on 2008-10-29
> **thebigfatgeek said:**
> I will try and do it this weekend when I am back at my PC. I am not sure if it will comply with the publishing standards, but I am sure I will be informed if I need to fix it.

We will let you know :)

Looking forward to the "how-to" :)


   Johnny

---

### Post by thebigfatgeek on 2008-10-29
**Howto: set-up your own DVD transcoding cluster**
   
  I have a 500GB XBOX, which is connected to a HDTV with composite video and optical 5.1 sound which I use to watch DVD&#8217;s, using XBMC. It is really nice system, and the only problem I have is the time it takes to transcode DVD to AVI for play on the XBOX (that, and the time it takes to copy the AVI files over FTP to the XBOX)
   
  Since I had a few AMD64 X2 Dual Core motherboards and CPU's lying around, I was looking at ways to user them in a cluster/networked environment when I came across the DVD::RIP program, and loved the idea that you could transcode with a cluster, reducing the processing time significantly.
   
  However, once I started down the process of configuring my cluster, it was to time consuming and complicated (for me in any case), and as I wanted something where I could just join a PC (node) to the cluster through PXE without affecting the current operating system on that PC (if any) and/or use diskless, headless PC's as a node in a DVD::RIP cluster.
   
  So, after many false starts I came upon DRBL through a Google search for PXE.
   
  **Starting Point:**
   
  I have decided to have a single master for DVD::RIP and DVD::RIP Clone Master, and the DRBL server, with separate nodes. 
   
  *Please note this installation is for the i386 platform, and may not work for other platforms.*
   
  **Master Server:**
   
  DRBL requires your DRBL server to have two network cards, one for the internet (you do need his if you intend to download the cluster boot images) and one for the cluster. If you do not have two network cards, this method will not work, but you can attempt two network addresses per Ethernet card (eth0 and eth0:1), but I cannot help you there
   
  So, you have your two network cards in the machine, pop the Ubuntu CD into your CD/DVD drive and install Ubuntu 8.04 Hardy Heron as normal (if you have not done so already)
   
  Once your machine is up and running and all updates installed, check that the Universe and Multiverse repositories are enabled (in my case it was by default, and you should not have any problems).
   
  If you want to, you can check this by either looking at the /etc/apt/sources.list, if you are that way inclined, or you can use the Synaptics Package Manager menus. Install the following software, the sequence is not too important:
   
  ```

  sudo apt-get install dvdrip
  sudo apt-get install gxine
  sudo apt-get install mplayer
  sudo apt-get install rar
  sudo apt-get install ogle
  sudo apt-get install vlc
```  Download libdvdcss.deb (at your own risk) from [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb) and install using debpackager (double click on the downloaded file, and it should ask you to open it with debpackager as the default, unless you have tinkered with your settings)
   
  The next section deals with the workhorse behind the whole process, namely DRBL, which stands for Diskless Remote Boot Linux
   
  Installing DRBL:
   
  The official DRBL installation how-to can be found at [http://drbl.sourceforge.net/one4all/](http://drbl.sourceforge.net/one4all/)
   
  I will reproduce the steps I needed to take to get it to work. It is surprisingly easy, considering the complexities, and I must congratulate the authors on a very useful piece of software. In any case, here goes:
   
  To allow access to their repository you have to import the key. First download the key as follow:
   
  ```
wget [http://drbl.nchc.org.tw/GPG-KEY-DRBL](http://drbl.nchc.org.tw/GPG-KEY-DRBL)
```  Thereafter, import the key with:
   
  ```
apt-key add GPG-KEY-DRBL
```  You will also have to update your repository source list. Open a terminal window, and type:
   
  ```
sudo gedit /etc/apt/sources.list
```  Once the file is displayed, scroll down to the bottom of the file, and place your cursor in a new line. Copy the two lines of text below (select/highlight the text, right click on it, and select copy) and paste it into the already open sources.list file by right clicking at the cursor and selecting paste. Once you have done that, save the file (File->Save) and close gedit.
   
  I suggest you configure your two network cards at this point in time. The one card will be used for internet access, and the other for cluster traffic. I recommend you get yourself Gigabit Ethernet cards and hubs to benefit from the speed increase. I have found my Gigabit network to be my main bottleneck on a 1 Master + 6 Node Cluster, with the network often maxing out, slowing data transfer and hence transcoding.
   
  You can configure your network in two ways, through the graphical network manager in Ubuntu, or by configuring the network interfaces by editing the /etc/network/interfaces file.
   
  I chose to use the graphical network manager after struggling for hours to configure the network in the more traditional manner.
   
  You have to select a different _private_ network for your cluster network on eth1. My ADSL router supplies DHCP to my home network in the 192.168.1.xxx range, and I set my eth1 to the following:
   
  Address: 192.168.100.1
  Netmask: 255.255.255.0
   
  To use the graphical network manager, left click the network panel indicator (normally on the top panel at the right hand side). Click on the UNLOCK button and unlock the panel with your password.
   
  You should see Wired Connection eth0 and Wired Connection eth1 in your list of network interfaces. You may have others (such as ath0 etc, but I cannot tell how well those interfaces will work)
   
  Select eth1 and click on PROPERTIES. Disable roaming mode and select Static IP address under the CONFIGURATION dropdown. In IP address type 192.168.100.1(or any other private IP address you wish, as long as it is not the same network range as eth0).
   
  If you are not sure of your network address for eth0, just open up a terminal window and type ifconfig and press enter, and you will be able to see the network configuration of your computer. 
   
  To complete the configuration on eth1, under subnet mask enter 255.255.255.0. (I am sure there are networking geniuses who could perhaps correct my choices (there may be reasons to be on another subnet mask etc that could be beneficial for performance and any input would be appreciated).
   
  Do not worry about gateway or any other information, just click OK, and close the application.
   
  Once you have done that, you could restart your network by opening your terminal window and type:
   
  ```
sudo /etc/networking restart
```  After this is completed, check your network configuration by typing ifconfig and ensure your two network cards are configured correctly.
   
  **_Installing the DRBL server_**
   
  Now it is time to download and install DRBL server. This is simply done by opening your terminal window (you can use Synaptics if you prefer) and typing:
   
  ```
sudo apt-get install drbl
```  **Configuring the DRBL server &#8211; PART 1**
   
  There are two ways of doing it (at least). One method is a step by step approach where you can configure all the settings yourself, and a second option that will configure the system to a default configuration. I will explain option 1 in more detail, and will only give a brief outline of option 2.
   
  **_Option 2 &#8211; For the impatient_**
   
  In your terminal window, type:
   
  ```
sudo /opt/drbl/sbin/drbl4imp
```  and go and have a cup of coffee (or two, depending on your download speed) whilst the boot images are downloaded, and the system configured. I have not tried this option yet, and your feedback would be appreciated if you decide to take this route.
   
  This configuration route will assume 12 cluster nodes/clients per network card (excluding eth0), and will accept all the default options (which may or may not work) for a DVD::RIP cluster. If it completes successfully, you may, or may not, have a working cluster at the end.
   
  **_Option 1 &#8211; My preferred route:_**
   
  Once you have installed the DRBL server, open your terminal window and enter:
   
  ```
/opt/drbl/sbin/drblsrv &#8211;i
```  This will start an interactive session, requiring your input. My configuration was done as follow:
   
  *Hint! When a yes/no option is available, the default value is uppercase, Ex. (y/N), the default is "N", when you press "Enter", it will use "N". If you are not sure which one to choose, you can just press "Enter" key.*
  
  ******************************************************.*
  
  ******************************************************.*
  
  *Installing DRBL for Debian Linux...*
  
  ******************************************************.*
  
  *Do you want to install those network installation boot images so that you can let client to install some GNU/Linux distributions (Debian, Ubuntu, RedHat Linux, Fedora Core, Mandriva, CentOS and OpenSuSE...) via network ?  ///NOTE/// This action will download a lot of files (> 100 MB totally) from Internet, so it might take a few minutes. If your client machine has harddisk and it is possible you will install GNU/Linux into that, say Y here. If you say "no" here, feel free to run drbl-netinstall to install them later.*
  
  [y/N] Y
   
  ******************************************************.*
  
  *This GNU/Linux distribution uses one kernel to support SMP and non-SMP arch.*
  
  ******************************************************.*
  
  *Do you want to use the serial console output for clients ?*
  
  *If you do NOT know anything about this, say "N" here, otherwise clients might show NOTHING on the screen !*
  
  [y/N] N
   
  ******************************************************.*
  
  *Which CPU architecture kernel do you want to assign for DRBL clients ?*
  
  *0 -> i386 level CPU *
  
  *1 -> i586 level CPU*
  
  *2 -> Use the same CPU level with that of this DRBL server*
  
  *Note! Note Note!  Note!  Note!  Note!  Note!*
  
  *NOTE!!! If your client machine(s) is not the same level with server, please answer "0" or "1", otherwise your client machine(s) will NOT be able to boot.*
  
  *If you use wrong CPU level kernel, the glibc and openssl package might use i686 or i386, the kernel might use i686, i586 or i386, which might be not suitable to all your machines.*
  
  *If you are not sure, "1" is recommended, this will still have good performance and compatibility.*
  
  *[1] 2*

  **[B](THIS IS IMPORTANT AS A BUG IN THE UBUNTU PACKAGE LIST CONTAINS A REFERENCE TO A MISSING LINUX-IMAGE-2.6.24-20-386, WHICH WILL CAUSE THE PROGRAM TO ABORT. I SPENT 8 HOURS, THREE COMPLETE REINSTALLS AND MANY MANY SERVER INSTALLATION ATTEMPTS TO FIND OUT WHY!!!)**[/B]

******************************************************.*
  
  *The CPU arch you specify: 0*
  
  *No optimization for your system, we will use the "i386" package.*
  
  ******************************************************.*
  
  *Cleaning the cache of apt to make some settings effect...*
  
  *Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg*
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                        *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                *
  
  *Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                     *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release                            *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release                                  *
  
  *Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                             *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                                    *
  
  *Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages                       *
  
  *Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                              *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages                              *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources                                     *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources                               *
  
  *Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources                        *
  
  *Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                         *
  
  *Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                          *
  
  *Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages                       *
  
  *Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources                        *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages                                *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources                   *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages                *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources                 *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages              *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages        *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources               *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources         *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages          *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources           *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages        *
  
  *Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources*
  
  *Hit [http://free.nchc.org.tw](http://free.nchc.org.tw) hardy Release.gpg  *
  
  *Hit [http://free.nchc.org.tw](http://free.nchc.org.tw) drbl Release.gpg*
  
  *Hit [http://free.nchc.org.tw](http://free.nchc.org.tw) hardy Release*
  
  *Hit [http://free.nchc.org.tw](http://free.nchc.org.tw) drbl Release      *
  
  *Hit [http://free.nchc.org.tw](http://free.nchc.org.tw) hardy/main Packages*
  
  *Hit [http://free.nchc.org.tw](http://free.nchc.org.tw) hardy/restricted Packages*
  
  *Hit [http://free.nchc.org.tw](http://free.nchc.org.tw) hardy/universe Packages*
  
  *Hit [http://free.nchc.org.tw](http://free.nchc.org.tw) hardy/multiverse Packages*
  
  *Hit [http://free.nchc.org.tw](http://free.nchc.org.tw) drbl/stable Packages*
  
  *Reading** package lists... Done*
  
  ******************************************************.*
  
  *Do you want to upgrade operating system ?*
  
  [y/N] 
  N
   
  ******************************************************.*
  
  *2nd, installing the necessary files for DRBL...*
  
  ******************************************************.*
  
  *Searching if lvm2 ntfs-3g lshw available... *
  
  *Package lvm2 exists in repository.*
  
  *Package ntfs-3g exists in repository.*
  
  *Package lshw exists in repository.*
  
  *Reading** package lists... Done*
  
  *Building dependency tree       *
  
  *Reading state information... Done*
  
  *util-linux is already the newest version.*
  
  *tar is already the newest version.*
  
  *gzip is already the newest version.*
  
  *bzip2 is already the newest version.*
  
  *procps is already the newest version.*
  
  *dialog is already the newest version.*
  
  *rsync is already the newest version.*
  
  *parted is already the newest version.*
  
  *pciutils is already the newest version.*
  
  *tcpdump is already the newest version.*
  
  *bc is already the newest version.*
  
  *grub is already the newest version.*
  
  *gawk is already the newest version.*
  
  *hdparm is already the newest version.*
  
  *sdparm is already the newest version.*
  
  *netcat is already the newest version.*
  
  *file is already the newest version.*
  
  *ethtool is already the newest version.*
  
  *etherwake is already the newest version.*
  
  *ssh is already the newest version.*
  
  *syslinux is already the newest version.*
  
  *mtools is already the newest version.*
  
  *Note, selecting genisoimage instead of mkisofs*
  
  *genisoimage is already the newest version.*
  
  *reiserfsprogs is already the newest version.*
  
  *e2fsprogs is already the newest version.*
  
  *psmisc is already the newest version.*
  
  *locales is already the newest version.*
  
  *wget is already the newest version.*
  
  *disktype is already the newest version.*
  
  *zip is already the newest version.*
  
  *unzip is already the newest version.*
  
  *patch is already the newest version.*
  
  *initscripts is already the newest version.*
  
  *dhcp3-server is already the newest version.*
  
  *tftpd-hpa is already the newest version.*
  
  *nfs-kernel-server is already the newest version.*
  
  *nis** is already the newest version.*
  
  *curl is already the newest version.*
  
  *lftp is already the newest version.*
  
  *iptables is already the newest version.*
  
  *libdigest-sha1-perl is already the newest version.*
  
  *lvm2 is already the newest version.*
  
  *ntfs-3g is already the newest version.*
  
  *lshw is already the newest version.*
  
  *partclone is already the newest version.*
  
  *mkpxeinitrd-net is already the newest version.*
  
  *clonezilla is already the newest version.*
  
  *mkswap-uuid is already the newest version.*
  
  *drbl-partimage is already the newest version.*
  
  *drbl-ntfsprogs is already the newest version.*
  
  *drbl-chntpw is already the newest version.*
  
  *drbl-lzop is already the newest version.*
  
  *udpcast is already the newest version.*
  
  *drbl-etherboot is already the newest version.*
  
  *freedos is already the newest version.*
  
  *0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.*
  
  ******************************************************.*
  
  ******************************************************.*
  
  *Trying to upgrade some necessary packages if available...*
  
  ******************************************************.*
  
  *In ayo repository, searching the latest  kernel ...*
  
  *The kernel image in Ubuntu 8.04 "uses generic" for i686/amd64 CPU.*
  
  *The latest kernel in the ayo repository is linux-image-2.6.24-20-generic*
  
  *There are 2 kernels available for clients, which one do you prefer ?*
  
  *[1]: kernel 2.6.24-19-generic i586 (from this DRBL server)*
  
  *[2]: linux-image-2.6.24-20-generic (from apt repository)*
  
  [1] 
  1 **[B](SELECT 1 HERE FOR THE REASONS GIVEN ABOVE)**[/B]

*Clients will use the kernel 2.6.24-19-generic i586 from server.*
  
  *It might take several minutes to install this kernel, please be patient... *
  
  *done!*
  
  ******************************************************.*
  
  *Install kernel for clients... ...*
  
  *In ayo repository, searching the latest kernel ...*
  
  ******************************************************.*
  
  *Now run: drblsrv-offline -c -d -a -l en_US -s 2.6.24-19-generic "" ""*
  
  *Using kernel from this server for client...*
  
  ******************************************************.*
  
  *The version number for your OS: Ubuntu 8.04*
  
  ******************************************************.*
  
  ******************************************************.*
  
  *Install kernel for clients... ... *
  
  *The kernel for client is copied from server.*
  
  *Installing kernel 2.6.24-19-generic for clients... *
  
  *It might take several minutes to install this kernel, please be patient... ...done!*
  
  *Generating modules.dep and map files for clients... done!*
  
  ******************************************************.*
  
  *Creating config file for PXE clients...*
  
  *Copying pxelinux.0, menu.c32, vesamenu.c32, chain.c32 and memdisk to /tftpboot/nbi_img...*
  
  *Copying memtest86+ to /tftpboot/nbi_img...*
  
  *Copying FreeDOS files to /tftpboot/nbi_img/... *
  
  *Generating default pxelinux config (/tftpboot/nbi_img/pxelinux.cfg/default)...*
  
  *Use com32 module: vesamenu.c32*
  
  *Adding menus for DRBL, local boot, memtest86+, FreeDOS...*
  
  *Adding netinstall-CentOS-4.6-i386 menu...*
  
  *Adding netinstall-CentOS-4.6-x86_64 menu...*
  
  *Adding netinstall-Debian-etch-amd64 menu...*
  
  *Adding netinstall-Debian-etch-i386 menu...*
  
  *Adding netinstall-Debian-lenny-amd64 menu...*
  
  *Adding netinstall-Debian-lenny-i386 menu...*
  
  *Adding netinstall-Fedora-9-i386 menu...*
  
  *Adding netinstall-Fedora-9-x86_64 menu...*
  
  *Adding netinstall-Mandriva-2008.1-i586 menu...*
  
  *Adding netinstall-Scientific-5.1-i386 menu...*
  
  *Adding netinstall-Scientific-5.1-x86_64 menu...*
  
  *Adding netinstall-Ubuntu-gutsy-amd64 menu...*
  
  *Adding netinstall-Ubuntu-gutsy-i386 menu...*
  
  *Adding netinstall-Ubuntu-hardy-amd64 menu...*
  
  *Adding netinstall-Ubuntu-hardy-i386 menu...*
  
  *Adding netinstall-openSUSE-10.3-i386 menu...*
  
  *Adding netinstall-openSUSE-10.3-x86_64 menu...*
  
  *done!*
  
  ******************************************************.*
  
  ******************************************************.*
  
  *Creating the image files for PXE and Etherboot client, this will take a few minutes ...*
  
  *The latest kernel for DRBL clients is 2.6.24-19-generic*
  
  *Running mknic-nbi --kernel 2.6.24-19-generic --all --no-modules*
  
  *Will client check DHCP server name is "drbl" or not: yes*
  
  *The maximum times to try to get IP address for a client: 3*
  
  *The pause time after network card is up: 0*
  
  *Setting port for udhcpc request to default...*
  
  *Using the kernel modules from /tftpboot/node_root//lib/modules...*
  
  *The selected kernel for DRBL clients is: 2.6.24-19-generic*
  
  *Kernel 2.6 is found, so default to use initramfs.*
  
  *Creating the network boot initrd for PXE clients by: mkpxeinitrd-net -k 2.6.24-19-generic -t initramfs  *
  
  *Use kernel modules from /tftpboot/node_root//lib/modules/2.6.24-19-generic.*
  
  *Creating the initRAMFS image...*
  
  *Initramfs, remove ramdisk_size/ramdisk_block in /tftpboot/nbi_img/pxelinux.cfg/default if exists...*
  
  *Finished!*
  
  *Done!*
  
  ******************************************************.*
  
  *Done!*
  
  
  **And that is part 1 done!!!**
  
  **Configuring the DRBL server &#8211; PART 2**
  
  The second part is required to create the file system used by the DVD::RIP cluster nodes. First some homework is required to allow connection between the cluster server and the nodes. To achieve this we need to configure ssh security between the server and clients.
   
  Open your terminal window again, and type:
   
  ```
ssh-keygen
``` 

**Make sure you enter nothing, nada, niks, buggerol in the passphrase**
   
  *cluster@ClusterMaster:~$ ssh-keygen*
  
  *Generating public/private rsa key pair.*
  
  *Enter file in which to save the key (/home/yourusername/.ssh/id_rsa): *
  
  *Enter passphrase (empty for no passphrase): *
  
  *Enter same passphrase again: *
  
  *Your identification has been saved in /home/yourusername/.ssh/id_rsa.*
  
  *Your public key has been saved in /home/yourusername/.ssh/id_rsa.pub.*
  
  *The key fingerprint is:*
  
  *54:8d:41:33:7a:10:bc:4b:5b:60:25:53:c6:5d:16:96 *cluster@ClusterMaster
  
  
  To ensure the system can connect with a password, we have to copy the newly created id_rsa.pub file to a new file called authorized_keys in the /home/yourusername/.ssh directory (replace cluster with your username in this case)
   
  Open your terminal window and type:
   
  ```
sudo cp /home/yourusername/.ssh/id_rsa.pub /home/yourusername/.ssh/authorized_keys
  
```  That is it. As all nodes will use the same home directory, they will automagically pick up the authorized keys from this file, and allow seamless connection to the server.
   
  To make sure the NFS folder is available to the cluster nodes, I recommend you make the following modifications to your drbl configuration file:
   
  In your terminal window, type:
   
  ```
sudo gedit /opt/drbl/conf/drbl.conf
```  Near the end of the file, look for a line that contains
   
  ```
diskless_root_dir_rw_user_add=""
```  modify this line to read
   
  ```
diskless_root_dir_rw_user_add="/home/yourusername/dvdrip-data/"
```  save the file and exit gedit.
   
  Now, to do the final configuration, in a terminal window type:
   
  ```
sudo /opt/drbl/sbin/drblpush &#8211;i
```  and follow the prompts:
   
  ********************************************************
  
  *Hint! When a yes/no option is available, the default value is uppercase, Ex. (y/N), the default is "N", when you press "Enter", it will use "N". If you are not sure which one to choose, you can just press "Enter" key.*
  
  ********************************************************
  
  *Searching the installed packages for DRBL server...This might take several minutes...*
  
  *Finished searching the installed packages for DRBL server.*
  
  ********************************************************
  
  *------------------------------------------------------*
  
  *The interactive mode let you supply the information of your DRBL environment.*
  
  *------------------------------------------------------*
  
  *------------------------------------------------------*
  
  *Please enter DNS domain (such as drbl.sf.net):*
  
  [drbl.sf.net] cluster.net **[B](THIS IS NOT TOO IMPORTANT WHAT YOU CALL IT)**[/B] 

Set DOMAIN as cluster.net
  
  ------------------------------------------------------
  
  Please enter NIS/YP domain name:
  
  [dvdcluster] 
  **Use the default entry here**
   
  *Set DOMAIN as dvdcluster*
  
  *------------------------------------------------------*
  
  *Please enter the client hostname prefix:*
  
  *This prefix is used to automatically create hostname for clients. If you want to overwrite some or all automatically created hostnames, press Ctrl-C to quit this program now, edit /opt/drbl/conf/client-ip-hostname, then run this program again.*
  
  [dvdmaster] 
  **ClusterNode (You can choose anything you want)**
   
  *Set the client hostname prefix as ClusterNode*
  *------------------------------------------------------*
  
  *Found private IP "192.168.1.11" in eth0 on your system!*
  
  *Found private IP "192.168.100.10" in eth1 on your system!*
  
  *Configured ethernet card(s) found in your system: eth0 eth1 *
  
  *------------------------------------------------------*
  
  *The public IP address of this server is NOT found.*
  
  *Which ethernet port in this server is for public Internet access, not for DRBL connection ?*
  
  *Available ethernet ports in this server:*
  
  *eth0 (192.168.1.11), eth1 (192.168.100.10), *
  
  [eth0]
  eth0 **(IMPORTANT)**
   
  *The ethernet port you choose for the WAN connection: eth0*
  
  *The ethernet port(s) for DRBL environment:  eth1 *
  
  ********************************************************
  
  ********************************************************
  
  *Now we can collect the MAC address of clients!*
  
  *If you want to let the DHCP service in DRBL server offer same IP address to client every time when client boot, and you never did this procedure, you should do it now!*
  
  *If you already have those MAC addresses of clients, you can put them into different group files (These files number is the same number of networks cards for DRBL service). In this case, you can skip this step.*
  
  *This step helps you to record the MAC addresses of clients, then divide them into different groups. It will save your time and reduce the typos.*
  
  *The MAC addresses will be recorded turn by turn according to the boot of clients,*
  
  *and they will be put into different files according to the network card in server, file name will be like macadr-eth1.txt, macadr-eth2.txt... You can find them in directory /etc/drbl.*
  
  *Please boot the clients by order, make sure they boot from etherboot or PXE!*
  
  *Do you want to collect them ?*
  
  [y/N] 
  N
   
  ********************************************************
  
  *OK! Let's continue...*
  
  ********************************************************
  
  *Do you want to let the DHCP service in DRBL server offer same IP address to the client every time when client boots (If you want this function, you have to collect the MAC addresses of clients, and save them in file(s) (as in the previous procedure)). This is for the clients connected to DRBL server's ethernet network interface eth1 ?*
  
  [y/N] 
  N
   
  ******************************************************
  
  *OK! Let's continue, we will set the IP address of clients by "first boot gets IP first" instead of fixed one!*
  
  ********************************************************
  
  *What is the initial number do you want to use in the last set of digits in the IP (i.e. the initial value of d in the IP address a.b.c.d) for DRBL clients connected to this ethernet port eth1.*
  
  [1] 
  10 
  **[B](You could use anything other than your initial ip address you set earlier, 10 is safe)**[/B]
   
  ********************************************************
  
  *How many DRBL clients (PC for students) connected to DRBL server's ethernet network interface eth1 ?*
  
  *Please enter the number: *
  
  [12] 12
  
   
  ********************************************************
  
  *The final number in the last set of digits in the clients' IP is "21".*
  
  *We will set the IP address for the clients connected to DRBL server's ethernet network interface eth1 as: 192.168.100.10 - 192.168.100.21*
  
  Accept ? [Y/n] 
  Y
   
  ********************************************************
  
  *OK! Let's continue...*
  
  ********************************************************
  
  *The Layout for your DRBL environment: *
  
  ********************************************************
  
  *          NIC    NIC IP                    Clients*
  
  *+----------------------------------+*
  
  *|         DRBL SERVER           | *
  
  *|                                               |*
  
  *|    +-- [eth0] 192.168.1.11     +- to WAN*
  
  *|                                               |*
  
  *|    +-- [eth1] 192.168.100.10 +- to clients group 1 [ 12 clients, their IP *
  
  *|                                               |            from 192.168.100.10 - 192.168.100.21]*
  
  *+----------------------------------+*
  
  ********************************************************
  
  *Total clients: 12*
  
  ********************************************************
  
  *Press Enter to continue... *
  
  
  *------------------------------------------------------*
  
  *In the system, there are 3 modes for diskless linux services:*
  
  *[0] Full DRBL mode, every client has its own NFS based /etc and /var.*
  
  *[1] DRBL SSI (Single system image) mode, every client uses tmpfs based /etc and /var. In this mode, the loading and necessary disk space of server will be lighter. NOTE! (a) The client machine memory is recommended at least 256 MB. (b) The setting and config files of client will not be saved to the DRBL server! They are just used once and will vanish after the machine shutdowns! Besides, if you modify any file in the template client (located in /tftpboot/nodes), you have to run /opt/drbl/sbin/drbl-gen-ssi-files to create the template tarball in /tftpboot/node_root/drbl_ssi/. (c) If you want to provide some file to overwrite the setting in the template tarball when client boots, check /tftpboot/node_root/drbl_ssi/clients/00_README for more details.*
  
  *[2] I do NOT want to provide diskless Linux service to client.*
  
  *Which mode do you prefer ?*
  
  [0] 
  1 
  **[B](THIS IS THE PREFERRED ROUTE IF YOU DO NOT WANT TO TOUCH THE INSTALLED OPERATING SYSTEM OF YOUR NODE, OR IF YOU USE CHEAP, DISKLESS NODES)**[/B]
  
  *DRBL SSI mode is set, an elegant mode for DRBL is on the way!*
  
  ********************************************************
  
  ********************************************************
  
  *------------------------------------------------------*
  
  *In the system, there are 3 modes available for clonezilla:*
  
  *[0] Full Clonezilla mode, every client has its own NFS based /etc and /var.*
  
  *[1] Clonezilla box mode, every client uses tmpfs based /etc and /var. In this mode, the loading and necessary disk space of server will be lighter than that in Full Clonezilla mode. Note! In Clonezilla box mode, the setting and config files of client will not be saved to the DRBL server! They just use once and will vanish after the machine shutdowns!*
  
  *[2] I do NOT want clonezilla.*
  
  *Which mode do you prefer ?*
  
  [0] 2
  
  
  *No Clonezilla is the system!*
  
  ********************************************************
  
  *------------------------------------------------------*
  
  *If there is a local harddrive with swap partition or writable file system in your client machine,*
  
  *do you want to use that swap partition or create a swap file in  the writable filesystem so that client has more memory to use ? (This step will NOT destroy any data in that harddisk)*
  
  [Y/n] 
  N
  
  *No Clonezilla is the system!*
  
  ********************************************************
  
  *------------------------------------------------------*
  
  *If there is a local harddrive with swap partition or writable file system in your client machine,*
  
  *do you want to use that swap partition or create a swap file in  the writable filesystem so that client has more memory to use ? (This step will NOT destroy any data in that harddisk)*
  
  [Y/n] N
  
  
  
  ********************************************************
  
  *------------------------------------------------------*
  
  *Which mode do you want the clients to use after they boot ?*
  
  *"1": Graphic mode (X window system) (default),*
  
  *"2": Text mode.*
  
  [1] 2
  
  
  
  *The clients will use text mode when they boot.*
  
  ********************************************************
  
  *------------------------------------------------------*
  
  *Do you want to set the root's password for clients instead of using same root's password copied from server ? (For better security)*
  
  [y/N] N       
  
   
   
  *OK! Let's continue...*
  
  *------------------------------------------------------*
  
  *Do you want to set the pxelinux password for clients so that when client boots, a password must be entered to startup (For better security)*
  
  [y/N] N
  
   
   
  *OK! Let's continue...*
  
  *------------------------------------------------------*
  
  *Do you want to set the boot prompt for clients ?*
  
  [Y/n] Y
  
   
   
  *How many 1/10 sec is the boot prompt timeout for clients ?*
  
  [70] 10
  
   
   
  *OK! Let's continue...*
  
  *------------------------------------------------------*
  
  *------------------------------------------------------*
  
  *Do you want to use graphic background for PXE menu when client boots ?*
  
  *Note! If you use graphical PXELinux menu, however client fails to boot, you can switch to text mode by running "/opt/drbl/sbin/switch-pxe-bg-mode -m text".*
  
  [y/N] N
  
   
   
  *Use graphic PXE Linux menu for client.*
  
  *------------------------------------------------------*
  
  *------------------------------------------------------*
  
  *Do you want to let audio, cdrom, floppy, video and plugdev (like USB device) open to all users in the DRBL client ? If yes, we will add all the users to those device groups in the server and client.*
  
  [Y/n] N
  
  
  
  *------------------------------------------------------*
  
  *By using alias interface, every client can have 2 IPs,*
  
  *one of them is private IP for clients connected to DRBL server, and the other is public IP for clients directly connected to WAN from switch!*
  
  *Do you want to setup public IP for clients ?*
  
  [y/N] N
  
   
   
  *------------------------------------------------------*
  
  *Do you want to let DRBL clients have an option to run terminal mode ? i.e. you want to let that client run remote display (which will mostly use resources of server), say "Y" here.*
  
  *Note!*
  
  *0. If you say yes to this option, this will be a very limited environment for client, i.e. NO local access for USB, CD, audio, printer, etc. in client.*
  
  *1. If your server is not powerful, say "no" here.*
  
  *2. By saying "yes" here, we will turn on xdmcp,*
  
  *It is never a safe thing to turn on that.  Setting up /etc/hosts.allow and /etc/hosts.deny to only allow local access is another alternative but not the safest.*
  
  *Firewalling port 177 is the safest if you wish to have xdmcp on.*
  
  *Read the manual for more notes on the security of XDMCP.*
  
  *Please set it by yourself!*
  
  *3. If you say "yes" here, you might have to restart your desktop environment manager (gdm/kdm) later, remember to save your data before you close applications!*
  
  *Do you want to let client has an option to run terminal mode ?*
  
  [y/N] N
  
   
   
  *OK! Let's continue...*
  
  *------------------------------------------------------*
  
  *------------------------------------------------------*
  
  *Do you want to let DRBL server as a NAT server ? If not, your DRBL client will NOT be able to access Internet.*
  
  [Y/n] N
  
   
  *This DRBL server does NOT provide NAT service, so your DRBL client will NOT be able to access Internet.*
  
  ********************************************************
  
  *The running kernel in the server supports NFS over TCP!*
  
  *Note! If you change the running kernel in the server, and not sure whether the kernel supports NFS over udp or tcp, you'd better to re-run "drblpush -i" again to avoid the client boots in failure!*
  
  *Press Enter to continue.*.. 
  
   
  *------------------------------------------------------*
  
  *Searching installed Etherboot files for dhcpd.conf... done! *
  
  ********************************************************
  
  *The calculated NETWORK for eth1 is 192.168.100.0.*
  
  ** The client IP address you assigned is same with nfsserver: 192.168.100.10, *
  
  * ---> the next IP address (192.168.100.11) will be used for that client!*
  
  ********************************************************
  
  ********************************************************
  
  *We are now ready to deploy the files to system! *
  
  *Do you want to continue ?*
  
  *Warning! If you go on, your firewall rules will be overwritten during the setup!*
  
  *The original rules will be backed up as iptables.drblsave in system config directory (/etc/sysconfig or /etc/default).*
  
  [Y/n] 
  Y
   
  *------------------------------------------------------*
  
  *Checking the necessary disk space... done!*
  
  *Copying the config file to /etc/drbl... done!*
  
  *Backup the original /etc/hosts as /etc/hosts.drblsave... done!*
  
  *Generate the /etc/hosts for clients connected to eth1... done!*
  
  *Cleaning the stale files of the diskless nodes if they exist... done!*
  
  ******************************************************.*
  
  ******************************************************.*
  
  *The version number for your GNU/Linux: DBN-TU*
  
  *Completely cleaning old common root files if they exist... done !*
  
  *Completely cleaning old nodes if they exist... done !*
  
  *Creating common root files... This might take several minutes........... done!*
  
  *Update the kernel for client if necessary... *
  
  *The DRBL client uses i586 kernel with version 2.6.24-19-generic...*
  
  *Trying to update the /tftpboot/node_root/lib/modules/2.6.24-19-generic from server's /lib/modules/... This might take several minutes...*
  
  *Found kernel modules in /lib/modules/2.6.24-19-generic and its arch "i586" matches client's "i586"...*
  
  *Syncing /lib/modules/2.6.24-19-generic to client's common root...*
  
  *Syncing /boot/*-2.6.24-19-generic* to client's common root...*
  
  *Generating the /tftpboot/node_root/lib/modules/2.6.24-19-generic/modules.dep*
  
  *Copying the directory /etc/ to clients common root /tftpboot/node_root...*
  
  *Cleaning the ssh key file ssh_host_dsa_key copied from server... done!*
  
  *Cleaning the ssh key file ssh_host_dsa_key.pub copied from server... done!*
  
  *Cleaning the ssh key file ssh_host_rsa_key copied from server... done!*
  
  *Cleaning the ssh key file ssh_host_rsa_key.pub copied from server... done!*
  
  *Commenting the TCPwrapper related file /tftpboot/node_root/etc/hosts.deny copied from server... done!*
  
  *Commenting the TCPwrapper related file /tftpboot/node_root/etc/hosts.allow copied from server... done!*
  
  *The startup services for DRBL client are:*
  
  *firstboot portmap nis nfs-common ssh hal dbus acpid acpi-support usplash cupsys drblthincli arm-wol sendsigs umountfs*
  
  *Using udev for clients... Set text mode for Debian DRBL client...*
  
  *Deleting the accounts (except root) in the clients common root template... done!*
  
  *Enabling the NIS client in the common root template... done!*
  
  *Creating some necessary files in the clients common root template....... done!*
  
  *Creating DRBL client: ClusterNode111 192.168.100.11... Generating SSH host keys for client 192.168.100.11 if they do not exist... done!*
  
  *Display manager:"gdm"...*
  
  *Setting node 192.168.100.11 as normal_login... done!*
  
  *Creating DRBL client: **_ClusterNode112_** 192.168.100.12... Pseudo client is created for DRBL SSI or clonezilla box mode! done!*
  
  *Creating DRBL client: ClusterNode113 192.168.100.13... Pseudo client is created for DRBL SSI or clonezilla box mode! done!*
  
  *Creating DRBL client: ClusterNode114 192.168.100.14... Pseudo client is created for DRBL SSI or clonezilla box mode! done!*
  
  *Creating DRBL client: ClusterNode115 192.168.100.15... Pseudo client is created for DRBL SSI or clonezilla box mode! done!*
  
  *Creating DRBL client: ClusterNode116 192.168.100.16... Pseudo client is created for DRBL SSI or clonezilla box mode! done!*
  
  *Creating DRBL client: ClusterNode117 192.168.100.17... Pseudo client is created for DRBL SSI or clonezilla box mode! done!*
  
  *Creating DRBL client: ClusterNode118 192.168.100.18... Pseudo client is created for DRBL SSI or clonezilla box mode! done!*
  
  *Creating DRBL client: ClusterNode119 192.168.100.19... Pseudo client is created for DRBL SSI or clonezilla box mode! done!*
  
  *Creating DRBL client: ClusterNode120 192.168.100.20... Pseudo client is created for DRBL SSI or clonezilla box mode! done!*
  
  *Creating DRBL client: ClusterNode121 192.168.100.21... Pseudo client is created for DRBL SSI or clonezilla box mode! done!*
  
  *Creating DRBL client: ClusterNode122 192.168.100.22... Pseudo client is created for DRBL SSI or clonezilla box mode! done!*
  
  *Template client for DRBL SSI is 192.168.100.11*
  
  *Using template host /tftpboot/nodes/192.168.100.11*
  
  *Generating SSH host keys for client 192.168.100.11 if they do not exist... done!*
  
  *Generating the files for DRBL single system image template... etc... var... opt/drbl... Root's openssh public key... done!*
  
  *Disable the password in pxelinux simple menu for all clients... *
  
  *Disabling PXE password in config file /tftpboot/nbi_img/pxelinux.cfg/default... *
  
  *done!*
  
  *Now add necessary services to this DRBL server: DHCP, TFTP, NFS, NIS...*
  
  *Generating the NFS exports for DRBL clients... *
  
  *Backup the original /etc/exports as /etc/exports.drblsave*
  
  *Exporting to clients by IP address line-by-line...*
  
  *The /etc/exports setting is ok now!*
  
  *This DRBL server does NOT provide NAT service, so your DRBL client will NOT be able to access Internet.*
  
  *Now stop the NAT service...*
  
  *Flushing** firewall rules: success*
  
  *Now set the YP securenets...*
  
  *Backup the original /etc/ypserv.securenets as /etc/ypserv.securenets.drblsave*
  
  *The /etc/ypserv.securenets setting is done!*
  
  *Update YP...*
  
  *Now add the service:  portmap dhcp3-server nis nfs-common nfs-kernel-server tftpd-hpa drbl-clients-nat*
  
  *Force to add portmap service in this Debian DRBL server...*
  
  *Force to add dhcp3-server service in this Debian DRBL server...*
  
  *Force to add nis service in this Debian DRBL server...*
  
  *Force to add nfs-common service in this Debian DRBL server...*
  
  *Force to add nfs-kernel-server service in this Debian DRBL server...*
  
  *Force to add tftpd-hpa service in this Debian DRBL server...*
  
  *Force to add drbl-clients-nat service in this Debian DRBL server...*
  
  *Now start the service:  portmap dhcp3-server nis nfs-common nfs-kernel-server tftpd-hpa drbl-clients-nat*
  
  * * Stopping portmap daemon...                                                                            [ OK ] *
  
  * * Starting portmap daemon...                                                                            [ OK ] *
  
  * * Stopping DHCP server dhcpd3                                                                           [ OK ] *
  
  * * Starting DHCP server dhcpd3                                                                           [ OK ] *
  
  * * Starting NIS services                                                                                 [ OK ] *
  
  * * Stopping NFS common utilities                                                                         [ OK ] *
  
  * * Starting NFS common utilities                                                                         [ OK ] *
  
  * * Stopping NFS kernel daemon                                                                            [ OK ] *
  
  * * Unexporting directories for NFS kernel daemon...                                                      [ OK ] *
  
  * * Exporting directories for NFS kernel daemon...                                                        [ OK ] *
  
  * * Starting NFS kernel daemon                                                                            [ OK ] *
  
  *Restarting HPA's tftpd: in.tftpd.*
  
  *Stopping the NAT services for DRBL clients... Now stop the NAT service...*
  
  *Flushing** firewall rules: success*
  
  *done!*
  
  *Starting the NAT services for DRBL clients... done!*
  
  *Turn on ip_forward now.*
  
  *The display manager in this DRBL server is "gdm"*
  
  *The GDM remote access in the DRBL server is already off!*
  
  *Disable the terminal mode for DRBL clients ...*
  
  *done !*
  
  *Clean all the previous saved config file if they exist...done!*
  
  *Turn on the boot prompt for PXE client...done!*
  
  *Turn off the thin client option in PXE boot menu...done!*
  
  *Modifying /tftpboot/nbi_img/pxelinux.cfg/default to let DRBL client use text PXE boot menu... done!*
  
  *DRBL SSI mode. Set clientdir opt for label drbl in pxelinux config... *
  
  *Setting drbl_mode="drbl_ssi_mode" in /etc/drbl/drbl_deploy.conf and /etc/drbl/drblpush.conf... done!*
  
  *Clonezilla service is set as unavailable. Set clientdir opt for label clonezilla in pxelinux config... *
  
  *Setting clonezilla_mode="none" in /etc/drbl/drbl_deploy.conf and /etc/drbl/drblpush.conf... done!*
  
  ******************************************************.*
  
  *Enjoy DRBL!!!*
  
  *[http://drbl.nchc.org.tw;](http://drbl.nchc.org.tw;) [http://drbl.sf.net](http://drbl.sf.net)*
  
  *NCHC Free Software Labs, Taiwan. [http://free.nchc.org.tw](http://free.nchc.org.tw)*
  
  ******************************************************.*
  
  *If you like, you can reboot the DRBL server now to make sure everything is ready...(This is not necessary, just an option.).*
  
  ******************************************************.*
  
  *DRBL server is ready! Now set the client machines to boot from PXE or Etherboot (refer to [http://drbl.sourceforge.net](http://drbl.sourceforge.net) for more details).*
  
  *NOTE! If Etherboot is used in client machine, version 5.4.0 or newer is required!*
  
  *PS. The config file is saved as /etc/drbl/drblpush.conf. Therefore if you want to run drblpush with the same config again, you may run it as: /opt/drbl/sbin/drblpush -c /etc/drbl/drblpush.conf*
  
  
  **[B]THAT IS IT, THE DRBL SERVER IS ACTIVE AND WAITING FOR CLIENTS!!!**
  **You can at anytime rerun both Part 1 and Part 2 to change or fix your configuration.**[/B]
  
  **[B]Configuring the NODES**[/B]
  
  To use the server, you will have to configure your nodes to boot with PXE (over ethernet). This is set in your computer's BIOS, which is accessed normally by pushing DEL or F2 or whatever weird keystroke combination the manufacturers of your motherboard chose to use. Please see your manual for your motherboard or a friend to help you in this regard.
   
  Once they are configured to PXE boot, the work is done. Make sure they are connected to each other through a network switch or a router, and you could technically let RIP.
   
  **[B]Configuring DVD::RIP**[/B]
  
  You have to do some work on DVD::RIP to work. One is to ensure all the dependencies are satisfied, and the section part is to configure the different nodes.
   
  **[B]Check the dependencies:**[/B]
   
  Open up DVD::RIP, it is normally under Applications->Sound & Video
   
  In the DVD::RIP menu select Edit->Preferences
   
  Under the Basic Settings tab, ensure your Default Data Base Directory and Default Directory for .rip Project Files are both set to the same as what you have specified previously, namely /home/yourusername/dvdrip-data. You may have to create the directory if it does not exist yet. 
   
  Select the Commands tab, and change xine to gxine for the STDIN player command
   
  Once all the above changes have been made, click the CHECK ALL SETTINGS button and ensure there are no errors displayed. If no errors are displayed, click on OK to close the Preferences window.
   
  **Setting up the Cluster**
   
  The moment you all have been waiting for is here. In the DVD::RIP menu select Cluster->Cluster Control. You may sometimes get an error message saying &#8220;Can't start local master daemon on port 28646.  Execute the dvdrip-master program by hand to see why it doesn't run.&#8221; 
   
  This is not a crisis, and all you have to do is to open a terminal window and type:
   
  ```
dvdrip-master 2
```  and you are good to go. A new window will open &#8220;dvd::rip Cluster Control&#8221;, which is the main cluster control screen you will use to configure, control and transcode projects with, using your cluster.
   
  If your Cluster master daemon started automatically, you can skip the next step. For those who had to manually start the daemon, select Master->Connect Master Daemon here from the menu.
   
  **Setting nodes in DVD::RIP cluster**
   
  Once that is out of the way, time to add some nodes. Now assume we have two nodes, all ready PXE booted and somewhere on your ethernet. As we have previously set the prefix to our nodes as ClusterNode, and we set our IP address range for our nodes from 192.168.100.11 to 192.168.100.22 (12 clients, see above), your clusters will be named from ClusterNode111 to ClusterNode122. The first two nodes will be ClusterNode122 and ClusterNode121 respectively.
   
  Select Node->Add Nodes from the top menu, and enter the following data:
   
  ```

  Name                                     = ClusterNode122
  Hostname                               = ClusterNode122
  Local Data Directory                = /home/yourusername/dvdrip-data
  Username to connect with SSH = yourusername
  
```Click on the TEST SETTINGS button and a window should open asking you if you are sure about your marriage, ssh connections etc etc. In the entry box type &#8220;yes&#8221; and press Enter, and your node should be added at this stage. 
   
  If there is a problem ensure you have done the ssh settings as described above, and the data directory has been created. To ensure your node is active, open a terminal window and type:
   
  ```
ping 192.168.100.22
```  for ClusterNode122 etc. If you see a ping response, you know the node is alive and kicking.
   
  **[B]Repeat this for all your other nodes**[/B]
   
  If everything works as expected, you should see all your nodes as idle, like you, waiting for something to happen.
   
  From here on rip your movie as normal with DVD::RIP. Once they are ripped, and you are ready to transcode, select the ADD to CLUSTER button, switch to your Cluster Control screen, select the project and click on the START PROJECT, and your cluster should fly off and transcode in warp speed.
   
  **Performance**
   
  I have been able to rip and transcode a 2.5h movie to xvid in 55 minutes, and a 1.5h movie in 26 minutes, so you can see the benefits clearly. For an excellent guide to Linux DVD conversion see [http://www.bunkus.org/dvdripping4linux/en/separate/index.html#toc](http://www.bunkus.org/dvdripping4linux/en/separate/index.html#toc)
   
  Hope this helps all of you to use those spare machines lying around to convert a DVD quickly when you need to. I am able to run 10 nodes from my main Ubuntu box, without any impact, and as I do not use the main box as a node (which you can do just as you would for any other node) it does not impact on my normal use of that PC (except whilst ripping the DVD initially)

Good luck and I hope it works for you.

---

### Post by RealG187 on 2008-10-29
Can the original Xbox connect using an HD interface? I have my chipped one and a freind's softmodded one with a broken power supply.

---

### Post by thebigfatgeek on 2008-10-30
Yes it can, but you will need a special connector (to replace the standard composite connector) that you often find on ebay. The original HIGH DEFINITION AV Pack from Microsoft in my opinion is the best, but they are scarce. It allows 1080i resolution and 5.1 optical surround sound, and XBMC looks stunning in that configuration.

See for an example: 

[http://cgi.ebay.it/XBox-High-Definition-Video-HDTV-AV-Pack-Pak-HD-TV-Cable_W0QQitemZ130253140852QQcmdZViewItem?hash=ite%20m130253140852&_trkparms=72%3A1025|39%3A1|66%3A2|65%3A12|240%3A13%2018&_trksid=p3286.c0.m14](http://cgi.ebay.it/XBox-High-Definition-Video-HDTV-AV-Pack-Pak-HD-TV-Cable_W0QQitemZ130253140852QQcmdZViewItem?hash=ite%20m130253140852&_trkparms=72%3A1025|39%3A1|66%3A2|65%3A12|240%3A13%2018&_trksid=p3286.c0.m14)

---

### Post by RealG187 on 2008-10-31
How come that is not in English? Is there an English thing on eBay?

---

### Post by sosaudio1 on 2008-11-09
Holy cow....GEEEEEEEK....whatta tutorial...if there are any mods looking at this thread, can we take that tutorial by itself out of this and make a sticky???? That is excellent stuff.

Sooo if I am looking at this right, I can stick a DVD into one of the other systems in the backend server and then have it viewable to TV for example on one of the headless system frontends, correct???

---

### Post by marius.theron on 2009-01-07
> **thebigfatgeek said:**
> I have created a DVD::RIP PXE server that will create a cluster from a bunch of machines to do what you are intending to do quickly and easily. I have written a HOWTO if people are interested in it, which should take less than an hour to configure the first time around, and less than 5 minutes after that.

My cluster consists currently of 7 machines, one master (AMD 64 Dual Core, 512mb ram, 2 x Gb Ethernet cards, HDD and DVD-RW) and 6 nodes (AMD 64 Dual Core, 1280Mb Ram, No HDD, no DVD, PXE Ethernet card) and I am able to rip at 70fps per machine, all on a Belkin gigabit switch. A 2h30min DVD transcode in 55 minutes, and a 90min movie in 26 minutes.

The system can probably go quicker if my network could be improved, as that is my major bottleneck at present. 

The beauty of the systems is that can PXE boot any machine (even windows machines etc, with existing operating systems) and they will mount an NFS drive on the main RIP server and act as a node without any impact on their operating systems. Any server administrators with nothing to do on nightshift with a couple hundred CPU's and a nice network can now rip dvd's at the speed of light!!

Let me know if there are any interest

Hi!

I'm definitely interested! At present I'm a windows user, but love reading anything linux/ unix related... Have installed Ubuntu64 on a spre machine and found it adequate...

I do a lot of divx conversions and need a faster solution. Have x10 462 boards with 3Ghz Bartons and 512Mb DDR400 to assemble...

Considering to fit in a single case... any pointers?

Thanx!

---

### Post by evilempire on 2009-01-07
To answer the OP's first question, there is now a Ubuntu version of the ever so wonderful app Handbrake. It's a Mac OS X app that pretty much just does DVD to Avi/MP4 type files. You can find the package here:

[http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)

---

