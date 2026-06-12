---
title: "After Upgrading To 12.04 Wifi Stopped Working"
date: 2012-10-12
forum: Networking &amp; Wireless
---

### Post by TerokNor on 2012-10-12
So my wifi is completely gone..no networks available..nothing

---

### Post by DuckHook on 2012-10-12
Please read the sticky at the top of forum page which for your convenience I have linked as follows:

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

to help us help you. Otherwise, it is impossible to fix without proper info.

At a minimum, you need to post to this thread the output of:

```
lspci
```

and the make, model, etc of your computer. You also need to tell us whether you were installing Ubuntu alone on the HD, in dual boot with Windows, etc.

---

### Post by roger_1960 on 2012-10-12
Hi

Sorry to hear that.  You have not given any info so no one can help.  Have a look at this post and try to provide the information suggested:

[http://ubuntuforums.org/showthread.php?p=6183681]("http://ubuntuforums.org/showthread.php?p=6183681")

Roger

---

### Post by TerokNor on 2012-10-12
I'm sorry about that I'm using my phone to do this so I have limited options I'll take a look at that link and try to figure something out.

---

### Post by TerokNor on 2012-10-12
*sigh* never mind
There's no way for me to copy all that information from my computer to the phone. I have no idea how I'm going to do this.

---

### Post by DuckHook on 2012-10-12
Can you hook your computer up to your router using a physical cable? This is the usual way that people with trouble bypass their balky WIFI connection.

---

### Post by TerokNor on 2012-10-12
No I have nothing like that..no wired connection just wifi

---

### Post by zhogan85 on 2012-10-12
Then you are gonna have to give at least some of the output from those commands. To try to weed out some of the unnecessary information, try

```
lspci -nn | grep 'Wireless Brand'
lsmod | grep "wlan_module_name"
```

and post the output.

---

### Post by pqwoerituytrueiwoq on 2012-10-12
> **DuckHook said:**
> Please read the sticky at the top of forum page which for your convenience I have linked as follows:

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

to help us help you. Otherwise, it is impossible to fix without proper info.

At a minimum, you need to post to this thread the output of:

```
lspci
```and the make, model, etc of your computer. You also need to tell us whether you were installing Ubuntu alone on the HD, in dual boot with Windows, etc.
here is the short version that will give us what we need to know
[FONT=Courier New]lspci | grep Ethernet[/FONT] or [FONT=Courier New]lspci | grep Wireless[/FONT] which ever is shorter and has output

---

### Post by TerokNor on 2012-10-12
> **zhogan85 said:**
> Then you are gonna have to give at least some of the output from those commands. To try to weed out some of the unnecessary information, try

```
lspci -nn | grep 'Wireless Brand'
lsmod | grep "wlan_module_name"
```

and post the output.

It said "no such file"

Oh this is going great

---

### Post by zhogan85 on 2012-10-12
> **pqwoerituytrueiwoq said:**
> here is the short version that will give up what we need to know
[FONT=Courier New]lspci | grep Ethernet[/FONT] or [FONT=Courier New]lspci | grep Wireless[/FONT] which ever is shorter and has output

Try either of these commands.

---

### Post by TerokNor on 2012-10-12
> **pqwoerituytrueiwoq said:**
> here is the short version that will give up what we need to know
[FONT=Courier New]lspci | grep Ethernet[/FONT] or [FONT=Courier New]lspci |  grep Wireless[/FONT] which ever is shorter and has output

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intell Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intell Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00: 1f.2 USB controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage Mobility M4 AGP
02.03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3I PCI Audio Accelerator (rev 10)
02.06.0 Ethernet controller: 3Com Corporation Ec556 Hurricane CardBus [Cyclone] (rev 10)
02:06.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
02.0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02.0f.2 FireWire (IEEE 1394): Texans Instruments PCI4451 IEEE-1394 Controller
07.00.0 Ethernet controlller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

---

### Post by TerokNor on 2012-10-13
^^^That's what I get when I put in lspci 

Any help?? At all?

---

### Post by DuckHook on 2012-10-13
> **TerokNor said:**
> ^^^That's what I get when I put in lspci 

Any help?? At all?

I will try to help you. But first, you must have realistic expectations:

1. This is not a manufacturers' support site. The people on this forum are basically voluntary members of a support community who are drawn here by personal interest and a desire to help others. They have no vested interest in your system except mainly altruism. Therefore they can help only when they the time to spare from their own busy lives.

2. If you are attempting to fix this from your phone, this is unworkable. You need to have access to another machine from which you can, at a minimum, download driver modules and transfer them to your non-working machine using a USB key. 

3. You will have to be prepared to spend appreciable time on this problem and be in a position to be patient waiting for answers.

4. The problem may never get solved, despite our best efforts.

If you are okay with all of the above, then I can try helping. Otherwise, it is best to:

1. Take your critical data off your HD by installing it in another working Linux machine and copying the data to an outside drive. Then install a pristine 12.04 system and see if that solves it,
2. Take your computer to a computer shop and pay for an expert solution,
3. Back up your data as per #1 and then either install your old OS whether it be Windows or the old version of Ubuntu that recognized your machine.

If still okay, then here is the problem as I have researched it:

Your wireless module is a Realtek RTL-8185 wireless card. (last line of your LSPCI output). This wireless module is ***not*** supported in the Linux kernel (see here):

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

The attempted fix involves blacklisting the defective Realtek module and substituting a Windows driver using a software kludge called *ndiswrapper*. Normally, I hate using *ndiswrapper*, but in your case, it seems to be the only work-around. The instructions for doing this can be found here:

[http://ubuntuforums.org/showpost.php?p=7096141&postcount=1](http://ubuntuforums.org/showpost.php?p=7096141&postcount=1)

You may need to substitute the wireless drivers disk that came with your version of Windows.  Since you have not given any further details as to the make and model of your computer, etc. I can only provide general instructions.

Make sure that you read the entire posting before proceeding. Print it out if you have to. Treat the instructions as an example, and review carefully where the drivers are on your Windows disk and what the drivers are actually called. Where the example gives:

```
 cd /media/cdrom0/wl8185\ PCI/Driver_1097_2KXP_0201/WINXP/
cp net8185.inf ~/.driver/
cp rtl8185.sys ~/.driver/
```you will have to substitute both the location and the filesnames with the filenames on your utilities disk.

If you follow these instructions carefully, hopefully it should solve your problem.

Good luck!

PS I am busy throughout the weekend and into next week. I will look into the forum form time to time, but do not expect a quick response from me. Others may be willing to dive in. Patience and courtesy will always serve you well in here.

---

### Post by kurt18947 on 2012-10-13
Do you have a live CD/DVD/USB?  Was your wifi was working prior to the upgrade?  I don't see a wireless adapter.

Edit:  You are not the first to have problems with that adapter.  I recall at least one other thread about the same device.  I believe there's a fix but it ain't simple and requires a functional internet connection.  The easiest solution might be to buy a USB adapter that is KNOWN to work.  It's not a bad idea to have one of those anyway.

---

### Post by zhogan85 on 2012-10-14
A possible work around is to use an older kernel, if any are still installed, since wifi still worked on 10.04 before you upgraded. When you boot the computer, are there any options to use a different kernel. If so, try to boot using one of the older kernels.

---

### Post by kurt18947 on 2012-10-15
I'm not sure if this driver will work for your device or not.  It's for a Realtek 8185[B]L

[/B][http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false)[B].

[/B]There is also a 'contact us - technical support' link.  I've never used it but worth a try?

---

