---
title: "[SOLVED] Dual boot from Ubuntu &amp;amp; Mandriva"
date: 2008-06-25
forum: Mandriva/Mageia
---

### Post by msayed2004 on 2008-06-25
Hi everybody;
I want to test other flavors of GNU/Linux rather than Ubuntu & I have some questions & I think here is the best place.
Currently I use both XP & Hardy, I will get rid of XP & I will reinstall Hardy & I think I will try Mandriva (I was thinking about openSUSE too but I will start with Mandriva anyway).


[LIST]
[*]In an old topic (not here) a guy said that Ubuntu installation is better in modifing GRUB as it will preserve previous systems so we should Install Mandriva first then Ubuntu, but for me I want Ubuntu to be on the first partition as it will be my main OS and others will be changed so often, so will Mandriva mess with GRUB ? & If so how can I fix that?
[*]In another topic a guy said that in machines with low RAM it is better to make the swap partition at the beginning of the HDD, if this is right should I do this too ? I have 768 MB (256+512) and I don't consider this low but I want the best performance.
[*]I think it is possible to have one Home directory (in a third partition), if this is right how can I do that ?




----
[*]Anyway to back up my Thunderbird msgs to be used in the freshly installed Ubuntu ?
[/LIST]
I know that my last question should not be here but I may get the answer here without making a new topic :lolflag: .


Thanks :)

---

### Post by logos34 on 2008-06-25
> **msayed2004 said:**
> 

[LIST]
[*]In an old topic (not here) a guy said that Ubuntu installation is better in modifing GRUB as it will preserve previous systems so we should Install Mandriva first then Ubuntu, but for me I want Ubuntu to be on the first partition as it will be my main OS and others will be changed so often, so will Mandriva mess with GRUB ? & If so how can I fix that?
[/LIST]

[LIST]
[*]Mandriva (2008.1, at least) will definitely detect hardy ubuntu and add it to menu.lst, and ubuntu should detect mandriva.  So either way, really.  Either grub will boot the other fine (this was not the case previously, i.e. pre-hardy ubuntu).  If you install mandriva second, when you come to the select bootloader location screen toward the end of the install, make sure to install grub to the mandriva root partition (choose in dropdown menu) rather than accept the default (->MBR).  Then copy the mandriva entry from its menu.lst and add it to the ubuntu menu.lst
[/LIST]


[LIST]
[*]> In another topic a guy said that in machines with low RAM it is better to make the swap partition at the beginning of the HDD, if this is right should I do this too ? I have 768 MB (256+512) and I don't consider this low but I want the best performance.
[/LIST]
I don't think you'll notice the diff no matter where you put it, but I've heard it's slightly faster if you put it next to the root at the front of the disk rather than the end (so the heads don't have so far to travel).  But with 768 you'll hardly be using the swap (linux manages memory very efficiently), so it's even less important.  I run 512 and it uses only a fraction of my swap space.  Although if you the type that has two dozen apps open at any given time, then obviously it's more of an issue.


[LIST]
[*]> I think it is possible to have one Home directory (in a third partition), if this is right how can I do that ?Specify a separate home partition during manual installation (mount point '/home') (Edit: if you mean a /home shared by ubuntu and mandriva, I wouldn't advise it, that's just my opinion...better to have a shared Data partition and keep each home folder on root)
[/LIST]

---

### Post by msayed2004 on 2008-06-30
Back with new questions & problems:

1-When I go to Mandriva it says (at log-in) that I use invalid session so I have to change the session to KDE, going to Ubuntu I get a message ask me if I want to make the KDE the default session while no KDE installed on it!
I guess it is related to settings saved on my Home directory, but where & how can I fix this I have no idea :confused: ?!

2-QT based applications became ugly under Ubuntu, see the attachments.

3-How can I install FF3 & Thunderbird 2.0.0.14 on Mandriva ? as the last updates only contain FF 2.0.0.14 & Thunderbird 2.0.0.12 and this lead to profile troubles (I want to use a shared profile).

---

### Post by AdamWill on 2008-06-30
Firefox 3 is available in the /main/testing repository (although it actually really shouldn't be, but never mind). Package name firefox.

Are you using a shared /home ? As logos says, I don't think it's a great idea. I don't think we or Ubuntu would really recommend it...

---

### Post by msayed2004 on 2008-07-07
> Are you using a shared /home ? As logos says, I don't think it's a great idea. I don't think we or Ubuntu would really recommend it...I installed everything before seeing that edit :(

---

I decided to remove Mandriva and try it via VBox.
Now I want to fix my GRUB before formatting Mandriva's partition, will ```
sudo grub-install /dev/sda3
```command do this via the installed Ubuntu ?
My Ubuntu on sda3

---

### Post by AdamWill on 2008-07-07
I'm not really sure, sorry - I don't know how Ubuntu handles GRUB. Anyone?

---

### Post by wolfen69 on 2008-07-07
boot to a live cd and:
```
sudo grub
```
```
root (hd0,1)
```
```
setup (hd0)
```
```
quit
```
then reboot

---

### Post by logos34 on 2008-07-07
> **msayed2004 said:**
> 
I decided to remove Mandriva and try it via VBox.
Now I want to fix my GRUB before formatting Mandriva's partition, will ```
sudo grub-install /dev/sda3
```command do this via the installed Ubuntu ?
My Ubuntu on sda3

If you mean you're currently using Mandriva's grub to boot, then to revert to ubuntu grub do this from ubuntu:
[B]
sudo grub-install /dev/sda[/B] 

(if you add a '3' that just writes it to the bootsector of the ubuntu root--but you want it to overwrite mandriva's grub on the MBR)

OR

sudo grub

grub> root (hd0,2)
grub> setup (hd0)
grub> quit

Now you can safely format Mandriva partition.

---

