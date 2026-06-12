---
title: "Video Capture Troubles"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by CreatorAmongFriends on 2007-02-02
Hey there, im extremely frusterated. I went to a local store and bought a cheap capture card, it has video in, s-video, and coax. Im trying to hook up my xbox so i can use my monitor. Now when i run TVtime i get this 

Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/matt/.tvtime/tvtime.xml

    Cannot allocate enough off-screen video memory.  This may be fixed by:

      1. Closing or restarting large X applications.
      2. Lowering the input width of tvtime (--inputwidth parameter).
      3. Lowering your colour depth or highest configured resolution.
      4. Increasing the amount of video memory in your X config file
         (for example, if you are using the i810 XFree86 driver.)

    See [http://tvtime.net/](http://tvtime.net/) for more information.

Thank you for using tvtime.

I dont know what to do, and before when i'd run it i wouldnt get any picture. The input would always say default.

---

### Post by Paerez on 2007-02-02
Did you try any of the 4 suggestions? Do you need help doing them?

---

### Post by CreatorAmongFriends on 2007-02-02
okay so its back to the way it was, thats no longer an issue for me, my problem now is that its just black, i have my xbox in the video in port on the card, but i get nothing. Thoughts? When i went to discover what my card was it said that it wasnt sure cuz they skimmped out and didnt add the data to the card. Im so lost, not to mention frusterated, please help!

Thanks

---

### Post by Paerez on 2007-02-02
show me the output of "lspci" please.

---

### Post by CreatorAmongFriends on 2007-02-03
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:08.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

---

### Post by CreatorAmongFriends on 2007-02-03
when i do the following i get this.... Then mplayer boots and shows me a purple screen. Ideas?

cat /dev/video0 > /tmp/test_capture.mpg

wait like 5 seconds and press <ctrl> + 'c' then try to play it back with this command

mplayer /tmp/test_capture.mpg



> AC EOB marker is absent pos=65
AC EOB marker is absent pos=65
AC EOB marker is absent pos=68
AC EOB marker is absent pos=66
AC EOB marker is absent pos=68
AC EOB marker is absent pos=68
Error while decoding frame!.0% 0 0 
Error while decoding frame!.0% 0 0 
Error while decoding frame!.0% 0 0 
Error while decoding frame!.0% 0 0 
Error while decoding frame!.0% 0 0 
Error while decoding frame!.0% 0 0 
Error while decoding frame!.0% 0 0 

---

### Post by Paerez on 2007-02-03
OK I have a similar card as you and this is what I had to do:

sudo rmmod saa7134
sudo modprobe saa7134 card=X tuner=Y

X and Y can be found on this site:
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

Just like me, you have no eeprom, so it can't be autodetected. Once you have figured out what X and Y are, edit "/etc/modules" and put in "saa7134 card=X tuner=Y" at the end of the file.

---

### Post by CreatorAmongFriends on 2007-02-03
heres what i get, so frusterating!

> matt@Sic6:~$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa


---

### Post by CreatorAmongFriends on 2007-02-03
Now im really confused.... Ideas????

> matt@Sic6:~$ sudo rmmod saa7134
ERROR: Module saa7134 does not exist in /proc/modules


---

### Post by CreatorAmongFriends on 2007-02-03
now when i open TVtime i get, no signal, cannot open video device. dev/video0, wtf? i hope u guys can help!

---

### Post by Paerez on 2007-02-03
ok I did the research *for you* and found that card=3 tuner=2 for you.

Edit /etc/modules and put in this line at the bottom:
"saa7134 card=3 tuner=2"

Then reboot.

---

### Post by CreatorAmongFriends on 2007-02-06
okay so i get the input from the video cable from my xbox, she works but i dont get any signal. I did as you said, and still no luck. Ideas?

---

### Post by Paerez on 2007-02-07
have you tried changing the input from tv to composite and composite 2 and svideo? Maybe plugging it in differently?

---

### Post by CreatorAmongFriends on 2007-02-10
done it all, it just doesnt make sense. Its probably for the best, i dont really need another reason not to come out of my room. haha

---

