---
title: "Internet Connection Configuration"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by _Error_ on 2010-06-11
Hi guys, I’m new in this forum & I don't know if this is the right section to post this problem... Sorry…
   
  After searching some thread & found a few command to solve my problem, but still it didn’t solve the solution to my problem. So I decided to join the forum so that I can voice out my problem.


It’s one of my dreams to have & learn Linux so I decided to install my choice, which is Ubuntu, I have RedHat Linux CD before but it always giving me headache of how to solve the installation & have a dual boot system.


  Yesterday I decided to install Ubuntu to my PC but it will give me an error so I decided to reformat my PC and install a fresh Windows XP after that OS with complete installation including Internet connection then I install Ubuntu & succeed to have it running but after some suggestion in other thread of this forum on how to configure the Internet connection I have no luck of it because I can’t edit resolvconf or resolv.conf as well as the ndiswrapper… it always giving me a message saying that it was not install... I also do the command stated in other thread to install it but it says “command not found”.


  What I’m trying to do here is to have an Internet connection. I’ve already ping my IP with 100% OK. But I have a hard time to change the DNS figure in able to have an Internet connection.


  Any help would be really appreciated. Sorry guys I’m newbie into this OS (Ubuntu)




  Best Regards

---

### Post by ucal on 2010-06-11
Could you be more specific about what commands you're trying?  

If you want to install ndiswrapper then either:

System ---> Administration ---> Synaptic Package Manager
then search for "ndis", and mark for installation ndisgtk (which will mark the other two packages for installation as well)

or run in a terminal

sudo apt-get install ndisgtk

---

### Post by _Error_ on 2010-06-11
> **ucal said:**
> Could you be more specific about what commands you're trying?  

If you want to install ndiswrapper then either:

System ---> Administration ---> Synaptic Package Manager
then search for "ndis", and mark for installation ndisgtk (which will mark the other two packages for installation as well)

or run in a terminal

sudo apt-get install ndisgtk

   Hi,
  Thanks for the reply…
  [FONT=Verdana]I’ve try the command that you wrote as well as searching ndis at synaptic package manager but this is the message that I get.[/FONT]

[IMG]http://i47.tinypic.com/2eoxhqx.png[/IMG]

   Also here are the commands that I have use individually type in terminal window:
   
  Sudo vi /etc/resolv.conf 
   
  &
   
  sudo vi /etc/resolvconf
   
  I’ve also try this:
   
  Sudo apt-get remove dhcp-client
   
  I’ve also try this:
   
  Sudo vi /etc/network/interfaces
   
  This also:
   
  Sudo chattr +i/etc/resolv.conf
   
  Including this:
   
  Sudo cp /etc/resolvconf/resolv.conf.d/original /etc/resolvconf/resolv.conf.d/tail
   
  Here’s another command:
   
  /etc/dhcp3/dhclient.conf
   
  /etc/resolv.conf
   
  sudo chmod-w-w-w /etc/resolv.conf
  


Thanks again

---

### Post by _Error_ on 2010-06-12
Anyone can help me with my problem of having Internet connection or setup?

Thanks

---

### Post by warfacegod on 2010-06-14
Without knowing more about your situation, I'd say your looking to get wireless running. Again, I don't know what you've done before try ndiswrapper but I'd say if you have a wired connection then use it for the moment.

Go to: System> Admin.> Software Sources> Ubuntu Software tab> enable Software restricted... (Multiverse)> Other Software tab> enable "partner" (top of the list)> Updates tab> enable Unsupported... (backports)

When you click Close, it will ask you to Reload, do so. Now go to: System> Admin.> Update Manager> install all updates

Now you'll want: System Admin.> Synaptic> search for ubuntu-restricted-extras> right click it and Mark for Installation> click Apply

Finally: System> Admin.> Hardware Drivers> click Activate for the (Recommended) wireless driver, if there is one. You may want to also Activate the (Recommended) video driver, if there is one.

---

### Post by _Error_ on 2010-06-14
Hi, WarFaceGod,
  Thanks for having your attention, I really appreciate it. Unfortunately all the above command that I have been followed doesn&#8217;t work to me because of the error giving me. Yesterday I decided to uninstall the Ubuntu OS & reinstall a fresh one without configuring the ipv4 for manual configuration in able to have Internet connection.
   
  Your tutorial right now are also doesn&#8217;t work to me because I don&#8217;t have Internet connected in my Desktop PC (Ubuntu OS). This desktop PC is my main home server, which my printer are wired, connected & shared to other wireless PC. This also are having dual boot both Windows XP & Ubuntu OS & having wired (connected to router) Internet access if I&#8217;m using Windows XP but the Ubuntu doesn't have Internet access.
   
  Any other configuration in able to have Internet connection so that I can do the tutorial that you&#8217;ve asking me to do it? The Ubuntu software is downloaded to the main Ubuntu site and burn it to CD & installed it to my desktop PC. Do I miss something here so that I can get the updates from DVD/CD or this will only work if I&#8217;m having an Internet connection which now my biggest problem.

Here's 2 screenshot of the error.


[IMG]http://www.shutterspeedandaperture.com/download/ubuntu1.png[/IMG]




[IMG]http://www.shutterspeedandaperture.com/download/Screenshot-2.png[/IMG]





Thanks

---

### Post by warfacegod on 2010-06-14
Okay, I'm stumped. I don't think I've ever heard of a wired connection not working "out of the box". Let me look around for some answers.

---

### Post by warfacegod on 2010-06-14
Apparently it does happen occasionally. Try this: [http://ubuntuforums.org/showthread.php?t=1507090]("http://ubuntuforums.org/showthread.php?t=1507090")

---

### Post by _Error_ on 2010-06-14
Ok I follow the instruction posted on that link but before I continue I want to know if my Ethernet driver is the right one that I have now for Ubuntu OS because in Windows XP my driver is working properly. I'm also using D-Link router.

Please check it for me... Here's the result when a I type a few command in terminal box:

   error@ubuntu:~$ sudo ifconfig -a 
  [sudo] password for error: 
  eth0      Link encap:Ethernet  HWaddr 00:1a:92:83:08:af  
            inet6 addr: fe80::21a:92ff:fe83:8af/64 Scope:Link 
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:1876 (1.8 KB) 
            Interrupt:33 Base address:0x6000 
   
  eth1      Link encap:Ethernet  HWaddr 00:1a:92:83:17:25  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1 
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
            Interrupt:34 Base address:0xa000 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0 
            inet6 addr: ::1/128 Scope:Host 
            UP LOOPBACK RUNNING  MTU:16436  Metric:1 
            RX packets:272 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:272 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:0 
            RX bytes:24729 (24.7 KB)  TX bytes:24729 (24.7 KB) 
   
   
  I Ping the IP 127.0.0.1 & it's 100% working... now here's another answer to the command that I have made...

   
   
  error@ubuntu:~$ lshw -c 
  Hardware Lister (lshw) - B.02.14 
  usage: lshw [-format] [-options ...] 
         lshw -version 
   
              -version        print program version (B.02.14) 
   
  format can be 
              -html           output hardware tree as HTML 
              -xml            output hardware tree as XML 
              -short          output hardware paths 
              -businfo        output bus information 
   
  options can be 
              -class CLASS    only show a certain class of hardware 
              -C CLASS        same as '-class CLASS' 
              -c CLASS        same as '-class CLASS' 
              -disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
              -enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
              -quiet          don't display status 
              -sanitize       sanitize output (remove sensitive information like serial numbers, etc.) 
              -numeric        output numeric IDs (for PCI, USB, etc.) 
   
  error@ubuntu:~$ lspci -nn 
  00:00.0 Host bridge [0600]: nVidia Corporation C55 Host Bridge [10de:03a1] (rev a2) 
  00:00.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ac] (rev a1) 
  00:00.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03aa] (rev a1) 
  00:00.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a9] (rev a1) 
  00:00.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ab] (rev a1) 
  00:00.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a8] (rev a2) 
  00:00.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b5] (rev a1) 
  00:00.7 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b4] (rev a1) 
  00:01.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ad] (rev a1) 
  00:01.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ae] (rev a1) 
  00:01.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03af] (rev a1) 
  00:01.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b0] (rev a1) 
  00:01.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b1] (rev a1) 
  00:01.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b2] (rev a1) 
  00:01.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b3] (rev a1) 
  00:02.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b6] (rev a1) 
  00:02.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03bc] (rev a1) 
  00:02.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ba] (rev a1) 
  00:03.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b7] (rev a1) 
  00:06.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b9] (rev a1) 
  00:07.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03bb] (rev a1) 
  00:09.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a1) 
  00:0a.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a2) 
  00:0a.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a2) 
  00:0a.2 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:036a] (rev a2) 
  00:0b.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1) 
  00:0b.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2) 
  00:0d.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1) 
  00:0e.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2) 
  00:0e.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2) 
  00:0e.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2) 
  00:0f.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2) 
  00:11.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2) 
  00:12.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2) 
  00:13.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0376] (rev a2) 
  00:14.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0374] (rev a2) 
  00:15.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0374] (rev a2) 
  00:16.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0378] (rev a2) 
  00:17.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0375] (rev a2) 
  00:18.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0377] (rev a2) 
  01:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce 8800 GT] [10de:0611] (rev a2) 
  04:06.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005] 
  04:0b.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0) 
  0a:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce 8800 GT] [10de:0611] (rev a2) 
  error@ubuntu:~$ 



Editing in FireFox is also done.




Thanks again

---

### Post by warfacegod on 2010-06-14
Nothing sticks out to me as out of the ordinary. You should be fine. Nice video card, by the way.

---

### Post by _Error_ on 2010-06-14
> **warfacegod said:**
> Nothing sticks out to me as out of the ordinary. You should be fine. Nice video card, by the way.

Thanks... I will continue the rest of the tutorial & I let you know what's the result as soon as I finish it. By the way I got dual SLI nVidia card for my online game purposes & planning to upgrade my motherboard as well as my processor one's the price is down.

Best Regards

---

### Post by warfacegod on 2010-06-14
> **_Error_ said:**
> Thanks... I will continue the rest of the tutorial & I let you know what's the result as soon as I finish it. By the way I got dual SLI nVidia card for my online game purposes & planning to upgrade my motherboard as well as my processor one's the price is down.

Best Regards

Sounds like Compiz would totally badass with that rig.

---

### Post by _Error_ on 2010-06-14
Ok still got the problem here with the Internet connection. There's only 1 file downloaded but I can't see which folder to look at the succeeding file downloaded. All the remaining file are failed to download so I canceled it & check if my supplied ipv4 is correct in able to have Internet.

Here's the screenshot again.

[IMG]http://www.shutterspeedandaperture.com/download/faileddownload.png[/IMG]

---

### Post by warfacegod on 2010-06-14
Did you reboot?

---

### Post by _Error_ on 2010-06-14
Yes I did reboot but still not working. I've also try to hook up direct to modem without using router but it doesn't work. By the way the IP that I need to put in manual configuration in IPv4 is the IP shown in Windows XP when I type the ipconfig in CMD terminal right? Do I need to supply the MAC & DNS?

---

### Post by _Error_ on 2010-06-14
By the way I didn't install this [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) because as far as I know this is for wireless right?

---

### Post by warfacegod on 2010-06-14
Yep, that's for wireless.

Grasping at straws here. Try right clicking the Network icon and seeing Networking is enabled. If it is, try disabling wireless. Aside from that, I'm totally out of ideas. You should consider posting in the Networking & Wireless sub-forum and asking for help there posting a link to this thread.

---

### Post by _Error_ on 2010-06-14
OIC...I didn't know that there's a Networking & Wireless sub-forum... I though this is the right section for this kind of problem.

Thanks again for the help. I will try to ask my problem in that section.

---

### Post by _Error_ on 2010-06-14
Greetings,

I didn't know that there's a Networking & Wireless section to brought out my problem about my Wired Internet Connection. I'm completely new in this Ubuntu and I really want it to learn how to operate this kind of OS but I'm stuck because I can't configure my Internet connection so I decided to make a thread in [General Help Discussion]("http://ubuntuforums.org/showthread.php?t=1507661")
I really appreciate it if the moderator can move my [thread]("http://ubuntuforums.org/showthread.php?t=1507661") in this section so that I can get help.
I have a lot of information given in that [thread]("http://ubuntuforums.org/showthread.php?t=1507661") & if that is not enough let me please.

Thanks

---

### Post by Iowan on 2010-06-15
Moved/merged by request :)

---

