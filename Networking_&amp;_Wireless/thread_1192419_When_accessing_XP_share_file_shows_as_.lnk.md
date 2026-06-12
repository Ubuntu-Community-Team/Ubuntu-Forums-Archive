---
title: "When accessing XP share file shows as .lnk"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by Scunnered on 2009-06-20
I am obviously going wrong somewhere and seek assistance.  

I managed to set up a share in XP to let me access a drive in the hope that I could work with a programme which when I checked its properties did not offer a share facility.  When I opened the network in Jaunty I was able to see the drive and the specific item that I wished to work with but when I attempted to open the file it displayed as bowls.lnk and could not be opened.

Looking at other folders / files displayed similar endings.  This included a lot of Microsoft items like Update etc etc.  Someone advised me that .lnk was only a link to the file but no matter what I tried I got no further.

Can anyone offer a solution to my problem.  I am fed up of chasing the laptop to find the one that has the bowls programme.

Thanking you in anticipation

---

### Post by coffeecat on 2009-06-20
It sounds as though bowls.lnk is a link in your Windows C: drive share to a file somewhere in another partition - something like E: or F: or whatever.

This is what I discovered in setting up shares between Ubuntu and Windows. If I set up a share in Ubuntu and create a symlink (Linux equivalent of a Windows link) in the share to a folder in another mounted partition, then from Windows I am able to browse into the symlinked folder from the Ubuntu share. But if I set up a share in Windows, create a link in that to a folder in the E: drive, I can browse the Windows share in Ubuntu, but if I try to browse into the folder in the E: drive I get an error. And this sounds like what you're getting. I've always assumed this is a limitation in Windows.

What exactly are you trying to do? Where is your Windows share situated? Where is bowls? What is bowls? Are you trying to access bowls-associated files or are you trying to run bowls from Ubuntu, because your "in the hope that I could work with a programme" makes it sound as though that is what you are trying to do.

I think there may be a way round this, but without more information I can't say any more.

---

### Post by Scunnered on 2009-06-20
I had a bowls programme written to record some lawn bowling statistics for me. This was done some time ago and since then I have moved away from Windows working totally with Ubuntu Jaunty. I therefore have been unable to work with this unless I use the XP laptop.

I checked the properties of bowls and found that there was no sharing tab so I thought that if I could not share the individual item that I should be able to access it on my C drive in XP.  I went through the share proceedure in XP and found that when I returned to Jaunty I could find everything on the C drive. 

On attempting to open it it displayed as .lnk  I have double checked the laptop and it shows that the file is contained in the C drive.  I also noted that there is a Windows shared folder for this programme but attempting to open this shows up as an .mbd file which will not open either.  Many other files which have a sharing tab will not open either again the file ends up as .lnk even Windows Update for example.

Strangely enough this was a follow on from initially sharing my printer which worked OK but even that now will display as printing but nothing comes out at the Jaunty end.

I hope that you can offer a solution as frustration is the order of the day at the moment.

---

### Post by coffeecat on 2009-06-23
**Scunnered**, my apologies for not posting back before.

From what you've told I should imagine the bowls.lnk file is a Windows shortcut for opening the executable in your bowls program. If that's right, then you're trying to run a Windows executable over a Windows share from Linux. I'm 99.9% sure that's not possible, although I'll be happy to be corrected. Windows shares are for sharing files, not for running apps over the network - but again I'm prepared to be corrected.

If your bowls program is in Windows and you want to run it from the Ubuntu machine, one solution might be to run it over [VNC]("http://en.wikipedia.org/wiki/Vnc"). There are some vnc packages in the repositories, but I have no experience of this.

Another possibility, if you still have the bowls installer, is to install it in WINE in Jaunty. If you're lucky, it may run in wine.

In Windows, have a look at the properties for the bowls.lnk shortcut. Where does it point to? Is there just one executable file, or is there a whole load of stuff under its own folder in C:\Program Files? If it's just a simple executable without any assocaited files and no registry entries (some straightforward apps are like this), you could try copying the .exe file to Ubuntu and then running it under wine.

---

### Post by dmizer on 2009-06-23
Please see the 6th link in my sig for the fix to this problem.

---

### Post by Scunnered on 2009-06-24
My thanks to you both for your replies.  I will have to give this problem some thought and effort as I would much prefer to work totally within Ubuntu.

My initial look at the information from dmizer scared the life out of me as I am somewhat new to Linux and a bit of unsure of some of the terms used.

I have a rather busy few days but will dovote time on Sunday to have a close look into the suggestions and report back later on

Again my sincere thanks for your assistance

---

### Post by dmizer on 2009-06-24
> **Scunnered said:**
> My initial look at the information from dmizer scared the life out of me as I am somewhat new to Linux and a bit of unsure of some of the terms used.

Since this is a fix related to Windows networking, most of the terms I use are from the Windows side of things, not the Linux side of things.

If you need help, or if you are unsure of something, please post in the howto and I will be more than happy to help you understand :)

---

### Post by Scunnered on 2009-06-25
**dmizer**

Many thanks for your guidance and kind offer.

I never understood Windows. It worked, fell down, caused more trouble than was worth and made me determined to find something better.

Found it - now with assistance from the forum starting to understand matters. It is very much the case of teaching an old dog new tricks but with the support I am receiving I might learn a new trick or two

Once again my sincere thanks for your kind offer

---

### Post by Scunnered on 2009-06-29
**dmizer**

I have has a closer look at your tutorials and think that “**Mount samba shares with utf8 encoding using cifs**” will meet my needs better.  In your Fix Samba browsing you state that firewalls can cause problems and this was my experience with my earlier attempts.

I am using AVG anti virus & firewall on the XP*system and had to disable the firewall to let Jaunty read the shared drive.  AVG requested that I load a temp file to see what happened but all their instructions went over my head.  As a result I used the system restore in Windows and went back to the old ways.

Can you advise on the following :

1.Will using cifs avoid firewall problems.

2.Can I assume that where you made reference to Windows 2000 server and Hardy that my XP laptop will be the server and that Jaunty will be ok for use.

3.You make reference to “sharename” can this be as simple as the laptops user?

4.As I am on a cable wireless network do I ignore references to  “DHCP network” and references to nsswitch and winbind?

5.A permanent install would suit me better but I am confused with the password references. I believe that Samba is automatically loaded in Jaunty and would assume that the system passwords would apply.  I see no reason for me to have a password as I will be the only one requiring access to the share.

If you can clarify the above then I will put my faith in your tutorial and venture forth into the unknown.

Thanking you in anticipation

---

### Post by dmizer on 2009-06-29
> **Scunnered said:**
> 1.Will using cifs avoid firewall problems.
There still may be problems, but you're more likely to be successful. Firewalls cause more problems for share browsing than they do for mounted shares.

> **Scunnered said:**
> 2.Can I assume that where you made reference to Windows 2000 server and Hardy that my XP laptop will be the server and that Jaunty will be ok for use.
Yes, the howto is up to date for Jaunty and works fine with XP as the server.

> **Scunnered said:**
> 3.You make reference to “sharename” can this be as simple as the laptops user?
No, you will have to verify the sharename on your XP computer. See the second post in the tutorial for how to figure out what the sharename (as well as the workgroup) is.

> **Scunnered said:**
> 4.As I am on a cable wireless network do I ignore references to  “DHCP network” and references to nsswitch and winbind?
No, unless you have a static network (unlikely), you'll still need to configure nsswitch and winbind. This way, your laptop will still be able to find your XP computer even if your XP computer gets a different IP address.

> **Scunnered said:**
> 5.A permanent install would suit me better but I am confused with the password references. I believe that Samba is automatically loaded in Jaunty and would assume that the system passwords would apply.  I see no reason for me to have a password as I will be the only one requiring access to the share.
Passwords are set on the Windows side of things, not the Ubuntu side of things. If you do not configure Windows for a password protected share, then you do not need to enter a password on the Ubuntu side.

More than happy to provide any other information you might need, but it would be better if you posted in the howto as I will be notified of your post more quickly.

Good luck!

---

