---
title: "HP G60 Laptop Wireless Disabled By Hardware Switch"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by Noobs*McGee on 2011-07-16
Hi,

I'm in the process of setting up my parents' HP G60-630US laptop with Ubuntu 11.04 Natty.  Installation went fine, but now I am trying to get the wireless set up and am encountering an annoying problem:  The wireless drop down menu will not allow me to enable wireless because "wireless is disabled by hardware switch".  When I try to turn on the wireless via the glowing orange wireless button above the keyboard nothing seems to happen.

When I enter rfkill list in terminal, it returns the following:

0: phy1: Wireless LAN
             Soft blocked: yes
             Hard blocked: yes
1: hp-wifi: Wireless LAN
             Soft blocked: yes
             Hard blocked: yes

when I press the button and enter rfkill list again it returns:

0: phy1: Wireless LAN
             Soft blocked: yes
             Hard blocked: yes
1: hp-wifi: Wireless LAN
             Soft blocked: yes
             Hard blocked: no


I'm not really sure what this output means.  I wasn't able to find any threads the addressed this issue specifically.  If there is a quick and easy solution to this issue, or if this is a known problem with no solution, I'd like to know either way.

Appreciate any help.

Thanks,
NM

p.s. if it helps, lspci -v lists the wireless card as:

Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by jboyette on 2011-08-19
Had the same problem, very common with 11.04 upgrade!  Try this on the command line, and if you have a wireless button, turn it on after you issue the command if you see no change.

sudo rfkill unblock all

---

### Post by cosners on 2011-08-27
I'm not the OP but I'd just like to say that I had the same problem and this worked for me. The laptop that I'm using is a HP Pavilion dv2500 that I just recently switched over to Ubuntu. Thanks for the tip!

---

### Post by Noobs*McGee on 2011-10-22
Sorry to let this thread sit for so long, I actually ended up resolving this some time ago.  The solution suggested by jboyette did the trick.  I haven't had a chance to find out if it holds for a reboot, or if you have to run that command every time you boot to Linux, but it solved the immediate issue anyway.  Thanks for the input, everyone.

NM

---

### Post by Jonathan Foster on 2011-10-25
Hi all, I had the same problem when I installed 11.04 on to my own G60-630US. Did some research and the "sudo rfkill unblock all" trick in terminal helped too. Just letting any other HP G60 users know it works.

---

### Post by David Samuels on 2011-11-05
This solution also worked for me on a Compaq nc6320. Thanks.

---

### Post by Habeouscorpus on 2011-11-13
Worked on a Dell Inspiron 1545! Thanks a lot!

---

### Post by beefiron on 2011-12-27
Also worked for me on a Pavilion dv1355ea (which also goes by dv1000 and dv1300).

Many (many) thanks.

---

### Post by Grifftology on 2012-02-07
I'm so sorry! I don't mean to be the short busser of this thread but I still cant get the wireless to work on my HP G60. The wireless button stays blue, which on windows meant it was ON, and does register changes (by checking with rfkill list) but it always says "Wireless Disabled by Hardware Switch" in Ubuntu 11.10...this is such an amazing OS and i'm hell bent on using it...just gotta get past this snag! any help would be greatly appreciated.

---

### Post by Schwowsers on 2012-02-12
EDIT:  I can only get it to work until I reboot, and then I have to mess around with pressing the wifi toggle button and entering "rfkill unblock all."

---

### Post by techiebiker on 2012-03-04
Same problem with my HP G60-530US.

Had Ubuntu installed using entire partition. On this laptop started with 10.04 I think. Upgraded through each successive version, am now on 11.10. Wireless worked fine.

Just recently had to shrink partition to install Windows 7 so could use a specific program.

Now get "Wireless disabled by hardware switch" when I boot into 11.10. 

If I plug in Ethernet and wait a while the option to "Enable Wireless" becomes available on the system tray (is that what it's called) icon's right click menu.

At that point can enable wireless and it works. Though before problem began light usually would be solid blue all the time. Now it flashes orange intermittently.

If I don't plug in Ethernet the option to "Enable Wireless" doesn't become available.

System was up to date with all patches as of 3/3/12. Only change was shrink partition. Then this behavior began.

---

