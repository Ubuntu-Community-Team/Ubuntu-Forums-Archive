---
title: "wireless driver became de-activated after plugging in ethernet cable for file sharing"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by teklife on 2010-12-10
using ubuntu 10.10 (pinguy OS)

i connected an ethernet cable from my girl's macbook pro to her lenovo ideapad s10-3t to transfer some DS9 episodes onto it. new enough to linux to have not been able to figure out how to access the files on the mac, so i disconnected the ethernet, and the wireless hasn't worked since. tried everything i know, and googling for a while (as well as searching again on this forum) to no avail.

just before linking the 2 computers via ethernet, the wireless worked fine on the ideapad, always had; but not so after the ethernet connection that did nothing other than apparently kill the wireless. 

an "lshw -C network" command tells me i have a BCM4313 wireless card, and *-network UNCLAIMED. also, if i launch "install additional drivers", i see that the proprietary driver is not active. 

how could merely plugging in an ethernet cable that happened to be conncected to a MBP running OSX.6 do that? and will that happen again? i thought linux was supposed to play real nice with other OS's, so why did a simple file transfer kill my wireless connectivity?

i have no access to internet via ethernet cable, so i cannot just download the driver i need now. shouldn't it still be in the computer still? somewhere?

is there a simple solution to this, or has the wireless driver been wiped out by plugging in the ethernet? 

is this a bug that should be reported?

thanks

---

### Post by grahammechanical on 2010-12-10
Some questions from someone who is puzzeled by this problem. Is Ubuntu the only OS on the Lenovo? Is there a key combination that switches wireless on and off, such as Fn+F2? Is the wireless connection set to automatically connect? What messages did the Ubuntu Operating System give you when you pulled out the ethernet cable? It would be a rude OS if it failed to say that networking was disconnected. What have you tried to do to establish a wireless connection with the modem?

Regards.

---

### Post by teklife on 2010-12-10
> **grahammechanical said:**
> some questions from someone who is puzzeled by this problem. Is ubuntu the only os on the lenovo? 

No, there's also the win7 hp that came with it, in which the wireless works fine.

Is there a key combination that switches wireless on and off, such as fn+f2?

Um, not sure, but this case is one of the times where i know exactly what i did, since it was such a short time. I connected both computers via ethernet (mac first) then looked for the mac in my nautilus file manager in ubuntu, saw nothing, looked over the control centre, then unplugged. Right away i noticed there was no way to see the list of wireless networks.

Is the wireless connection set to automatically connect?

Yes, it had been set to auto connect.


What messages did the ubuntu operating system give you when you pulled out the ethernet cable? 

Nothing

it would be a rude os if it failed to say that networking was disconnected. What have you tried to do to establish a wireless connection with the modem? I checked anything on the computer that said network, to see if i could get the wifi working again, but i didn't see anything. I googled around and found some command line stuff such as the "lshw -c network" command, plus other instructions, but could not get it working. I launched the additional drivers utility and saw that the driver for my wireless card was not activated, but even plugging into a wired internet would not resolve that. It would give an error message which i don't recall now. It said something like, "failed to install..." 

i got my macbook pro to share internet via ethernet to try to download the driver, but no cigar. 

I "solved" the problem by reinstalling the os:( not a very elegant solution, but i figured, in the end, it would save me more time than all the googling and reading and posting to forums. Still, i would like to know the cause, and whether it will happen again if i connect the ethernet cable again to transfer files.

I read that you need a crossover cable, but then other people said the mac automatically reverses the polarity. I still would like a better way to transfer files than a usb key.

Regards.
1

---

### Post by owiknowi on 2010-12-10
If both computers are in close vicinity of each other you could just use a USB cable?

Had the same problem here more or less, but could reactivate the wireless by adding a new connection (after deleting the old one).

---

