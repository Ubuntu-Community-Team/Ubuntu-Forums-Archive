---
title: "Abondoned by Network Manager"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by Siouxsie on 2009-12-03
I recently downloaded Ubuntu 9.10 on my Asus Eee and network manager was working well until I changed locations and wanted to connect to a different wireless network. It refused to let me do this, so I switched to wicd. After wicd didn't work, I removed it and found that network manager had gone away as well. I can't get connected to the internet, wireless or wired without a similar program, and I can't a program without being connected to the internet. Does anyone have any suggestions that might be more productive that banging my head against the wall?

---

### Post by coffeecat on 2009-12-03
**Edit:** oops - posted some nonsense. It's late here.

Sorry - it's too late for me to think clearly, but to re-install network-manager you could download the deb package files from the Karmic repository with another machine, transfer them over, and install them simply by double-clicking on them. Offhand I don't know how to find the URL for the Karmic repository and I'm too tired now to find it, but this issue comes up a lot - installing packages without an internet connection - so a search of the forum might give you a clue.

---

### Post by k3lt01 on 2009-12-03
Hmmmm, I see this all to often. People are advised to try Wicd but to do so means you delete Network Manager. I have done this same thing twice and both times resulted in a full clean install of Ubuntu.

The only thing I can suggest to you right now is that you use the LiveCD, enable it in the Software Sources GUI, refresh the repository, open Synaptic, search for Network Manager on the LiveCD and if it is there install it and all its dependencies.

If non of that works I'm sorry but I think you'll be stuck with a having to do a fresh install.

Edit: Network Manager is in Main so I would assume its on the LiveCD. I don't know much about Asus EeePCs but from memory they don't have a CD drive or slot so you will need to use the installation media you used to install Ubuntu in the first place and get Software Sources to use that instead of a LiveCD.

---

### Post by wilee-nilee on 2009-12-03
If you install wicd from synaptic it will remove network manager  removing wicd will reinstall network manager. You have to work at removing either without adding the other or removing it.

Are you missing the notification area on the panel which can be added from add to panel.

---

### Post by k3lt01 on 2009-12-03
> **wilee-nilee said:**
> If you install wicd from synaptic it will remove network manager  removing wicd will reinstall network manager. You have to work at removing either without adding the other or removing it.

Are you missing the notification area on the panel which can be added from add to panel.What does the OP say? lets take a look hey!

> **Siouxsie said:**
> After wicd didn't work, I removed it and found that network manager had gone away as well. I can't get connected to the internet, wireless or wired without a similar program,Removing Wicd does NOT automatically re-install Network Manager. To say this is wrong and leads people up the garden path and to a heap of frustration, been there done that. Seriously, I wish people would learn to read the OP.

Rant over, lol.

> **Siouxsie said:**
> Does anyone have any suggestions that might be more productive that banging my head against the wall?Take a look in /var/cache/apt/archives to see if the deb file for Network Manager has been stored there. I doubt it will be but it may be worth a try.

[Here's the package page for Network Manager]("http://packages.ubuntu.com/karmic/network-manager") where you can download it from. The page also lists all Network Managers dependencies so if you haven't got them installed, check your computer first in Synaptic to see if they are listed as installed. If the dependencies are installed then you will just need to download Network Manager on another computer put the deb file onto a thumb drive or whatever your netbook uses then copy it to your desktop and install it from there.

Hope that helps, let us know how you go.

---

### Post by wilee-nilee on 2009-12-03
All I will say is that I have switched back and forth between wicd and network manager many times in synaptic and every time they replace each other you are completely wrong. I am not spreading incorrect information that is a stupid reply.

It may be so that if you remove the last gui net access that you have nothing but you can use the terminal to access the net. If you remove the last network access gui your not thinking.

There is not enough information in the OP's post to really know what happened as well. It may be that the network manager is still there but is not shown because the notification area has been removed.

---

### Post by k3lt01 on 2009-12-04
> **wilee-nilee said:**
> All I will say is that I have switched back and forth between wicd and network manager many times in synaptic and every time they replace each other you are completely wrong. I am not spreading incorrect information that is a stupid reply.The OP states wicd was removed not switched back to nm. They may have assumed nm would have been reinstalled but without asking for nm to be reinstalled then that would not have happened. We do know however wicd was removed and there is no network connection working so it stands to reason regardless of an applet appearing or not that nm was NOT reinstalled.

> **wilee-nilee said:**
> It may be so that if you remove the last gui net access that you have nothing but you can use the terminal to access the net. If you remove the last network access gui your not thinking. I don't think they need you being judgemental, just your help to get nm back.

> **wilee-nilee said:**
> There is not enough information in the OP's post to really know what happened as well. It may be that the network manager is still there but is not shown because the notification area has been removed.There is plenty of info to base a halfway decent educated response to.

1: Check synaptic to see if nm, and its dependencies, is installed.
2: If its not download it, and its dependencies if required, on another computer, copy the downloaded files to a usb drive or whatever the netbook uses.
3: Copy the files from the usb drive to the netbooks desktop.
4: Tell Software Sources about the new file/s.
5: If you just require nm install from the desktop, if more is required install via Synaptic
6: If that doesn't work be prepared, unfortunately, to fully reinstall Ubuntu.

---

### Post by wilee-nilee on 2009-12-04
I hope the op is able to find a working answer.

---

### Post by Siouxsie on 2009-12-04
Thank you all for your suggestions!
 
NM is still in synaptic, but when I try to install it I'm told "W: failed to fetch whatever.deb, Could not resolve us.archive.ubuntu.com"
 
I've downloaded a few different versions and put them on a usb stick, but none of them are working either.
 
NM is still listed in the startup applications as well, so I suspect it may not be necessary to download/reinstall NM, let alone all of ubuntu

---

### Post by seenthelite on 2009-12-05
> **k3lt01 said:**
> Hmmmm, I see this all to often. People are advised to try Wicd but to do so means you delete Network Manager. I have done this same thing twice and both times resulted in a full clean install of Ubuntu.

The only thing I can suggest to you right now is that you use the LiveCD, enable it in the Software Sources GUI, refresh the repository, open Synaptic, search for Network Manager on the LiveCD and if it is there install it and all its dependencies.

If non of that works I'm sorry but I think you'll be stuck with a having to do a fresh install.

Edit: Network Manager is in Main so I would assume its on the LiveCD. I don't know much about Asus EeePCs but from memory they don't have a CD drive or slot so you will need to use the installation media you used to install Ubuntu in the first place and get Software Sources to use that instead of a LiveCD.


I have seen people saying what you have regarding installing Wicd and then having Network Manager removed. But what do you do when Network Manager does not work on your hardware and you can not use wireless at all.  This happened to me and I saw a post advising To remove Network Manager and Install Wicd I done this and it worked for me. I no longer have Network Manager and do not need it. To constantly advise not to do something that did not work for you but works on other peoples hardware seems wrong to me.

---

### Post by Love2MeetU on 2009-12-05
> **Siouxsie said:**
> Thank you all for your suggestions!
 
NM is still in synaptic, but when I try to install it I'm told "W: failed to fetch whatever.deb, Could not resolve us.archive.ubuntu.com"
 
I've downloaded a few different versions and put them on a usb stick, but none of them are working either.
 
NM is still listed in the startup applications as well, so I suspect it may not be necessary to download/reinstall NM, let alone all of ubuntu

All you have to do is change your Repository settings for Sources.

Go System>Administration>Software Sources
Tick the little box in the big white section which allows you to include the CD as a source.

Startup Synaptic Package Manager, then Reload. Search for Network Manager, and install.

Ignore the 
 "W: failed to fetch whatever.deb, Could not resolve us.archive.ubuntu.com"
 Because that doesn't matter as you're getting Network Manager from the CD.

Restart, and it will be working again.

I did it on my own PC just 30 minutes ago.

---

### Post by k3lt01 on 2009-12-05
> **seenthelite said:**
> I have seen people saying what you have regarding installing Wicd and then having Network Manager removed. But what do you do when Network Manager does not work on your hardware and you can not use wireless at all.  This happened to me and I saw a post advising To remove Network Manager and Install Wicd I done this and it worked for me. I no longer have Network Manager and do not need it. To constantly advise not to do something that did not work for you but works on other peoples hardware seems wrong to me.Why don't you discuss this with people who constantly advise this, I myself don't constantly advise anything so this shouldn't be targeted at me.

I have tried Wicd and it has never worked for me, if others want to try it then good for them but as we are seeing here people install Wicd which removes NM then remove Wicd because it didn't work for them. What are they left with? nothing working because NM isn't re-installed when Wicd is removed. If you find this to be incorrect then why are we discussing it in a thread where the OP has had it happen to them?

In the post you refer to did the person offer any other advice to those who Wicd is not a good solution for? Did they say if you choose to remove Wicd make sure you re-install NM before you remove Wicd because if you don't you will have NOTHING?

Instead of having a go at people for trying to be helpful, offer some helpful advice yourself and together we may be able to find a solution for the OP.

---

### Post by k3lt01 on 2009-12-05
> **Siouxsie said:**
> NM is still in synaptic, but when I try to install it I'm told "W: failed to fetch whatever.deb, Could not resolve us.archive.ubuntu.com"You have told us you don't have a net connection at all on that machine so it wont download anything. Thus the failed to fetch message.
 
> **Siouxsie said:**
> I've downloaded a few different versions and put them on a usb stick, but none of them are working either.Lets keep this simple by sticking to the correct Ubuntu version for your system. Ubuntu is pretty good like that they list everything, you just need to know where to look to find it. Forget about anything else for the moment.

Did you download the version listed on the page I gave you the link to? Have you checked if the dependencies are installed?

If both the answers are yes, and assuming you have all the Dependencies installed, copy the correct version of NM to your desktop and install from there. It should be that simple if it is going to work easily.

If the dependencies are not all installed you will have to download the correct versions of them as well. Just follow the links on the page I gave you previously to obtain them. This is where it gets a little more difficult because you then have to tell Synaptic you have them and where you have put them. To do this open Synaptic go to File > Add downloaded packages and tell Synaptic where you have put them, hopefully you will have just put them on your Desktop. Once you have done that Reload Synaptic so it has the files available to it. Find Network Manager in the list, Mark for Installation (or even Re-installation), Apply, and go from there.

Reboot your machine, and if things go as they should Network Manager should now be working and you should have a working net connection. n.b. that's in a perfect world, like I have already said I have personally had to do a clean re-install of Ubuntu because of bad advice given to me by well meaning people.
 
> **Siouxsie said:**
> NM is still listed in the startup applications as well, so I suspect it may not be necessary to download/reinstall NM, let alone all of ubuntuI think all this means is when you installed Wicd Network Manager was removed but not some of the configuration files relating to it, in other words it was not a Complete Removal. This is another thing altogether. Re-installing NM will simply find these files are already there.

---

### Post by wilee-nilee on 2009-12-05
> **Love2MeetU said:**
> All you have to do is change your Repository settings for Sources.

Go System>Administration>Software Sources
Tick the little box in the big white section which allows you to include the CD as a source.

Startup Synaptic Package Manager, then Reload. Search for Network Manager, and install.

Ignore the 
 "W: failed to fetch whatever.deb, Could not resolve us.archive.ubuntu.com"
 Because that doesn't matter as you're getting Network Manager from the CD.

Restart, and it will be working again.

I did it on my own PC just 30 minutes ago.

+1 a actual workable answer.;)

---

### Post by k3lt01 on 2009-12-05
> **wilee-nilee said:**
> +1 a actual workable answer.;)Except it is slightly incorrect. Check the screenshot, you click the "CD" NOT "Source" as Source is "Downloadable from the internet" which is not available according to the OP.

Also, Eee's don't have CD drives so the "actual workable answer" needs a little more work :p. Work that includes showing Synaptic where to actually find the files.

---

### Post by wilee-nilee on 2009-12-05
meh.

---

### Post by Siouxsie on 2009-12-05
I was able to reinstall wicd from synaptic, from there get a wired connection, then reinstall NM from synaptic. Everything indicates NM is installed and running, but there is no icon on the upper right side and I can't open NM. Oh, so very frustrating.

---

### Post by coffeecat on 2009-12-05
> **Siouxsie said:**
>  Everything indicates NM is installed and running, but there is no icon on the upper right side and I can't open NM.

Two things to check.

The Network Manager appears on the panel if you have the Notification Area panel applet on the panel. It's possible with all your problems that the Notification Area was removed somehow. The icon of NA itself looks like three very small horizontal lines above each other making a vertical stack. If that's not there, right-click somewhere on the panel, select 'Add to Panel', highlight 'Notification Area' and click on 'Add'.

The other thing to check is whether NM is still in Startup Applications. What follows is for the standard gnome desktop, but System > Preferences should be in the netbook remix version somewhere. Anyway, find 'Startup Applications' in System > Preferences. Is Network Manager listed under the 'Startup Programs' tab? If not click on 'Add' and the code for the command is:

```
nm-applet --sm-disable
```

If you've had to add the NM command to Startup Applications, you'll need to restart your session, perhaps reboot.

---

### Post by Siouxsie on 2009-12-05
Thank you, coffeecat! The startup command was what I needed. Now that it's running, though, under both wired and wireless connections it says "devices not managed" even when I'm plugged into my modem. D'oh?

---

### Post by Siouxsie on 2009-12-12
Does anyone know of a way to fix the "device not managed" issue?

---

### Post by k3lt01 on 2009-12-13
> **Siouxsie said:**
> Does anyone know of a way to fix the "device not managed" issue?Yep, and it was the 3rd paragraph of my 1st post in this thread. I have never seen a good outcome from installing Wicd and then trying to re-install NM yet, it always ends with a complete re-install.

---

