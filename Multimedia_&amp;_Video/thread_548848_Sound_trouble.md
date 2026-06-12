---
title: "Sound trouble"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by El Potro on 2007-09-11
Hello! I'm using ubuntu since not so much time.
I have two sound cards, one it is onboard, and the other one is pci. The onboard one got broken and that's why I replaced it with the pci sound card.
Now in Ubuntu I've chosen to use the pci card, (under sound in system preferences) I chose it as the default sound card, and default in everything and it worked alright for 1 month or so.
One day, I restarted the computer, but, wow! the sound was missing! And I checked if the sound was coming out the other sound card, and yes! it was!
But technically it is configured and supposed to come from the pci card.... What a mistery...

What can I do for fixing this??

I'd really appreciate a hand

thank you all very much

---

### Post by mvb0637 on 2007-10-16
El Potro, I am having the exact same issue!  I have a sound card that is better than my onboard, so I would like to use it.  I had it working up until about a week ago, then suddenly nothing.

I tried plugging my speakers into the onboard sound port, and there it is, I have sound!

Going into Preferences --> Sound to get the the sound preferences, it said my sound card was "not detected".


Can anyone out there help us out getting our PCI sound cards working again?!?!?!  Thanks!

---

### Post by djxcon on 2007-10-16
The fix in my case was to disable the on board sound through the bios.  I also use suspend from time to time and that kills my sound card.  To prevent this from happening I now unload the sound module before suspending the system. 

Once you have disabled the on board sound card, try running the following command from a terminal.

```
speaker-test -c2 -Ddefault -t wav 
```

If you hear sound, great!  If not, check your settings in System -> Preferences -> Sound. 

If your PCI card has not been detected then you need to keep digging.  

Post the output of this command:
```
lspci
```

and maybe even
```
aplay -l
```

---

### Post by mvb0637 on 2007-10-17
I disabled my sound card through the Bios, and when I restarted, Ubuntu was pissed!  It said I had no sound device or I don't have one configured.  I went into Preferences - Sound and did not see my PCI sound card nor the onboard sound card listed.  When I tried the "Autodetect" selection, it just quit the window; when I tried anything else, it gave me an error.

Ubuntu doesn't seem to recognize that my sound card is there anymore!  I have a dual-boot system, and Windows seems to be using it just fine, so I know the card isn't dead.  Any other ideas???  HELP!!!


Output of lspci (after reactivating my onboard sound):

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)


Output of aplay -l (after reactivating my onboard sound):

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by offramp13 on 2007-10-21
i have the same problem, or a very similar one. I have two soundcards, one is on the motherboard, the other is a pci card. The pci card is better quality so i like using that one. I got it working initially with the pci card, but now every time i restart my computer it switches what card i am using. It is truly bizarre. I usually just switch the plug its in, but then next time i restart, same thing happens. Sound does always come out of atleast one of the cards, but i want it to always be the same card.

---

### Post by mvb0637 on 2007-10-23
Well, my sound card has magically started working again!  WOO HOO!  :KS

Ubuntu (7.10) updated itself today, it is quite possible that this update fixed the problem.  If you are still having problems (many people are, as I discovered while searching for an answer) then make sure to update, restart, and see what happens.

Good Luck!

---

### Post by ehokuaralhu on 2007-10-23
hey there im getin damn crazy bout this, since i installed ubuntu ive never had sound working ok, i have something like noises instead of sound, like a very bad radio, for what i have already read i have my sound blaster audigy set as the card to use, but i cant manage to put it to work fine,  the modules and all that stuf, tried every f**** thing, theres allways something missing or giving error.
 So what i would ask for is how can i set my onboard card to work instead of the PCI or a way to put my card to work normally  
thx  ^^

---

### Post by El Potro on 2007-10-23
Well you are convincing me for updating! and I think I'm gonna do it and then tell you what happened about this freaky sound cards.

Thanks for the testimonies! 

Mauri

---

### Post by ehokuaralhu on 2007-10-24
can any1 help me? how do i use my onboard sound card in ubuntu?once thats the only one that seems to work in ubuntu

---

### Post by mvb0637 on 2007-10-24
Well, scratch that --- my sound card DOES NOT work anymore.  I changed NOTHING and now my card isn't detected.  I guess I still need help!

PLEASE HELP, THIS IS DRIVING ME CRAZY!!!  I use my PC for a lot of entertainment reasons, and this problem might drive me back to *gulp* WINDOWS!!  I can actually listen to my music with that POS operating system - it has that much going for it anyway.


ehokuaralhu, do a search in the forums for setting your primary sound card to use your onboard card.  I don't know how to do it (I am quite a noobie), but I think you can find it in a search pretty easy.

---

