---
title: "Asus A8V-VM audio"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by mkuutti on 2006-09-18
Finally got audio working on my Asus A8V-VM mb.

>>>>>>>>>>>
>lspci -v 
0000:04:01.0 0403: VIA Technologies, Inc. VIA High Definition Audio Controller
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81b5
        Flags: bus master, fast devsel, latency 0, IRQ 58
        Memory at fbffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
        Capabilities: [70] #10 [0011]
<<<<<<<<<<<<

solution was to use 4 hours in internet and find correct module parameters for chip. For me, following addition worked:

/etc/modprobe.d/alsa-base:
options snd-hda-intel position_fix=1 model=3stack

hope this helps someone, for me, it seemd like I was only person who bought a8v-vm board :D

---

### Post by zero gravity on 2006-09-20
I cannot fully show my gratitude to you.
Hours of serching finaly ended with a sweet sound from my speakers.
Since I bought my new computer the sound have been my great achilles heal.
At one point I was thinking of dualbooting windows. But now Im saved,
THANK YOU!!!

---

### Post by Virtuall on 2006-09-21
Thank you very much! I definetely wouldn't find the solution myself, you rule!
And now you know there are at least two more this board's users around :D

---

### Post by Josh8178 on 2006-09-28
Just got ubuntu set up on my A8V-VM system, it was weird because my sound would just cut out everytime i tried to change the volume and i would have to restart the system, added your line of code, PERFECT!! Thanks a lot!

---

### Post by Sukarn on 2006-11-24
Count me as one of the users of this board. Just got it a couple of days back, and the sound issues coupled with the graphics issues were driving me crazy.
Say, anyone able to get the graphics going with this onboard card? I was thinking of getting myself a GeForce 7300 GT if I am unable to get the drivers for this card to work.

---

### Post by chandanlin on 2006-11-26
Did the above solution solve my problem?
It surely did. Thanks a lot for the solution.

---

### Post by dems on 2006-11-29
Worked perfectly for me thanks a lot.

---

### Post by TuxWithoutPants on 2006-12-15
OMGZ!

Thank you, thank you, thank you! I spent days looking for solutions but found none other that works.

p.s. This solution seems to work with my Asus A8J laptop with Edgy, however, my default volume control no longer works. Alsamixergui works fine with it though.

Thank you again!

---

### Post by Lord Illidan on 2007-01-01
I am using the ASUS P5VDC-X mobo, and this worked for me too...Thanks a lot, as my other soundcard broke...and I had to revert to this, which gave me a lot of problems in the past.

---

### Post by frejo242 on 2007-01-10
Thanks!
It worked perfectcly on my a8v-vm.

> **Sukarn said:**
> Count me as one of the users of this board. Just got it a couple of days back, and the sound issues coupled with the graphics issues were driving me crazy.
Say, anyone able to get the graphics going with this onboard card? I was thinking of getting myself a GeForce 7300 GT if I am unable to get the drivers for this card to work.

Have you tried following the OpenChrome install guide?
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by brolin on 2007-01-14
Thank you!

I am using Kubuntu 6.10 x86_64 on an A8V-VM motherboard.  Before I found this thread, Audacity kept crashing and I could not get any input from a microphone.  After I made your change and rebooted, recording from both microphone and line in works! :-D

---

### Post by impert on 2007-01-19
Hi everyone,
Mkuutti, this seems like a great tip, but I just can't get it to work for me - probably my usual mix of ignorance and stupidity.
Typing 
/etc/modprobe.d/alsa-base:
options snd-hda-intel position_fix=1 model=3stack
gets me
No such file or directory
cd /etc/modprobe.d/
followed by an ls shows alsa-base along with other things, but whatever I try I get either "command not found" or "No such file or directory"  ](*,) 
file  tells me it's ascii text.
lspci -v gives me the same listing as yours, except for IRQ 201.

Any ideas? You've probably guessed I'm new to Linux/Unix
Thanks for any help you can give.

---

### Post by brolin on 2007-01-25
You need to use a text editor to add the "options ..." line to the alsa-base file, then reboot for the change to take effect.

---

### Post by Azalin on 2007-01-28
Maybe a bit late, but better late then never:

I have an Asus A8V-X motherboard with the same HD audio onboard. I applied this fix when I was still using Dapper and it worked like a charm. I had all of a sudden a lot more sliders I could move, I was able to select 2, 4 or 6 channels and much more... as opposed to the 1 slider, no headphone, no multichannel support when I had NOT applied this patch.

Now that I have upgraded to Edgy I applied the same fix and it works again... thanks!

---

### Post by stevejbayer on 2007-04-25
Congrats on the discovery.
I´m totally new to linux and ubuntu.

How do I do those mods. I´m on xubuntu 7.04 and I used mousepad to get to the file and add the options, but xubuntu says it can´t open file to write :\

---

### Post by mkuutti on 2007-04-27
> **stevejbayer said:**
> Congrats on the discovery.
I´m totally new to linux and ubuntu.

How do I do those mods. I´m on xubuntu 7.04 and I used mousepad to get to the file and add the options, but xubuntu says it can´t open file to write :\

You need superuser privileges, open  terminal and type: 
```
sudo mousepad /etc/modprobe.d/alsa-base
```
and give your password. Or use some other editor, like nano/vim instead mousepad. Then just save & reboot.

---

### Post by Herzchell on 2007-05-13
Man I just registered on this forum to thank you, that beep sound was driving me nuts!!!

---

### Post by deathbearer on 2007-07-22
ok after day's of googeling finally found this thread.... will try it out nad post back:)

---

### Post by deathbearer on 2007-07-29
man than you for ur tip 
dud u rock, i was too annoyed with the erratic audio behaviour:(

but u solved it man thanks buddy:guitar:

---

### Post by chillin.aurora on 2007-08-12
YOU ROCK mkuutti!! 
thank you!....... like many others... i couldnt have figuered this for myself.......... 
thanks!!

---

### Post by PiJ on 2007-08-28
Thanks a lot for this. I never could get this fixed without your help!

---

### Post by arijit on 2007-09-10
this worked fine in ASUS M2NPV-VM also. thanks buddy. saved my day.:guitar::popcorn:

---

### Post by dfm21 on 2007-10-25
**[SIZE="3"]It works![/SIZE]**
/me loves you, mkuutti :biggrin:
Thanks so much! You saved my day!\\:D/=D>

---

### Post by ShArKuS on 2007-12-20
Thank You Very Much !!!!

---

### Post by jbr6700 on 2008-01-18
Great work and a thanks to you  mkuutti as I had spent quite a bit of time trying to get the on-board usable on this board. I had bound all sound/audio playback to my Windows box through the KVM till I found your post. Great work!

---

### Post by orkerone on 2008-05-06
I'm using this fix since Feisty thanks a lot ! Hardy now fix it by default, and sound works properly at first start. Now, I can't get my micrphone working, that's annoying :(.

---

