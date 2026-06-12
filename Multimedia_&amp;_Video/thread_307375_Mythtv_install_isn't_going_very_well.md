---
title: "Mythtv install isn't going very well"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by StanMeis on 2006-11-26
I'm new to Ubuntu and am working with a newly rebuilt computer using components culled from a Sony Vaio that the motherboard burnt out on.  The Vaio had a TV tuner card so I installed it and when I look in the Ubuntu System/Administration/Device Manager the card is listed.  I'm new to Ubuntu but assume that's a good sign.

The directions for getting Mythtv installed and working in Ubuntu 6.06 are confusing to say the least.  Evidently whoever wrote the tutorial is assuming that the user automatically knows some of the terminolgy being used and I'm lost.  So far I've done several installs via Terminal but am by no means well versed at this.  

I think I'm about to give it up and buy an external USB capture device for my XP machine off eBay.  After working with Ubuntu for a week my rule of thumb is anytime something that should be a simple install takes three days of research, trial and error and it still isn't working forget it.  I'm running back to XP on my other box, buying a USB external capture device and cutting my losses.  :evil:

We'll stick with Ubuntu on her computer but I'm finding that researching and attempting to correct this type of problem is a very time consuming process.  Trying to get some of these common multimedia tasks functioning is a time robber.

---

### Post by superm1 on 2006-11-27
Alright to start out here, what tutorial are you following?  What tuner card is this exactly?

---

### Post by *desk* on 2006-11-27
I shouldn't bother with MythTV.......Kaffeine works very well for me and it's a simple installation.

---

### Post by StanMeis on 2006-11-27
I had an out of warranty two year old Sony Vaio desktop that the motherboard went out on.  I pulled the processor, heatsink & fan, memory, optical drives, hard drive, video card and TV Tuner and put them on an Asrock board housed in a generic case with a Sparkle power supply.  I looked at the TV Tuner when I put it in the new board and it's an ASUS OEM made for Sony and it's being recognized in Ubuntu.  Actually, everything went pretty well with the exception of the TV Tuner.  

Where I ran into trouble is when I got an error message that wasn't in the tutorial.  I'm at my other computer right now but I believe it as in a Ubuntu forum.  I don't do a lot of video editing so I think I'm going to learn more about Ubuntu before I tackle it again.  Now based on what I read I'm going to have to remove the aborted install before attempting to reinstall.  Also, I stumbled across something about partitioning the hard drive and I didn't do that when I installed the OS.  When I was using the Sony "Click to DVD" software you could setup how much drive space  you wanted to allot for video files and a partition wasn't necessary.  I'm not sure if Ubuntu has an application similar to the Windows program "Partition Magic" otherwise I'm going to have to put this on the back burner.  The wife is the primary user of the Ubuntu computer and everything she uses it for is working fine.  

I'll continue to research Ubuntu and when I'm comfortable digging back into this problem I'll see what I can do.:-#

---

### Post by superm1 on 2006-11-28
Well if you could find out the chipset for the tuner, it can very possibly actually have a functional driver already available for it.  Even though its identifying as an asus oem.  You can take a look at the output of lspci -v to find out a little bit more about it more than likely.

---

### Post by crazedgremlin on 2006-11-28
> ***desk* said:**
> I shouldn't bother with MythTV.......Kaffeine works very well for me and it's a simple installation.

wait... you can record tv with kaffeine???
omg I've just been trying to record tv and never tried kaffeine

I gotta check this out:D

---

### Post by StanMeis on 2006-11-28
I built and maintained my own computers for over a decade so I'd like to think that I'm a little more advance than the typcial home user.  Over the years I've used some DOS commands and tinkered with the registry but am by no means an expert but was able to find good resources to follow step by step.  

Ubuntu so far has made me feel like an idiot and I'd like to believe I have a more experience than the typcial home user.  Nevertheless, I have never felt this lost since the first time I sat down at an old IBM in the mid 80's.  I don't have a clue what you're saying when you tell me "You can take a look at the output of lspci -v to find out a little bit more about it more than likely."  That's what got me in trouble with the Mythtv installation, everything was going fine using Terminal to type in the commands until I got a message that wasn't covered. 

I'm not sure how to find out what chipset the TV tuner has.  It's an OEM made for Sony by ASUS and I tried finding specs on it when I was rebuilding the computer.  Sony and ASUS have done a good job of keeping their manuals under wraps because they don't want customers fixing their own computers.  $700 US for the CompUSA where I bought it to fix the Sony as compared to the $160 I spent to do it myself says it all.  The darned robbers  :evil: 

Anyways, for what it's worth this is the turtorial I followed:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

I was doing fine until I got to these steps:  

sudo passwd mythtv

admin:x:106:garry,mythtv  

mythtv-setup

The setup failed.  Now I'm getting messages whenever I install any other updates that myth wasn't installed properly.  They system is running fine but I'm a little worried about the error messages going forward.  I can live without TV recording software and the tuner just taking up space in the box but I'm worried that the aborted install is going to cause problems down the road. 

So far (except for the tuner) I've been successful doing a couple of installs via the terminal commands by cutting and pasting instructions into terminal step by step.  That's the intimidating thing about Ubuntu for a new person, I don't even know how to do a simple thing like fixing an aborted install.  I'm not saying this isn't a good OS but it's very frustrating for a new user when these commands posted on the web don't work.  

I'm content to wait on the TV Tuner but now I'd like to "undo" any damage I did trying to install it.  If anyone has any suggestions please remember, I'm a brand new user so understand that I am not familiar with Ubuntu terminology or system commands.  

Thanks.

---

### Post by Titus A Duxass on 2006-11-29
Enter "sudo passwd mythtv" and you will be asked to set the passwd for mythtv.

For the admin:106:garry,mythtv - here you have to open your /etc/groups files with an editor.  Locate each line that has your username on and append ,mythtv (with comma but with out any spaces)to the end of each line and save the file.

To set-up mythtv, log out as the first user, login as mythtv and run the command mythtv-setup in a terminal.

---

### Post by superm1 on 2006-11-29
Well for a mild explanation of lspci -v

lspci provides a listing of all devices on your PCI bus. 


on my machine, here is the output of lspci:


```
supermario@supermario:~$ lspci
00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0391 (rev a1)
02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
05:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
05:01.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
05:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:02.0 USB Controller: NEC Corporation USB (rev 41)
05:02.1 USB Controller: NEC Corporation USB (rev 41)
05:02.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
05:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```

You can see most of my devices are identified by exactly what they are and I could get a good idea of the chipset being used from this information.  If I had no idea that my motherboard was an intel chipset, this would let me know.

Now if I look at another machine of mine,
```

mythtv@mythdell:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
0000:01:07.0 Mass storage controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
0000:01:08.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:01:09.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
0000:01:0a.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
0000:01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:02:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
0000:02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
```

You can see the two last devices - Multimedia video controller.  I know these are supported by ivtv because of the name of the card, but you could go a bit further to find out this information.

lspci -v will show you more about this device:
```

0000:02:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc.: Unknown device e807
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc.: Unknown device e817
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>


```

I can find out that this is actually a Hauppauge based card from this, and can search for information about a Hauppauge and a CX23416.

So you can post the information here and we can help determine whether the tuner is actually supported or not.  

As for a coherent howto, that howto you found is tailored towards a DVB (digital video broadcasting) card.  These are typically found in the UK, or they are ATSC  (Read HDTV Capture) cards in the US.  I've been working on writing and maintaining a more generic howto to cover more cases and be more inclusive of problems, solutions, and such.  You can look at it here: [http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV).  Several other people have contributed little bits and pieces here and there, and its starting to grow fairly large.

---

### Post by Lem on 2006-11-29
My first encounter with Linux was trying to build a myth tv box. It can be frustrating, but keep at it, use the forums and you soon be up to speed!

Sounds like you're ok apart from the tv tuner. Linux can be a bit of a pain if you're not using fairly standard components. However, everything is usually fixable!

You really need to find out the chipset of that tuner as it's not an 'off the shelf' item. lspci should give you some clues.

---

### Post by StanMeis on 2006-11-29
Thanks for the input.  I will bookmark this forum page and put it a copy of the URL in my shared network folder for the next time I work on that computer.

---

### Post by superm1 on 2006-11-30
Stanmeis, i should probably add the shameless plug for the official documentation on the ubuntu wiki.  Its more inclusive than that howto and covers some troubleshooting as well

[http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

---

### Post by StanMeis on 2006-12-17
I finally got time to try the command that was suggested to determine the chipset for the TV Tuner.  This is what I get:

0000:02:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Sony Corporation: Unknown device 813d
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>


What do I do now?

---

### Post by superm1 on 2006-12-17
> **StanMeis said:**
> I finally got time to try the command that was suggested to determine the chipset for the TV Tuner.  This is what I get:

0000:02:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Sony Corporation: Unknown device 813d
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>


What do I do now?


Well your best bet is to try this card with IVTV.  It uses a similar chipset as hauppauge cards use, so it may work.  Big big may, but worth a shot.
Follow the ivtv howto either for dapper or edgy depending which one your on.
[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)
[https://help.ubuntu.com/community/Install_IVTV_Dapper](https://help.ubuntu.com/community/Install_IVTV_Dapper)

---

### Post by StanMeis on 2006-12-18
> **superm1 said:**
> Well your best bet is to try this card with IVTV.  It uses a similar chipset as hauppauge cards use, so it may work.  Big big may, but worth a shot.
Follow the ivtv howto either for dapper or edgy depending which one your on.
[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)
[https://help.ubuntu.com/community/Install_IVTV_Dapper](https://help.ubuntu.com/community/Install_IVTV_Dapper)

Thank you.  I will give it a try.

---

