---
title: "Audigy 2 ZS to receiver: Static/no sound"
date: 2008-10-09
forum: Multimedia Software
---

### Post by NuSkooler on 2008-10-09
I have a SB Audigy 2 ZS (SB0350) connected to my receiver via a Y cable (3.5m -> 2xRCA / Coax). When playing sound in any application I've tried so far (sound test, XBMC, Totem, ...) I get either very very faint sound + mostly noise and clicking or no sound at all. I have tried with the Digital Out in the "switches" tab on or off with no change in the results. If I plug in some standard computer speakers (3.5mm only) I get perfect sound; This doesn't help me much with trying to have a media box, however ;-)

Anyone have any tips? From what I've read I should be able to do this no problem. 

Here is some information on the hardware/setup. Please let me know any tips or other information that would be helpful:

$ uname -a
Linux nu-htpc 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

$ asoundconf list
Names of available sound cards:
Audigy2
CX8801

Sound prefs has Playback and Music and Movies set to "Autodetect"

Thanks again for any help!

---

### Post by NuSkooler on 2008-10-11
No one has any ideas? Am I doing this completely wrong? I've read the stickied guides and tried everything that looks like it may apply to my situation with no luck :(

---

### Post by markbuntu on 2008-10-11
So, are you plugged into the line out or some speaker out?

---

### Post by NuSkooler on 2008-10-11
OK, I feel like a idiot. I had a 3.5m to 2xRCA Y cable plugged from the Audigy digital out to the L/R RCA's on my reciever. 

My receiver only has 1 digital coaxial input. I found a thread stating that for digital, one can plug a mono 3.5m to RCA plug cable from the Audigy digital out to the digital coaxial -- if this works, I suppose I could get some sort of switch box to toggle between input sources?

Using the receiver's open L/R RCA however, shouldn't it be possible for me to use the existing Y cable I have to get sound? I've tried the Audigy line out plugs with no luck -- no sound at all. It seems strange that when plugged into the digital I'd get any sound at all (though like I said in the OP is full of clicks and static).

Since everything I'm trying is not working, what SHOULD I do?

---

### Post by markbuntu on 2008-10-11
You could run that cable from the headphone jack though that is really not an optimal solution sine you would have a serious impedance mismatch and need to adjust the volume just right but it would probably work or you could get a 3.5mm rca mono plug and try the digital again. Some cards have configurable jacks and there are switches in the sound mixer or volume control. I have a C-Media 8768 and can change the line-in to lfe or something like that. You should check that out.

---

### Post by NuSkooler on 2008-10-11
markbuntu, thank you for your replies so far! 

Just to clarify before I go out and buy more stuff, when you refer to a 3.5mm RCA mono do you mean something like this [http://www.radioshack.com/product/index.jsp?productId=2103855&cp=&sr=1&kw=1%2F8+to+rca&origkw=1%2F8+to+rca&parentPage=search](http://www.radioshack.com/product/index.jsp?productId=2103855&cp=&sr=1&kw=1%2F8+to+rca&origkw=1%2F8+to+rca&parentPage=search) ?

---

### Post by markbuntu on 2008-10-12
Really, you should see what fits. I was just guessing.

---

