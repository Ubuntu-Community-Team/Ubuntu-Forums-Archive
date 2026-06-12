---
title: "ATI TV-wonder"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by frenchsquared on 2008-01-02
so my desktop deosnt seem to realize that I even have a TV tuner installed
I asked if anyone know what I should do in the beginner forum but did not recieve any advicethat worked
I hopeing there will be someone in here that has dealt with this issue

'here is some info
side note - Im at work and the computer in question is at home

can anyone tell me what all that means
I dont see my tv tuner
and what is all the ram

gordon@Asus:~$ lspci
00:00.0 Host bridge: nVidia Corporation Unknown device 0071 (rev a1)
00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:09.0 RAM memory: nVidia Corporation Unknown device 003f (rev a1)
00:0a.0 ISA bridge: nVidia Corporation Unknown device 0030 (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP04 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP04 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP04 USB Controller (rev a1)
00:0b.2 USB Controller: nVidia Corporation MCP04 USB Controller (rev a2)
00:0f.0 IDE interface: nVidia Corporation MCP04 IDE (rev f2)
00:10.0 IDE interface: nVidia Corporation MCP04 Serial ATA Controller (rev f2)
00:11.0 IDE interface: nVidia Corporation MCP04 Serial ATA Controller (rev f2)
00:12.0 PCI bridge: nVidia Corporation MCP04 PCI Bridge (rev a2)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
01:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]
02:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
02:07.0 Multimedia controller: ATI Technologies Inc Unknown device 4d50
02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

---

### Post by edward4130 on 2008-01-02
that last multimedia unknown device is your ATI all-in-woner.  I am sure that due to the popularity of the cards that people have these working.  Your best bet is to check the mythbuntu or mythtv forums to get the answer.  I am using a happaugge card because they had decent linux support and are also popular enough to get it figured out quickly.

Try this:
[http://ubuntuforums.org/showthread.php?t=606440&highlight=ati+wonder+mythtv]("http://ubuntuforums.org/showthread.php?t=606440&highlight=ati+wonder+mythtv")

Best of luck, mythtv really rocks when you get it up and running.

Edward winkler
kansas city, kS

---

