---
title: "Dear Family Computer:  Why do you ruin my laptop's Internet? A Linux+Windows Mystery."
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by LadyDoor on 2006-06-13
Hello!

(Hopefully) quick question for somebody who knows about both Linux and Windows (or Windoze--whatever). So I'm a student and living at home for the summer. I've been at school this year and never had internet problems on my laptop. However, here, I find myself unable to use the internet on my laptop anytime within an hour to an hour and a half after the family computer is used by someone else (I don't have an account on it, what with having a laptop). As you might imagine, this is annoying.

I've also found that if I don't do *sudo ifdown eth0* before shutting down my computer, people trying to use the other one have the same problem I do. If I do shutdown the internet like that before turning off the computer, however, they have no problem.

With these things in mind (you did read both paragraphs, right?), does anybody know of a way to remedy my problem? I think that perhaps if there were a way to manually shut down the internet on the family (Windows) computer (it gives an error message when you right click and hit "disable"), it might solve the problem, but I don't know for sure. If anybody has any idea, your help would be much appreciated.

Thanks,
Door

---

### Post by DarthMandeep on 2006-06-13
How are both computers connecting to the net? Are you using a router to share the internet connection, or does the laptop connect to the Windows computer and connect to the net from there? What version of Windows is this, XP?

---

### Post by LadyDoor on 2006-06-13
Ummm, the DSL wire goes into a box. Out of the box comes a wire that connects into whichever computer is supposed to be getting the internet. And it's XP.

---

### Post by Slim Odds on 2006-06-13
[quote=LadyDoor]Ummm, the DSL wire goes into a box. Out of the box comes a wire that connects into whichever computer is supposed to be getting the internet. And it's XP.[/quote] 
Ok, that answers part of the question. Where does linux come into the picture?

---

### Post by LadyDoor on 2006-06-13
I use Ubuntu on my laptop.

---

### Post by RRS on 2006-06-13
[QUOTE=LadyDoor]Ummm, the DSL wire goes into a box. Out of the box comes a wire that connects into whichever computer is supposed to be getting the internet. And it's XP.[/QUOTE]

Does your laptop use wireless or do you plug it into "the box"? 

Also, is there a make/model label on the box and is anything else plugged in between the computer and the wall?

---

### Post by LadyDoor on 2006-06-13
Well, as I said, the wire from the box, a Westell Wirespeed modem, goes into whichever computer one wants to use the internet on. So no, I don't use wireless. It would be nice to have, though, because I know wireless works on this computer. But at present, it's not an option ($$$).

---

### Post by RRS on 2006-06-14
Makes a little more sense now, thanks.

Since you've indicated that your loss of internet seems to be a computer/modem problem I'm guessing you plug the computers into some sort of switch or splitter and the modem only has one outlet. On the other hand does the loss occur when one computer is physically unplugged and the other plugged in in it's place?  

Either way you're going to need a router to properly share the connection. These can be found for under $40 or $50. I use a Linksys and the seem to have a good reputation for easy set-up and reliabilty.

---

### Post by LadyDoor on 2006-06-14
Um, the modem does only have one outlet, but I don't know about a switch or splitter. I just unhook the internet from the family computer when I want to use it on mine, and do *sudo ifdown eth0* and then plug it back into the family computer when i'm done. But for it to work on mine I need to wait about an hour or an hour and a half after the family one was used. Does anybody know of a similar trick that could be used when shutting down the windows computer? Something that would have a similar effect to the ifdown command that takes down the internet? (I can't afford a router and I'm just going to be here for two months; also, I have no idea whether something fancy like that would work).

---

### Post by DarthMandeep on 2006-06-14
The Westell is probably a DSL modem/NAT router combo, though it only has one LAN port. I've worked with one before. Maybe it assigns an IP to the current computer, and when a new machine is plugged in it doesn't make a new DHCP lease?

Easiest thing to try would be rebooting the Westell box when you change what computer is plugged into it. That way it'll renew the lease and give you a connection without making you wait.

Other than that, I'd setup a static IP on the laptop, some address different than what the desktop had.

---

### Post by Indifferent on 2006-06-14
The modem/router supplies the DHCP lease to your computer and uses your MAC address to uniquely indentify each computer. If you are unplugging from one and plugging into another, the MAC address no longer matches. You can either reboot it or go into your router (192.168.0.1) and renew the lease for the new computer.

---

### Post by jrobinson5 on 2006-06-14
LadyDoor, I strongly suggest you get a wireless router. Ask around to see if any of your friends have an old one (lots of people who upgraded to G have an old B router sitting around, which will work perfectly fine.) Or ask santa for one, or save nickels and dimes. I bought one a few months ago from NewEgg for less than twenty bucks after rebate, and it works great. Trust me, you won't regret it.

---

### Post by lucia_engel on 2006-06-15
[QUOTE=DarthMandeep]Easiest thing to try would be rebooting the Westell box when you change what computer is plugged into it. That way it'll renew the lease and give you a connection without making you wait.[/QUOTE]

I can attest to that method. Whenever I have a connection problem (which disappeared after I switched to linux, wonder why :p) I just turn my router on and off again to restart it and it'll work.

---

### Post by viper52b on 2006-06-15
There is simmilar action in windows like the ifdown eth1 you use on linux, which might solve your problem.

```

type "CMD" in start -> run
# ipconfig /release

```

But you will have to do this every time you switch from windows to linux machine (and ifdown if you switch from linux to windows).  You're probably best of buying a router :)

Greetz

---

