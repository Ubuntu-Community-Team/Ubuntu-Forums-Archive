---
title: "Nvidia geforce 310m goes to blank screen"
date: 2010-12-19
forum: Multimedia Software
---

### Post by crownclown on 2010-12-19
Im using nvidia geforce 310M cuda..
The additional driver for nvidia is available...
but after the installation then after reboot it just ***e a blank screen..:cry:
so i reformat it..but this time i dont install the nvidia driver...
what should i do.

---

### Post by tjones00 on 2010-12-19
You most likely downloaded the driver from the Nvidia website and didn't install it properly being sure to blacklist the opensource drivers eliminating any conflicts.

Try using the Ubuntu Nvidia proprietary drivers available via Hardware Drivers this will ensure the driver is installed properly.

[http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+drivers](http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+drivers)

Above is a link to a recent guide to installing the recent Nvidia drivers from Nvidia just follow the instructions in post #1. The guide was written for Ubuntu 10.04 but it should still work for 10.10.

If you still receive errors try using the kernel boot parameters nomodeset and noplymouth.

---

### Post by crownclown on 2010-12-19
> **tjones00 said:**
> You most likely downloaded the driver from the Nvidia website and didn't install it properly being sure to blacklist the opensource drivers eliminating any conflicts.

Try using the Ubuntu Nvidia proprietary drivers available via Hardware Drivers this will ensure the driver is installed properly.

[http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+drivers](http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+drivers)

Above is a link to a recent guide to installing the recent Nvidia drivers from Nvidia just follow the instructions in post #1. The guide was written for Ubuntu 10.04 but it should still work for 10.10.

If you still receive errors try using the kernel boot parameters nomodeset and noplymouth.

well so i dont need to install from the additional drivers?
because after i install then reboot it just a blank screen..

---

### Post by cascade9 on 2010-12-19
What laptop is it?

There is a chance that you've got 'switchable' graphics (both intel and nvidia).

---

### Post by crownclown on 2010-12-19
> **cascade9 said:**
> What laptop is it?

There is a chance that you've got 'switchable' graphics (both intel and nvidia).

my laptop is asus a42j 
processor i5
graphic nvidia geforce 310m cuda

---

### Post by cascade9 on 2010-12-19
#%&#%&# asus making that many variant on the A42J. 

From the looks of this forum post, the version you have does have switchable graphics- 

[http://forums.hardwarezone.com.sg/showthread.php?t=2987049](http://forums.hardwarezone.com.sg/showthread.php?t=2987049)

---

### Post by crownclown on 2010-12-19
> **cascade9 said:**
> #%&#%&# asus making that many variant on the A42J. 

From the looks of this forum post, the version you have does have switchable graphics- 

[http://forums.hardwarezone.com.sg/showthread.php?t=2987049](http://forums.hardwarezone.com.sg/showthread.php?t=2987049)

the link show that he using the windows...
but i dont have problem with windows...everything is fine...just inside the ubuntu..
i've try on 10.04 and now 10.10..both same..the driver can be install fom the additional driver it detect by itself.
just after reboot then it blank...so exactly what is this switchable graphic ?
isit the intel and nvidia?

---

### Post by Yellow Pasque on 2010-12-19
Post output of:
```
lspci
```

---

### Post by crownclown on 2010-12-19
> **Temüjin said:**
> Post output of:
```
lspci
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
07:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

---

### Post by cascade9 on 2010-12-20
> **crownclown said:**
> 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)

Yep, thats switchable graphics (aka 'optimus'), and heres the bad news- 

>  				 				[**AaronP**]("http://www.nvnews.net/vbulletin/member.php?u=41053") 				 				 			
  			NVIDIA Corporation
 			 			  			 				 					 
[[IMG]http://www.nvnews.net/vbulletin/image.php?u=41053&dateline=1207120136[/IMG]]("http://www.nvnews.net/vbulletin/member.php?u=41053") 				
 			  			 				 
				Join Date: Mar 2005
 				 				 				 					Posts: 2,240 				
 				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				[IMG]http://www.nvnews.net/vbulletin/images/icons/icon1.gif[/IMG] 				**Re: Optimus support for Linux** 			
 			 			 		  		 		We have no plans to support Optimus on Linux at this time.


[http://www.nvnews.net/vbulletin/showthread.php?t=144750](http://www.nvnews.net/vbulletin/showthread.php?t=144750)

There migth be some software or BIOS hacks to let you use the nVidia graphics + driver, but I dont know anything about that, sorry.

---

### Post by BicyclerBoy on 2010-12-20
Shame you didn't state what your hardware really was from the start..

You can try to enable the nvidia graphics in the bios.
Some laptop bios (optimus) allow you to force the nvidia GPU on only so the i5 GPU is off.

Optimus as such will not work just yet or ever...

---

### Post by theasprint on 2010-12-20
Hi,

As my signature suggests, I can help.

Please go to this link. [http://ubuntuforums.org/showthread.php?t=1648734](http://ubuntuforums.org/showthread.php?t=1648734)

In the thread, there will be another link. Do navigate there for clearer instructions.

And BTW, I also went to search for your Nvidia Driver.
Here is the link: [http://www.nvidia.com/object/linux-display-ia32-260.19.29-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.29-driver.html)   (This is 32-bit version)

Just follow my instructions in the first link i gave you.

If there is any problems, please report back. 

So far I have not seen problems after people followed my instructions.
I did the same procedure for my Nvidia GT 330M card and it worked! (Despite the link saying Nvidia GeForce 4 problem)

Good Luck :D

---

### Post by cascade9 on 2010-12-20
@ theasprint- um, no, that wont work. The issue here is optimus, and just disabling GDM and then installing is NOT going to help. 

> **BicyclerBoy said:**
> You can try to enable the nvidia graphics in the bios.
Some laptop bios (optimus) allow you to force the nvidia GPU on only so the i5 GPU is off.

If you've got that option, then the nvidia drivers will work. If you, then I dont know.

---

### Post by theasprint on 2010-12-20
Awww, I read somewhere that Optimus graphics are active by default, in the BIOS. Seriously.

And how did Nvidia.com manage to provide the driver for 310M Linux version if they don't support Optimus? You mean that there is a non-optimus 310M version also on sale?

---

### Post by cascade9 on 2010-12-20
> **theasprint said:**
> Awww, I read somewhere that Optimus graphics are active by default, in the BIOS. Seriously.

And how did Nvidia.com manage to provide the driver for 310M Linux version if they don't support Optimus? You mean that there is a non-optimus 310M version also on sale?

AFAIK optimus BIOS settings vary from manufaturer/series. 

Yes, there is versions of the 310M without intel graphics as well (ie, not optimus).

---

### Post by crownclown on 2010-12-20
cascade9 : hey thx man..at least u try to help me...

theasprint  : ohh...i will try it..after u state the link and read the solve problem that u help,give me more  
                    confident to try it..if anything i will report in..

bicyclerboy : well im so sry..im just a newbie user of ubuntu..this is my first time using it,,well saw my friend  
                      is using it..i've started to learn about ubuntu now..at least i learn something from u guys ..thx  
                      again guys..

---

### Post by crownclown on 2010-12-20
Seems that i got this problem....

[IMG]http://i377.photobucket.com/albums/oo218/noob_crown/Screenshot-1-1.png[/IMG]

---

### Post by cascade9 on 2010-12-20
You cant install nVidia drivers with x (desktop) running. 

I think that if you do install the nvidia drivers, you wont get back to the desktop anyway, optimus wont work. 

About all you can do is look in your BIOS and see if there is a way to force the laptop to use just the nvidia GPU.

---

### Post by crownclown on 2010-12-20
> **cascade9 said:**
> You cant install nVidia drivers with x (desktop) running. 

I think that if you do install the nvidia drivers, you wont get back to the desktop anyway, optimus wont work. 

About all you can do is look in your BIOS and see if there is a way to force the laptop to use just the nvidia GPU.

nope check already..there is no graphic can be changed..T.T

---

### Post by BicyclerBoy on 2010-12-21
Well just stick to the intel i5 graphics then. The intel drivers are in better shape.

I have heard rumours that the expert's have got optimus working with linux.
I believe (status now) you have to reboot to change from i5 CPU&GPU to i5-CPU & nvidia-GPU.

This could be 6 - 12 months before 'appearing in a laptop near you'..

Nvidia may realise it is better for their image/reputation to fix this in their driver but it was never their fault.

Nvidia made it very clear that optimus was not supported in linux.

People buy computer hardware with windows OS ($$) with no thought given to the fact that the hardware can not run anything else.

---

### Post by cascade9 on 2010-12-21
@ crownclown- Opps. I just looked at the screenshot you posted,a nd realise something- you were posting commands that should have gone into terminal into gedit by mistake. 

This is what terminal looks like- 

[IMG]http://vpnblog.info/wp-content/uploads/ubuntu10.10_strongvpn/ubuntu10_openvpn_step1.jpg[/IMG]

> **BicyclerBoy said:**
> Well just stick to the intel i5 graphics then. The intel drivers are in better shape.

I have heard rumours that the expert's have got optimus working with linux.
I believe (status now) you have to reboot to change from i5 CPU&GPU to i5-CPU & nvidia-GPU.

This could be 6 - 12 months before 'appearing in a laptop near you'..

Nvidia may realise it is better for their image/reputation to fix this in their driver but it was never their fault.

Nvidia made it very clear that optimus was not supported in linux.

People buy computer hardware with windows OS ($$) with no thought given to the fact that the hardware can not run anything else.

Intel graphics are fine, if you dont want to play games (Intel video is slower than a snail), dont like watching video (VDPAU is great), and in the case of optimus, dont mind paying extra for something you cant use. 

Interesting that somebody might have got optimus working with linux. We'll see how that goes. 

I totally disagree, it IS 'nVidias fault'. AFAIK, optimus was made with minimal/no intel support. So, they should have made linux drivers. Simple. 

You cant push all the blame onto the consumer. Take a look at this asus page-

[http://www.asus.com/product.aspx?P_ID=1jsZM3TQdv4XtBZV&content=overview](http://www.asus.com/product.aspx?P_ID=1jsZM3TQdv4XtBZV&content=overview)

(If aus.com does its usual and stuffs the link, its the page for teh A42JC), Where on that page does it say 'optimus', 'switchable grpahics' or give you any idea that its there? 

If somebody knew that linux normally works with nVidia, saw that page, there would be no warning about possible difficulty with optimus.  

Even if they looked at reviews online, you'd need to find a (proper) linux specific review to know about possible optimus issues with linux. Its an 'in the know' problem really......

---

### Post by crownclown on 2010-12-21
> **cascade9 said:**
> @ crownclown- Opps. I just looked at the screenshot you posted,a nd realise something- you were posting commands that should have gone into terminal into gedit by mistake. 

This is what terminal looks like- 

[IMG]http://vpnblog.info/wp-content/uploads/ubuntu10.10_strongvpn/ubuntu10_openvpn_step1.jpg[/IMG]



Intel graphics are fine, if you dont want to play games (Intel video is slower than a snail), dont like watching video (VDPAU is great), and in the case of optimus, dont mind paying extra for something you cant use. 

Interesting that somebody might have got optimus working with linux. We'll see how that goes. 

I totally disagree, it IS 'nVidias fault'. AFAIK, optimus was made with minimal/no intel support. So, they should have made linux drivers. Simple. 

You cant push all the blame onto the consumer. Take a look at this asus page-

[http://www.asus.com/product.aspx?P_ID=1jsZM3TQdv4XtBZV&content=overview](http://www.asus.com/product.aspx?P_ID=1jsZM3TQdv4XtBZV&content=overview)

(If aus.com does its usual and stuffs the link, its the page for teh A42JC), Where on that page does it say 'optimus', 'switchable grpahics' or give you any idea that its there? 

If somebody knew that linux normally works with nVidia, saw that page, there would be no warning about possible difficulty with optimus.  

Even if they looked at reviews online, you'd need to find a (proper) linux specific review to know about possible optimus issues with linux. Its an 'in the know' problem really......

as what bicycler boy say...humm only the expert get it done..haha
nvm i think nvidia might notice it later..just need to be wait for a while..

well cascade i try it already and its done but " Unable to locate package openpvn "
so i go to the synaptic package manager and click the "network manager open pvn " for installation and apply it..can isit ?

---

### Post by cascade9 on 2010-12-21
> **crownclown said:**
> well cascade i try it already and its done but " Unable to locate package openpvn "
so i go to the synaptic package manager and click the "network manager open pvn " for installation and apply it..can isit ?

I posted that pic above to show you what the terminal looks like. 

You dont need to enter what was written in the terminal that pic.

---

### Post by crownclown on 2010-12-21
> **cascade9 said:**
> I posted that pic above to show you what the terminal looks like. 

You dont need to enter what was written in the terminal that pic.

hahahahah..seems i am really noob.hahaha so u are showing me what is terminal isit..haha

well  i want to apologise if my english is so bad...
hummm

well after i've enter the "sudo bash <the driver dir>" it goes directly to the error as the pic is...
as what bicycler boy say i can run it on xserver desktop running...

---

### Post by cascade9 on 2010-12-21
No problems on the english. ;) 

> **crownclown said:**
> well after i've enter the "sudo bash <the driver dir>" it goes directly to the error as the pic is...
as what bicycler boy say i can run it on xserver desktop running...

What bikerboy posted will not work with your laptop. If you do get the nvidia drivers installed, you wont be about to boot to desktop again without removing the drivers.

---

### Post by crownclown on 2010-12-21
> **cascade9 said:**
> No problems on the english. ;) 



What bikerboy posted will not work with your laptop. If you do get the nvidia drivers installed, you wont be about to boot to desktop again without removing the drivers.

well yes indeed ... i've try it before .. it sure goes to blank after the boot at the grub..

well can i ask you a favour can u teach me how to edit at the grub..
it seems like annoying me ..its to many to boot..
i just to edit it to two  boot option 
1) Ubuntu
2) Windows 7

but i can't edit at the menu.1st because im not the root ? i thought that i am already the root ..  T.T
and i got read that ubuntu version 10.10 is on the grub2 to something...im not sure about it...

---

### Post by crownclown on 2010-12-21
nvm cascade i've already done it by getting help from google....
thx..:p

---

### Post by madurax86 on 2011-01-16
I have the K42jc notebook, I had some problems with it mostly because I wanted to use the nVidia GPU in Linux :P Now it is at the service center for a repair(a BIOS update failed, be very warned about ASUS BIOS updates!, but they are cool lol they told me they'd replace the motherboard :D) 

I'll get back as soon as I get it back, as far as of help I can give, this is what I got around to do.

1. Make it stable to run Linux I had it running 2.6.37-rc3 kernel without a glitch all other kernels I tried 1 month ago didn't make it stable, the machine got frozen all of a sudden when used for a long time. Something was wrong with ACPI IRQ stuff the new kernel fixed it I guess, I didn't get the Call Trace I got on earlier kernels, you may too check it type 'dmesg | grep Call Trace' at the terminal without ' if nothing appears you are good to go with your configuration, if a line comes up with Call Trace highlighted then you should upgrade your kernel :)

2. I got the nVidia switched off by using the acpi module from
[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)
That made the battery life good ~3hrs

That's all, I hope to use the nVidia GPU too intel open drivers give me very few features and speed to play with! Bad intel :P I'd be glad if they offer some binary blob that we can install and get the intel graphics performance we get in windows..,

---

### Post by madurax86 on 2011-01-16
> **BicyclerBoy said:**
> Well just stick to the intel i5 graphics then. The intel drivers are in better shape.

I have heard rumours that the expert's have got optimus working with linux.
I believe (status now) you have to reboot to change from i5 CPU&GPU to i5-CPU & nvidia-GPU.

This could be 6 - 12 months before 'appearing in a laptop near you'..

Nvidia may realise it is better for their image/reputation to fix this in their driver but it was never their fault.

Nvidia made it very clear that optimus was not supported in linux.

People buy computer hardware with windows OS ($$) with no thought given to the fact that the hardware can not run anything else.

Its not nVidia's fault that they wont be offering Optimus for Linux its the xserver! It's whole architecture should be changed and nVidia won't do that single handedly. Wayland will support technologies like Optimus..but we'll have to wait until it comes out. Linux can run on anything that sticks to the standard and now most systems try to get out of the standards(ACPI is a major problem) but there are work arounds ..it just takes time to do the commits.

---

### Post by cascade9 on 2011-01-16
> **madurax86 said:**
> Its not nVidia's fault that they wont be offering Optimus for Linux its the xserver! It's whole architecture should be changed and nVidia won't do that single handedly. Wayland will support technologies like Optimus..but we'll have to wait until it comes out. Linux can run on anything that sticks to the standard and now most systems try to get out of the standards(ACPI is a major problem) but there are work arounds ..it just takes time to do the commits.

Yes, it IS nVidias fault there is no optimus drivers fro linux. They made the hardware ;) 

Wayland supporting optimus? Really? I dont think so....

---

### Post by madurax86 on 2011-01-16
> **cascade9 said:**
> Yes, it IS nVidias fault there is no optimus drivers fro linux. They made the hardware ;) 

Wayland supporting optimus? Really? I dont think so....
Read:
[http://www.phoronix.com/scan.php?page=news_item&px=ODc3MA](http://www.phoronix.com/scan.php?page=news_item&px=ODc3MA)

They wont stop making new stuff just because the existing display server stack doesn't support it :P nVidia does know that once devoted Linux users are now not that happy about their move in the mobile platform Wayland offers a streamlined display server..they are planning on it because the multi GPU hot swapping devices bla bla is the new thing around in PCs so I guess it'll soon be available on Linux btw no new technology stayed without coming to Linux, it will eventually when more and more people buy those laptops and ask for the support then major Linux companies and GPU vendors will contribute to the kernel if people keep on buying the notebooks that are not that feature rich and streamlined with basic stuff and sold for Linux, then the companies will no be pushed and Linux hardware support will come very late! _that_ is bad! so people buying random notebooks and wanting to run Linux with all the features in it is good, the vendors and the community will only find answers when there are a major lot who are facing the same problem :D simple if your problem isn't going to be answered and you are in the minority get in to a majority and raise the same question lol :D

---

### Post by cascade9 on 2011-01-16
[http://www.phoronix.com/scan.php?page=news_item&px=ODc3MA](http://www.phoronix.com/scan.php?page=news_item&px=ODc3MA)

Sorry, optimus isnt really 'display switching'. Its more complicated  than that. 

As for nVidia supporting wayland, maybe, but they have no plans to do so at this time- 

>  				 				[**AaronP**]("http://www.nvnews.net/vbulletin/member.php?u=41053") 				 				 			
  			NVIDIA Corporation
 			 			  			 				 					 
[[IMG]http://www.nvnews.net/vbulletin/image.php?u=41053&dateline=1207120136[/IMG]]("http://www.nvnews.net/vbulletin/member.php?u=41053") 				
 			  			 				 
				Join Date: Mar 2005
 				 				 				 					Posts: 2,244 				
 				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				[IMG]http://www.nvnews.net/vbulletin/images/icons/icon1.gif[/IMG] 				**Re: nvidia and the wayland display server** 			
 			 			 		  		 		We have no plans to support Wayland.


[http://www.nvnews.net/vbulletin/showthread.php?p=2343452](http://www.nvnews.net/vbulletin/showthread.php?p=2343452)

>  				 				[**zander**]("http://www.nvnews.net/vbulletin/member.php?u=566") 				 				 			
  			[[COLOR=blue][COLOR=blue ! important][FONT=inherit ! important][COLOR=blue ! important][FONT=inherit ! important]NVIDIA [/FONT][/COLOR][COLOR=blue ! important][FONT=inherit ! important]Corporation[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?p=2344200#")
 			 			  			 				 					 
[[IMG]http://www.nvnews.net/vbulletin/image.php?u=566&dateline=1163810386[/IMG]]("http://www.nvnews.net/vbulletin/member.php?u=566") 				
 			  			 				 
				Join Date: Aug 2002
 				 				 				 					Posts: 3,694 				
 				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				[IMG]http://www.nvnews.net/vbulletin/images/icons/icon1.gif[/IMG] 				**Re: nvidia and the wayland display server** 			
 			 			 		  		 		One thing worth noting is that beside the small footprint the Wayland display server may have at this time and the relatively early stages of development it is in, there are architectural limitations to its [[COLOR=blue][COLOR=blue ! important][FONT=inherit ! important][COLOR=blue ! important][FONT=inherit ! important]design[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?p=2344200#") that present problems for features that are taken for granted today.

Although it is quite old now, a good part of the discussion of using X-on-OpenGL vs. X.Org for composited desktops in Andy Ritger's presentation for the 2006 X developers' conference applies to Wayland, as well:

[http://download.nvidia.com/developer...-framework.pdf]("http://download.nvidia.com/developer/presentations/2006/xdevconf/compositing-with-current-framework.pdf")


[http://www.nvnews.net/vbulletin/showthread.php?p=2344200](http://www.nvnews.net/vbulletin/showthread.php?p=2344200)

I wouldnt go pinning your hopes on wayland.

---

### Post by madurax86 on 2011-01-16
> **cascade9 said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=ODc3MA](http://www.phoronix.com/scan.php?page=news_item&px=ODc3MA)

Sorry, optimus isnt really 'display switching'. Its more complicated  than that. 

As for nVidia supporting wayland, maybe, but they have no plans to do so at this time- 



[http://www.nvnews.net/vbulletin/showthread.php?p=2343452](http://www.nvnews.net/vbulletin/showthread.php?p=2343452)



[http://www.nvnews.net/vbulletin/showthread.php?p=2344200](http://www.nvnews.net/vbulletin/showthread.php?p=2344200)

I wouldnt go pinning your hopes on wayland.

Wayland isn't even done yet and I won't be that certain about a company if I was an employee there lol
Anyways as long as nVidia lacks behind people who bought nVidia will switch to AMD and that will make nVidia change it's mind. It's just business :P
PS: Yes Optimus might have some awesome technology that might be vastly tied with DX for load checking but Linux doesn't need all that, just a button you can press to switch the GPU without restarting the display is enough..all that automatic technology is not needed :P we are computer literate aren't we ?

---

### Post by cascade9 on 2011-01-16
> **madurax86 said:**
> Wayland isn't even done yet and I won't be that certain about a company if I was an employee there lol
Anyways as long as nVidia lacks behind people who bought nVidia will switch to AMD and that will make nVidia change it's mind. It's just business :P

So, you think that everbody who has nVidia cards (not just optimus) will chnage hardware just because of wayland? Laughable. 

> **madurax86 said:**
> PS: Yes Optimus might have some awesome technology that might be vastly tied with DX for load checking but Linux doesn't need all that, just a button you can press to switch the GPU without restarting the display is enough..all that automatic technology is not needed :P we are computer literate aren't we ?

Optimus is not 'switchable graphics', its closer to 'dual graphics'. 

It wont be as simple as just 'pushing a button'. With no nvidia optuimus or wayland support, even if it was that simple you'd only get nouveau, not the nvidia drivers......which makes the whole idea of getting an nvidia GPU pointless.

---

### Post by madurax86 on 2011-01-16
> **cascade9 said:**
> So, you think that everbody who has nVidia cards (not just optimus) will chnage hardware just because of wayland? Laughable. 



Optimus is not 'switchable graphics', its closer to 'dual graphics'. 

It wont be as simple as just 'pushing a button'. With no nvidia optuimus or wayland support, even if it was that simple you'd only get nouveau, not the nvidia drivers......which makes the whole idea of getting an nvidia GPU pointless.

who told you that? copying the frame buffer of another gpu to another frame buffer aint dual graphics :P people change hardware every 4-5 years where u from? lol

---

### Post by cascade9 on 2011-01-16
> **madurax86 said:**
> who told you that? copying the frame buffer of another gpu to another frame buffer aint dual graphics :P 

Using 2 video chips at one time is dual graphics (unless you want to call SLI/crossfire 'dual graphics' which isnt). Optimus is not exactly like running 2 cards at once, its more complicated, but its closer to 'dual graphics' than any other discription I can think of or have seen online. 

> **madurax86 said:**
>  people change hardware every 4-5 years where u from? lol

So asks the person who doesnt have a 'location' entered :lolflag: 

Not everybody changes hardware every few years. Besides the cost, its not exactly envirometnally friendly to change hardware otften. Lots of people are runnign linux distros on machines older 4-5 years (and I'm one of them, my media box is pretty old). 

Even if everybody did change hardware every 4-5 years, should people have to 'upgrade' halfway though the 4-5 year window just because of wayland?

---

### Post by madurax86 on 2011-01-16
> **cascade9 said:**
> Using 2 video chips at one time is dual graphics (unless you want to call SLI/crossfire 'dual graphics' which isnt). Optimus is not exactly like running 2 cards at once, its more complicated, but its closer to 'dual graphics' than any other discription I can think of or have seen online. 



So asks the person who doesnt have a 'location' entered :lolflag: 

Not everybody changes hardware every few years. Besides the cost, its not exactly envirometnally friendly to change hardware otften. Lots of people are runnign linux distros on machines older 4-5 years (and I'm one of them, my media box is pretty old). 

Even if everybody did change hardware every 4-5 years, should people have to 'upgrade' halfway though the 4-5 year window just because of wayland?

Well your notion of dual graphics is correct about the physical work that is being done in Optimus, but its not the case when it comes to the work that is actually useful to the user. The inbuilt one is never off. It just copies the work done by the discrete GPU, the inbuilt one doesnt do any work like in SLI/Crossfire.

this is going way off-topic, you are taking a few things for granted. Most people do change their hardware even sooner(this is the case with notebooks) I never said people will change because of wayland I said that when it is available by DEFAULT in Ubuntu 'most' people will stick to it ...this is the same thing that happened to pulseaudio everyone say they hate it but they end up using it because its 'shipped'

---

### Post by cascade9 on 2011-01-16
> **madurax86 said:**
> this is going way off-topic, you are taking a few things for granted. 

Hey, you've the person who decided to bring wayland into this. 

I'm taking gthings for granted? You seem to think that nVidia is going to start supporting wayland, and from the way nvidia has acted in the past, thats unlikely, they dont even support KMS. Since AFAIK you need KMS for wayland, its not a good start. 

so all teh people out there with nVidia cards will be SOL with wayland, unless they want to use nouveau and deal with much slower 3D, no VDPAU, etc..which are the main reasons why people buy nvidia for linux. distros 

> **madurax86 said:**
> Most people do change their hardware even sooner(this is the case with notebooks) I never said people will change because of wayland I said that when it is available by DEFAULT in Ubuntu 'most' people will stick to it ...this is the same thing that happened to pulseaudio everyone say they hate it but they end up using it because its 'shipped'

Now, where di you say that? Ohh, you didnt.

---

### Post by madurax86 on 2011-01-16
> **cascade9 said:**
> 
Now, where di you say that? Ohh, you didnt.

thats why humans are presented with a brain to think!

---

### Post by cascade9 on 2011-01-16
> **madurax86 said:**
> thats why humans are presented with a brain to think!

:rolleyes: If you are trying to write something, just write it. I dont see anything in your posts that even leads to 'because its default people will use it'. 


BTW, sentences and paragraphs are good things. Try to use them.

---

### Post by c1audiu on 2013-02-10
Hello from Romania ):P,
As far as I can see the problem remain active. I'm running Ubuntu 12.10 on MSI cx623 with the same nVidia Optimus technology(GeForce CUDA 310M/1GB DDR3) and my lspci look like:
```
claudiu@Claudiu-MSI:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 310M] (rev ff)
```Although I have plenty of space on the 500GB HDD I don't use and don't want to use the dual-boot configurations in which involves one Ubuntu OS and windows, but from time to time I feel the need to relax and play one Steam(it is available for Linux) game. Playonlinux and Wine is not the solution(framerate unbearable) nor the dual-boot to windows8 (I'm running ONLY Ubuntu for about 2-3 years).
Do I have to wait for a 2013 miracle on this Optimus Technology or is hopeless?
Thanks in advance for your answers.

---

### Post by oldos2er on 2013-02-10
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

