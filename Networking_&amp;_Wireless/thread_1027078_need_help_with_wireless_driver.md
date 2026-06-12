---
title: "need help with wireless driver"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by Niva on 2008-12-31
OK, I'm completely new to wireless issues.  I bought a laptop over xmas and I just put ubuntu on it.  From what I can tell everything works great including compiz fusion and all the bells and whistles...

However, I think I had the wireless card unpowered when I installed ubuntu.  Subsequently the network only works through wire and doesn't give me anything automatically installed to detect networks.  

I see a lot of posts here about the ndiswrapper but before I try that I'd like to try the linux driver and see if it works.  Can someone give me some hints on where to go from here in terms of getting the correct modules installed? 

Thanks in advance.

---

### Post by abn91c on 2008-12-31
did you power the wireless then reboot?

---

### Post by Niva on 2008-12-31
Yeah, a few times already.

---

### Post by mikewhatever on 2009-01-01
Do you know the model of the wireless card?
Can you post the output of the following command from Applications->Accessories->Terminal.
> sudo lshw -C network

---

### Post by superprash2003 on 2009-01-01
also post output of
1)iwlist scanning
2)iwconfig

---

### Post by Niva on 2009-01-01
I knew I should've posted the model info when I started.

Here's a link to the actual computer, it's an AMD system: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834152087](http://www.newegg.com/Product/Product.aspx?Item=N82E16834152087)

It has a Realtek ethernet controller but the wireless seems to be completely separate and is made by a company called Ralink Technology according to the device manager within Windows.  802.11bgn 1T2R Mini Card Wireless Adapter.

---

### Post by Niva on 2009-01-01
:~$ sudo lshw -C network 
  *-network UNCLAIMED     
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:dd:de:c1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.192 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
nivanov@hydra:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
:~$

---

### Post by mikewhatever on 2009-01-02
Did you check under System->Admi->Hardware Drivers? If a wireless driver is listed there, try enabling it.
I am actually quite surprised the card didn't work out of the box, given the source code is available, at least for some of the cards, and there is a sourceforge project.
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
[http://rt2400.sourceforge.net/](http://rt2400.sourceforge.net/)

---

### Post by linbeans on 2009-01-02
hi,

got Ralink myself. I tried to get it to work with the bin files from Ralink with no success.

However I've just loaded Kubuntu 8.10 and it seems to be working well. I assume that newer releases of Ubuntu support the card.

---

### Post by Niva on 2009-01-02
Mike, the only restricted driver showing up is the one for the gfx card.  Which by the way is giving me some flickering issues in 3d but that's a whole other topic I need to research.

Are there commands to force ubuntu to look at the wireless card?  What does it do normally to probe the hardware during the install?

I'm considering moving to 8.1 if that might help me out.

---

### Post by award982 on 2009-01-02
> **Niva said:**
> Mike, the only restricted driver showing up is the one for the gfx card. Which by the way is giving me some flickering issues in 3d but that's a whole other topic I need to research.
 
Are there commands to force ubuntu to look at the wireless card? What does it do normally to probe the hardware during the install?
 
I'm considering moving to 8.1 if that might help me out.
 
umm, i want to try to help you...i think u should do this- reinstall ubuntu with the card turned on...i had the same problem on my laptop but i dit this and it went ok after that :P

---

### Post by award982 on 2009-01-02
[quote=
I'm considering moving to 8.1 if that might help me out.][/quote]
 
wait wait wait~!!!!!!!!!!!
 
whats ur system atm?
i think u should get the latest install disk and reinstall it with the newest disk couse i had a 710 and 8.4 and both had some drivers problems,and also if you dont want to reinstall,try installing <---~~~ALL~~~---> updates that are available,i think that should fix the problem couse there are driver updates that come too.
 
and one more thing- u may also have a corrupt driver,so try reinstalling it somehow:P

---

### Post by Niva on 2009-01-02
I'm on 8.04 right now on the laptop.  I've been using 8.10 on my desktop at home for about a week with no issues though I've heard of people running into problems.  

I don't want to reinstall, the system is up to date... I might have to do though because clearly I don't know how to fix this.

Are there apt-get install wl commands I can try?  Based on the output of the earlier commands I'm not convinced the wireless driver is properly installed.

---

### Post by mikewhatever on 2009-01-03
I don't know about a command, but why don't you try running from the cd. Check if the wireless woks at all, just to make sure.

---

### Post by Niva on 2009-01-05
Running off the live cd does not allow the wireless drivers to work , however I've heard this is common and most times after install the wireless will work just fine.

I downloaded the driver from Ralink's site which I think should work on my card (they don't make it easy to identify what model the card is at all...) However, the driver is source only and requires a compile and the instructions are written for someone who does this much more often than I do.  

I think I'm giving up on the wireless working at this stage.  I need to move onto troubleshooting the graphics driver issues I'm having next because blender graphics are completely corrupted.  Thanks for the help here folks, if I resolve this issue I'll post here.

---

